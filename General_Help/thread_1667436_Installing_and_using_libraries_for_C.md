---
title: "Installing and using libraries for C"
date: 2011-01-14
forum: General Help
---

### Post by VGDude85 on 2011-01-14
Hi, very new to Linux and C and I am trying to get my libraries to compile and run with this book example but I can't seem to get them to compile and run.

Here is the book example code:

```

/*
 * File: addlist.c
 * ---------------
 * This program adds a list of numbers.  The end of the
 * input is indicated by entering a sentinel value, which
 * is defined by setting the value of the constant Sentinel.
 */

#include <stdio.h>
#include "genlib.h"
#include "simpio.h"

/*
 * Constants
 * ---------
 * Sentinel -- Value that terminates the input list
 */

#define Sentinel 0

/* Main program */

main()
{
    int value, total;

    printf("This program adds a list of numbers.\n");
    printf("Use %d to signal the end of list.\n", Sentinel);
    total = 0;
    while (TRUE) {
        printf(" ? ");
        value = GetInteger();
        if (value == Sentinel) break;
        total += value;
    }
    printf("The total is %d\n", total);
}

```I am trying to import and use these libraries:
```

#include "genlib.h"
#include "simpio.h"

```Every time I compile and run it. It throws an error stating it can't define the GetInteger() method.

The directory I use is:
```
cd cs/2213/chap1ex
```The C file and all the libraries are in this folder. Libraries include genlib.h, genlib.c, genlib.o and same goes for simpio.

I compile and run the C program using the 

```

gcc addlist.c -o addlist
gcc -o addlist addlist.c
./addlist

```Any help would be great.

---

### Post by Pollox on 2011-01-14
Where is this GetInteger() function defined? It's probably in the libraries given with your book, as this cs/2213/chap1ex directory is something you made and not something standard to linux installs. Are you sure there is a GetInteger() function defined somewhere? Posting the exact error message you received would have been helpful. Also, the programming section of ubuntuforums would probably be of more help.

---

