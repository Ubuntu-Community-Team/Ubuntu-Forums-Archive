---
title: "gcc error"
date: 2011-03-04
forum: General Help
---

### Post by aybayrak on 2011-03-04
Hi 
gcc is not working, to try I tried to compile the simple.c file as

[I][B]#include <stdio.h>

int main()
{
    printf("Hello World \n");

    return 0;
}

[/B][/I]The reply is ;

~# gcc -o simple simple.c
/usr/bin/ld: 1: Syntax error: ";;" unexpected
collect2: ld returned 2 exit status


What happened to gcc or ld ?  Thanks

---

