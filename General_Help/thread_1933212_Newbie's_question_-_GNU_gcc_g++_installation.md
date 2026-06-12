---
title: "Newbie's question - GNU gcc g++ installation"
date: 2012-02-28
forum: General Help
---

### Post by chenxinghao on 2012-02-28
It was suggested that I do the following to get C/C++ compilers installed:

sudo apt-get install gcc g++ build-essential

However, after I installed Ubuntu 11.10 (without running the above command) it seems that the GNU C compiler gcc is already in the system. I had my old C codes compiled successfully.

Now, I wrote some C++ codes with a makefile. The "make" returned "g++: command not found". 

My questions are: 

(1) If I only need to install the g++ portion, shall I remove the "gcc" part from the above command?

(2) If I install both gcc and g++ using the above command line, would there be any potential problems (since a gcc version is already in the system)?

---

### Post by TeoBigusGeekus on 2012-02-29
You shouldn't get this error - g++ is included in gcc (Gnu Compilers' Collection).
Check your makefile again...

---

### Post by chenxinghao on 2012-02-29
Here is what in the makefile:

INCLUDE = $$HOME/include
LDFLAGS = -lm

CFLAGS  = -O -I$(INCLUDE)

OBJS =     readckt.o

cadac: $(OBJS) readckt.h
    ${CC} ${CFLAGS} -o $@ $(OBJS) ${LDFLAGS} 

clean : 
    rm -f $(OBJS)

Here is the output message:

~/SEST-TECH/cadac$ make
g++    -c -o readckt.o readckt.C
make: g++: Command not found
make: *** [readckt.o] Error 127
~/SEST-TECH/cadac$ 


I copied the makefile file from my old C code program (with several .c and .h files) and replaced the necessary .h and .C for this C++ exercise. It just has one .C file and several .h files.

The makefile works fine with the old C programs on my this Ubuntu 11.10 box - I made no changes to the old C source files and compiled them on this Ubuntu box and ran and verified the functions with old results.

I am learning C++ on this Ubuntu computer and need a C++ compiler to work.

Thank you.

---

### Post by TeoBigusGeekus on 2012-03-01
```
#include <iostream> 
int main() 
{ 
using namespace std; 
cout << "Hi there."; 
cout << endl;  
return 0; 
} 
```
Save it as test.cpp and give 
```
g++ -o test test.cpp
```
Does it give you any error messages?

---

### Post by chenxinghao on 2012-03-01
Saved the file in test.C file.
Using g++ doesn't get error; using gcc got the error.

My understanding is to use gcc to compile C programs and use g++ to compile C++ program.

My second note is on the makefile - somehow it doesn't compile the C++ code.

---

### Post by TeoBigusGeekus on 2012-03-02
Try adding this command
```
CC=g++
```
at the beginning of your makefile,

---

