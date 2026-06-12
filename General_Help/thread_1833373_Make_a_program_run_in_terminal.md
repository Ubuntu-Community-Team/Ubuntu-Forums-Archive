---
title: "Make a program run in terminal"
date: 2011-08-25
forum: General Help
---

### Post by WikedX on 2011-08-25
You know how if you make a simple Hello World in Windows and double click on it, it opens in command prompt? Well I'd like the same thing to happen on Ubuntu. I need to make it so double clicking on a program opens it up in terminal.

The only other way for me to do it is open terminal and manually execute it from there

---

### Post by TeoBigusGeekus on 2011-08-26
Create your program and save it as test.c, say on your Desktop
[PHP]#include <stdio.h>
int main(void)
{
    printf("Hi\n");
    getchar();
    return 0;
}[/PHP]
Compile it
```
gcc ~/Desktop/test.c -o ~/Desktop/test
```
Now create a launcher for it with this command
```
gnome-terminal -e ~/Desktop/test
```
(Replace gnome-terminal with the terminal you use).

---

### Post by aeiah on 2011-08-26
this'll work with any executible cli script or program, incidentally, not just c

---

