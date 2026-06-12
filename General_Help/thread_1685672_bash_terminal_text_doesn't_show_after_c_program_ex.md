---
title: "bash terminal text doesn't show after c program exits"
date: 2011-02-11
forum: General Help
---

### Post by dunsta on 2011-02-11
I think this may be a c problem rather than Ubuntu's, but somebody might know why this program and Terminal aren't getting along?

I have a program where 
1. the user can choose to display an ascii pic from three options
2. the pic displays in a curses window for, say 10 seconds (10 is a cmd line arg)
3.the menu of the 3 pics returns
if the user hits ctrl-c, the program should display a message, wait 3 seconds, then exit (using exit(1)).
 
I have a trial program that uses signal(SIGINT, func), that exits fine.
BUT, when i try a similar func in the middle of a curses program, the  signal function exits, BUT then the terminal screen will not show any  characters typed in, and the prompt will be LINE-1 COL+1
 
I'm new to signals and curses, so I don't know where the problem lies
 
here is my test program for signal(SIGINT,func), it works fine

  Code:
 #include<stdio.h>
#include<signal.h>

void handler(void)
{
    printf("timeout!\n");
    signal(SIGALRM, handler); //reset the action
    sleep(5); 
    exit(1);
}

int main(void)
{
    signal(SIGINT,handler); 

    while(1)
    {
        printf("PRESS <RETURN>\n");
        getchar();
    }
}

here is my main and func from the prog that causes terminal to mess up
  Code:
 #include<stdio.h>
#include<stdlib.h>
#include<signal.h>
#include<curses.h>

void func_handler(void)
{
    printf("\nquitting in 3 seconds\n");
    refresh();
    signal(SIGALRM, func_handler); //reset teh action
    sleep(3); 
    **endwin(); // forgot this**
    exit(1);
}

 Code:
 #include<stdio.h>
#include<curses.h>
#include "lib.h"
#include <signal.h>
#include<stdlib.h>

int main(int argc, char *argv[])
{
    int delay;
    
    signal(SIGINT,func_handler); //set the action
    
    
    
    
    sscanf(argv[1],"%d", &delay); //get argv[1] and convert from string to int
                                            //using sscanf

    char choice;
    initscr();
    choice =' ';
    do 
    {
        move(13,0);
        addstr("\nPress 1 for Sam,2 for Norm,3 for Rad 4 to quit: ");
        refresh();
        
        choice = getchar();
        if(choice =='1')
        {
            sd();
            sleep(delay);    
            
        }
        else if(choice =='2')
        {
            nd();
            sleep(delay);
        }
        else if(choice =='3')
        {
            rei();
            sleep(delay);
        }
    }while(choice != '4');
    
    endwin();
}

---

### Post by Habitual on 2011-02-11
dunsta:

Use the Code tag when you post. This will put raw code in a pretty little box in the post and reduce the possibility of a mis-interpretation.
It is the **[SIZE="4"]#[/SIZE]** symbol the editor.
You seem to have posted the actual code twice in the same post.

```
#include<stdio.h>
#include<signal.h>

void handler(void)
{
printf("timeout!\n");
signal(SIGALRM, handler); //reset the action
sleep(5);
exit(1);
}

int main(void)
{
signal(SIGINT,handler);

while(1)
{
printf("PRESS <RETURN>\n");
getchar();
}
}

here is my main and func from the prog that causes terminal to mess up
Code:
#include<stdio.h>
#include<stdlib.h>
#include<signal.h>
#include<curses.h>

void func_handler(void)
{
printf("\nquitting in 3 seconds\n");
refresh();
signal(SIGALRM, func_handler); //reset teh action
sleep(3);
endwin(); // forgot this
exit(1);
}

Code:
#include<stdio.h>
#include<curses.h>
#include "lib.h"
#include <signal.h>
#include<stdlib.h>

int main(int argc, char *argv[])
{
int delay;

signal(SIGINT,func_handler); //set the action




sscanf(argv[1],"%d", &delay); //get argv[1] and convert from string to int
//using sscanf

char choice;
initscr();
choice =' ';
do
{
move(13,0);
addstr("\nPress 1 for Sam,2 for Norm,3 for Rad 4 to quit: ");
refresh();

choice = getchar();
if(choice =='1')
{
sd();
sleep(delay);

}
else if(choice =='2')
{
nd();
sleep(delay);
}
else if(choice =='3')
{
rei();
sleep(delay);
}
}while(choice != '4');

endwin();
} 
```

We hope this helps us help you.

---

