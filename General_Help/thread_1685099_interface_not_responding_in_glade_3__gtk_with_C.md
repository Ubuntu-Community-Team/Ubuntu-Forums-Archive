---
title: "interface not responding in glade 3 / gtk with C"
date: 2011-02-10
forum: General Help
---

### Post by axd on 2011-02-10
Hi,

I am a fairly new ubuntu user. I am using ubuntu 10.04 and glade 3 for building a simple interface that uses C .

In my interface , I have created two buttons :  start and stop .To focus on my actual problem , I have created a simpler UI and code .

start button runs a while(1) loop and stop should stop the loop .

The problem is , when I press start , the gui freezes and I cannot press any other button . I cant even close my app.After  some thorough experimentation, I found out that when I press start , it  never comes out of the while loop .

I need the loop to keep running until I press stop . What should i do ?

Here are the functions for the clickable buttons :

code:

void
on_start_button_clicked (GtkButton *button, gpointer user_data)
{

    flag1=0;
    
    while(1)
    {

        printf("**********checking !!!! ********\n\n");
        
        if(flag1 == 1) 
                break;
    }
}


void
on_stop_button_clicked (GtkButton *button, gpointer user_data)
{
 
        flag1=1;     

}

---

