---
title: "problems with: gcc, g++, etc..."
date: 2006-06-02
forum: General Help
---

### Post by rbprogrammer on 2006-06-02
am i the only one with a problem with C? so i have this code:
[FONT="Courier New"][INDENT]
#include <stdio.h>
int main()
{
    printf("Hello World!\n");
    return 0;
}
[/INDENT][/FONT]
and then i do the command:
[FONT="Courier New"][INDENT]gcc -o test -ansi test.c [/INDENT][/FONT]
it doesnt compile and i get these errors:
[FONT="Courier New"][INDENT]test.c:2:19: error: stdio.h: No such file or directory
test.c: In function ‘main’:
test.c:5: warning: incompatible implicit declaration of built-in function ‘printf’
[/INDENT][/FONT]
all i need is a basic program so i will get used to c/c++ programs in linux, but i just cannot get this to work...

---

### Post by murph2481 on 2006-06-02
try:

sudo apt-get install build-essentials

---

### Post by rbprogrammer on 2006-06-02
i get this:
[INDENT]$ sudo apt-get install build-essentials
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-essentials
[/INDENT]

---

### Post by elektronaut on 2006-06-04
it's called build-essential - without **s** at the end

---

### Post by murph2481 on 2006-06-06
oops sorry..

---

