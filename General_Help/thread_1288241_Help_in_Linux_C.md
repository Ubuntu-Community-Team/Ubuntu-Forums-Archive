---
title: "Help in Linux C"
date: 2009-10-11
forum: General Help
---

### Post by supravat on 2009-10-11
#include<stdio.h>
#include<stdlib.h>

main()
{
char ch;
printf("abcd");
ch=getchar();
}

in the above program at first abcd is printed on the screen. Now I want to do if at the time of getchar() "BackSpace" is pressed then only d will be vanished from the screen and only abc will be present on the screen..

I am talking about inserting some function after getchar()..actually i want to built a editor like program. in an editor we type characters & when we press "Backspace" from keyboard it removes one character from screen. I want to implement that thing...please help me.

---

### Post by McNils on 2009-10-11
you should take a look at ncurses. It allaws you to do what you want.

---

