#include<iostream>
#include<ctime>
#include<windows.h>
#include<conio.h>
#include<iomanip>
#include<fstream>
using namespace std;

bool GameEnd;
const int length=110;//this is the length of the game
const int height =30;//this is the height of the game
int     x_axis,// this is xaxis variable used for printing map
        y_axis,// this is yaxis variable used for printing map
        food_X,// this is xaxis variable for fruit  which will randomly generated
        food_y,// this is yaxis variable for fruit  which will randomly generated
        scoure;// this is for showing scour on the screen
enum eDirection { STOP = 0, LEFT, RIGHT, UP, DOWN};// this enum will used to sort data and give them some integer value used for using the snake in all direction
     eDirection dir;// i signed another name for enum edirection variable to dir
//int  x_tail[200],y_tail[200];// this array are for storing the length of the snake
int  length_tail;
//prototype funtions
void frame();
void draw(int *, int *);
void input();
void logic(int *, int *);
// main funtion where all other funtiion will me called within loop
int main()
{
int      size=200;
           // int  x_tail[200],y_tail[200];// this array are for storing the length of the snake
             int *x_tail=new int[size];
             int *y_tail=new int[size];

    while(!GameEnd)
    {

    int x;
    cout<<"##################################################################################"<<endl;
    cout<<"#                                                                                #"<<endl;
    cout<<"#                        WELLCOME TO SNAKE GAME                                  #"<<endl;
    cout<<"#                                                                                #"<<endl;
    cout<<"#                                                                                #"<<endl;
    cout<<"#                          1.  START GAME                                        #"<<endl;
    cout<<"#                                                                                #"<<endl;
    cout<<"#                                                                                #"<<endl;
    cout<<"#                          2.  GAME INSTRUCTIONS                                 #"<<endl;
    cout<<"#                                                                                #"<<endl;
    cout<<"#                                                                                #"<<endl;
    cout<<"#                          3.  QUIT GAME                                         #"<<endl;
    cout<<"#                                                                                #"<<endl;
    cout<<"#                                                                                #"<<endl;
    cout<<"#                                                                                #"<<endl;
    cout<<"#                                                                                #"<<endl;
    cout<<"##################################################################################"<<endl;
    cout<<endl<<endl;
    cin>>x;
switch(x)
 {

    case 1:
     {
         system("cls");
      int y;
    cout<<"##################################################################################"<<endl;
    cout<<"#                                                                                #"<<endl;
    cout<<"#                                   SELECT DIFFICULTY                            #"<<endl;
    cout<<"#                                                                                #"<<endl;
    cout<<"#                                                                                #"<<endl;
    cout<<"#                          1.  LOW (SPEED OF SNAKE IS VERY LOW)                  #"<<endl;
    cout<<"#                                                                                #"<<endl;
    cout<<"#                                                                                #"<<endl;
    cout<<"#                          2.  MEDIUM (SPEED OF SNAKE IS VERY MEDIUM)            #"<<endl;
    cout<<"#                                                                                #"<<endl;
    cout<<"#                                                                                #"<<endl;
    cout<<"#                          3.  HIGH (SPEED OF SNAKE IS VERY HIGH)                #"<<endl;
    cout<<"#                                                                                #"<<endl;
    cout<<"#                                                                                #"<<endl;
    cout<<"#                          4.  BACK TO MENU                                      #"<<endl;
    cout<<"#                                                                                #"<<endl;
    cout<<"#                                                                                #"<<endl;
    cout<<"##################################################################################"<<endl;
  cin>>y;
  cout<<endl<<endl;

  switch(y)
  {
  case 1:
    {
        system("cls");
            frame();

        while(!GameEnd)
        {


            draw(x_tail,y_tail);
            input();
            logic(x_tail,y_tail);
            Sleep(300);

        }


            break;
    }
    case 2:
    {
             system("cls");
            frame();
        while(!GameEnd)
        {


             draw(x_tail,y_tail);
            input();
           logic(x_tail,y_tail);
            Sleep(100);

        }


            break;
    }
    case 3:
    {
             system("cls");
            frame();
        while(!GameEnd)
        {


            draw(x_tail,y_tail);
            input();
             logic(x_tail,y_tail);
            Sleep(0);

        }

            break;
    }

    case 4:
        {
                system("cls");
                continue;
                break;
        }
    default:
        cout<<"PLZ SELECT VALID OPTION"<<endl;
        break;
  }

  break;
}
case 2:
    {
        system("cls");
        cout<<"##################################################################################"<<endl;
        cout<<"#                                             |            WARNING               #"<<endl;
        cout<<"#            WELLCOME TO SNAKE GAME           |                                  #"<<endl;
        cout<<"#                                             |     AVOID TOUCHING               #"<<endl;
        cout<<"#      YOU CAN CONTROL  THE SNAKE THROUGH     |                                  #"<<endl;
        cout<<"#                                             |     BOARDERLINE                  #"<<endl;
        cout<<"#                  W(UP)                      |                                  #"<<endl;
        cout<<"#                                             |     IF YOU TOUCH THE             #"<<endl;
        cout<<"#        (LEFT)A         D(RIGHT)             |                                  #"<<endl;
        cout<<"#                                             |     LINE,YOUR GAME WILL          #"<<endl;
        cout<<"#                   S                         |                                  #"<<endl;
        cout<<"#                 (DOWN)                      |     BE OVER                      #"<<endl;
        cout<<"#                                             |                                  #"<<endl;
        cout<<"#                                             |                                  #"<<endl;
        cout<<"#                                 PRESS 1 TO GOTO MAIN MENU                      #"<<endl;
        cout<<"#                                             |                                  #"<<endl;
        cout<<"#                                             |                                  #"<<endl;
        cout<<"##################################################################################"<<endl;
        cout<<endl<<endl;

         int u;

         cin>>u;

         switch(u)
         {
                 case 1:
                    {
                        system("cls");
                        continue;
                        break;
                    }
                    default:
                cout<<"PLZ SELECT VALID OPTION"<<endl;
                break;

         }


     break;

    }
case 3:
    {
        exit(0);
    }

}

   delete [] x_tail;
   delete [] y_tail;
    return 0;
}
}

void frame()// thos funtion is for make starting setup position axis random position of fruite etc....
{
    srand(time(0));//this is for randomly generate fruit on the screen
    GameEnd=false;
    dir=STOP;// in the first head of snake will not move until i press anyting
    x_axis=length /2;//this is the starting position of snake head at the start of the game at xaxis
    y_axis=height/2;//this is the starting position of snake head at the start of the game at yaxis
    food_X=rand()% length ;// this will randomly generate fruit on the screen in xaxis
    food_y=rand()% height ;// this will randomly generate fruit on the screen in yaxis
    scoure=0;
}


void draw(int *x_tail,int *y_tail)// this funtion is for draw the map of snake game on the screewn
{

    SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE), {0,0});// this is for avoiding the flecking this commmand will control the coursor and
    // set  to the origin

    int i=0;
    while(i<length+2)// this loop is for printed the upper side of the map
    {
        cout<<"#";
        i++;
    }
    cout<<endl;
   for(int i=0;i<height;i++)// this loop is for print map in y direction
  {
     for(int j=0;j<length;j++)// this loop is for print map in x direction
     {
       if(j==0)
         {
           cout<<"#";
         }
          if(i==y_axis && j==x_axis)
            {
              cout<<"0";
            }
             else if(i==food_y && j==food_X)
              {
               cout<<"o";
              }
               else
              {
                bool print=0;

                int k=0;//for declaring loop variable
                 while(k<length_tail)// this loop is for print the boy of the snake and make it longer when snake eat fruit
                  {
                       if(x_tail[k]==j && y_tail[k]==i)
                        {
                          cout<<"o";
                          print=1;
                        }
                        k++;
                  }
                     if(!print)
                     {
                        cout<<" ";
                     }
            }
                      if(j==length-1)
                       {
                        cout<<"#";
                        }
        }
        cout<<endl;
    }



      i=0;
     while(i<length+2)// this loop is for printed the lower side of the map
    {
        cout<<"#";
        i++;
    }
    cout<<endl;

cout<<"YOUR Score:"<< scoure<<endl;


ofstream myobj("file1.txt");
if(myobj.is_open())
{
    myobj<<scoure;
    myobj.close();
}
else
{
    cout<<"unable to open file";
}










}

void input()// this funtion is for keyboard input if user put any key
{
    if (_kbhit())//this will return positive integer if character is press through keyboard if nothing press it return 0;
    {
        switch (_getch())//getch in this swith return Ascii valur of the character we press
        {
            case 'a':
            case 75:
                dir = LEFT;
                break;
            case 'd':
            case 77:
                dir = RIGHT;
                break;
            case 'w':
            case 72:
                dir = UP;
                break;
            case 's':
            case 80:
                dir = DOWN;
                break;
            case 27:// if user press esc key loop will end
                GameEnd = true;
                break;
        }

        }
    }



void logic(int *x_tail,int *y_tail)// this is logic funtion where all the logic of game store
{
    int temp_x1=x_tail[0];// this is for swaping and follow the snake tail
    int temp_y1=y_tail[0];
    int temp_x2,temp_y2;
    x_tail[0]=x_axis;//first x element should follow head
    y_tail[0]=y_axis;//first y element should follow head



    for(int i=1;i<length_tail;i++)//this loop is for tail follow by head of snake
    {
        temp_x2=x_tail[i];
        temp_y2=y_tail[i];
        x_tail[i]=temp_x1;
        y_tail[i]=temp_y1;
        temp_x1=temp_x2;
        temp_y1=temp_y2;

    }

switch (dir)// this is for movement of snake if we press a snake position changes
    {
        case LEFT:
            x_axis--;


            break;
        case RIGHT:
            x_axis++;


            break;
        case UP:
             y_axis--;

            break;
        case DOWN:
             y_axis++;

            break;
        default:
            break;
    }


    if(x_axis > length || x_axis < 0 || y_axis > height || y_axis < 0 )//this will end the game if head of sanke touches the wall of the boundaries
   {
       system("cls");
                    cout<<setw(20)<<"##################################################################################"<<endl;
                    cout<<setw(20)<<"#                                                                                #"<<endl;
                    cout<<setw(20)<<"#                                                                                #"<<endl;
                    cout<<setw(20)<<"#                                                                                #"<<endl;
                    cout<<setw(20)<<"#                                                                                #"<<endl;
                    cout<<setw(20)<<"#                    Better luck next time                                       #"<<endl;
                    cout<<setw(20)<<"#                                                                                #"<<endl;
                    cout<<setw(20)<<"#                                                                                #"<<endl;
                    cout<<setw(20)<<"#                                                                                #"<<endl;
                    cout<<setw(20)<<"#                      YOUR SCORE:"<< scoure<<"                                              #"<<endl;
                    cout<<setw(20)<<"#                                                                                #"<<endl;
                    cout<<setw(20)<<"#                                                                                #"<<endl;
                    cout<<setw(20)<<"##################################################################################"<<endl;

                    cout<<endl<<endl;
       GameEnd=true;

   }
            int i=0;
            while(i<length_tail)
            {// this loop  will end if and only  if snake touch its body the game will over
              if(x_tail[i]==x_axis && y_tail[i]==y_axis)
              {
                  system("cls");
                    cout<<setw(20)<<"##################################################################################"<<endl;
                    cout<<setw(20)<<"#                                                                                #"<<endl;
                    cout<<setw(20)<<"#                                                                                #"<<endl;
                    cout<<setw(20)<<"#                                                                                #"<<endl;
                    cout<<setw(20)<<"#                                                                                #"<<endl;
                    cout<<setw(20)<<"#                    Better luck next time                                       #"<<endl;
                    cout<<setw(20)<<"#                                                                                #"<<endl;
                    cout<<setw(20)<<"#                                                                                #"<<endl;
                    cout<<setw(20)<<"#                                                                                #"<<endl;
                    cout<<setw(20)<<"#                      YOUR SCORE:"<< scoure<<"                                             #"<<endl;
                    cout<<setw(20)<<"#                                                                                #"<<endl;
                    cout<<setw(20)<<"#                                                                                #"<<endl;
                    cout<<setw(20)<<"##################################################################################"<<endl;

                GameEnd=true;
              }
                i++;
            }

   if(x_axis==food_X && y_axis== food_y)// this is for score to print on the screen
   {
       srand(time(0));//this is for randomly generate fruit on the screen
       scoure+=5;
       food_X=rand()% length ;// this will randomly generate fruit on the screen in xaxis
       food_y=rand()% height ;// this will randomly generate fruit on the screen in yaxis
       length_tail++;//this will increase the tail of snake
   }

}



