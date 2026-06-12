---
title: "apue.h header file not found"
date: 2010-04-01
forum: General Help
---

### Post by Anee on 2010-04-01
Hello all,

Iam trying to execute the following code from the book Advanced Programming in the UNIX® Environment: Second EditionBy W. Richard Stevens, Stephen A. Rago

Iam using ubuntu Hardy.

In usr/include the header file apue.h is not found.From where do i get this header file.

--------------------code----------------------------------
#include<stdio.h>
#include <apue.h> 
#include <dirent.h> 
 
int main(int argc, char *argv[]) 
{ 
    DIR             *dp; 
    struct dirent   *dirp; 
 
    if (argc != 2) 
        err_quit("usage: ls directory_name"); 
 
    if ((dp = opendir(argv[1])) == NULL) 
        err_sys("can't open %s", argv[1]); 
    while ((dirp = readdir(dp)) != NULL) 
        printf("%s\n", dirp->d_name); 
 
    closedir(dp); 
    return 0; 
} 

---------------------------------------------------------------
$gcc listdir.c 
listdir.c:2:18: error: apue.h: No such file or directory

----------------------------------------------------------

---

### Post by kushal.kumaran on 2010-04-01
The "apue" from apue.h stand for Advanced Programming in the Unix Environment.  The source code for the book is available from the book's site[1].

[1] [http://www.apuebook.com/](http://www.apuebook.com/)

---

### Post by sostentado on 2012-02-02
This might be old but i just want to share for future reference..

For me i haven't compiled apue.h source but when i used it in a code, i simply hardcode the directives like
[B]
#include "youWorkingDir/here/apue.2e/include/apue.h"[/B]

or for instance your C file is in same folder as apue.2e
[B]
#include "apue.2e/include/apue.h"[/B]

These compiles your C source without errors.

---

