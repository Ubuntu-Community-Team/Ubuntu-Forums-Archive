---
title: "fopen in c, file not declared"
date: 2011-05-19
forum: General Help
---

### Post by javajames97 on 2011-05-19
Im sorry if this is the wrong kind of question for this site (if you feel there is another forum i should be posting on feel free to let me know), but i seemed to be having some trouble with fopen in C/C++. (and yes, i have tried compiling with gcc instead of g++, with the same results), this is a very rough sketch of a program, but could someone please explain the nature of fopen, and post a program that does compile under the GCC (Gnu Compiler Collection, i.e. gcc/g++ in this case).
```

#include <stdio.h>
#include <stdlib.h>
 //defines file pointer

int main() {
    FILE *ftpr = fopen( "DATA.DAT", "w" ); //opens file writable
    if (fptr == 0) {
        printf("an error occured while opening the file.\n");
        exit (1);
    }
    fprintf(fptr, "start:\n");
    fprintf(fptr, "this is the file content!\n");
    fclose(fptr); //always close your files
    
    printf("ok, some files have been created! I will now attempt to open them\n");
    return (0);
}

```
and the error i get:
```

~/Desktop/CPP_coding$ g++ fopen.cpp -o fopen
fopen.cpp: In function ‘int main()’:
fopen.cpp:7: error: ‘fptr’ was not declared in this scope
fopen.cpp:11: error: ‘fptr’ was not declared in this scope

```
oh and btw, i have tried renaming this as fname.c and compiling it with gcc (and a few other combinations of the 2) but the same error withstanding.

---

### Post by r-senior on 2011-05-19
You are going to kick yourself ...

You have ftpr and fptr.

---

### Post by Petrolea on 2011-05-19
> **javajames97 said:**
> fopen.cpp:11: error: ‘fptr’ was not declared in this scope

**Read errors**. It says its not declared (which means the variable doesn't exist). In your case it is a wrong name as the post above stated.

---

### Post by javajames97 on 2011-05-19
oh.................. oops

---

