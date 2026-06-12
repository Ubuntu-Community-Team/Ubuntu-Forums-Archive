---
title: "Help  with GCC and NetBeans"
date: 2011-01-13
forum: General Help
---

### Post by vollager on 2011-01-13
Hi people, i have a problem and i need fix it quickly, i try to compile a program in this 2 compilers and send an error:

```
build/Debug/GNU-Linux-x86/newmain.o: In function `main':
/home/phentux/NetBeansProjects/CppApplication_1/newmain.c:15: multiple definition of `main'
build/Debug/GNU-Linux-x86/main.o:/home/phentux/NetBeansProjects/CppApplication_1/main.cpp:15: first defined here
collect2: ld returned 1 exit status
make[2]: *** [dist/Debug/GNU-Linux-x86/cppapplication_1] Error 1
make[1]: *** [.build-conf] Error 2
make: *** [.build-impl] Error 2

```is the same for the 2, i see the synaptic and i cant see anything weird, can u help me?

---

### Post by GregBrannon on 2011-01-13
It looks like an error with your source code, but I would have to see the code to be sure.  Show the source if you can.  Know that we're not allowed to help with homework.

---

### Post by vollager on 2011-01-13
xD yeah i know but the source file its correct see

```

#include <stdio.h>
#include <stdlib.h>

/*
 * 
 */
void hanoi(int n,int com, int aux, int fin);

void main(void) 
{
     char com='A';
    char aux='B';
    char fin='C';
    int n;

    printf("\nN£mero de discos: ");
    scanf("%d",&n);
    fflush(stdin);

    printf("\n\nLos movimientos a realizar son: \n");
    hanoi(n,com,aux,fin);

    return (EXIT_SUCCESS);
}
void hanoi(int n,int com, int aux, int fin){

    if(n==1){
        printf("%c->%c",com,fin);
    }
    else{
        hanoi(n-1,com,fin,aux);
        printf("\n%c->%c\n",com,fin);
        hanoi(n-1,aux,com,fin);
    }
}

```

is the compiler

---

