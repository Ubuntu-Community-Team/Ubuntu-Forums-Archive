---
title: "G++ Problems"
date: 2010-02-23
forum: General Help
---

### Post by rocket16 on 2010-02-23
Hello all. I am a Java/VB Developer (Not Professional, just hobby), and thinking to start developing and learning C++. But, when I try to compile a first programme of Mine, in C++, the gnu c++ Compiler gives error. It nicely compiles in Boreland and Turbo C++, but fails in Ubuntu. The programme is a Quadratic Equation solver, and when trying to be compiled, it shows: 
quadratic.cpp:1:21: error: iostream.h: No such file or directory
quadratic.cpp:2:18: error: conio.h: No such file or directory
quadratic.cpp:4: error: ‘::main’ must return ‘int’
quadratic.cpp: In function ‘int main()’:
quadratic.cpp:6: error: ‘clrscr’ was not declared in this scope
quadratic.cpp:12: error: ‘cout’ was not declared in this scope
quadratic.cpp:13: error: ‘cin’ was not declared in this scope
quadratic.cpp:22: error: ‘cout’ was not declared in this scope
quadratic.cpp:23: error: ‘getch’ was not declared in this scope

I am attaching the Source Code of the Programme. I have all the dependencies installed, and am confused. So, what to do to compile this programme in Ubuntu? (And, please don't ask me to compile this in Windows. I hate Windows, and can't live without Ubuntu). :(

---

### Post by rocket16 on 2010-02-23
Additionally, I tried to use Anjuta and CodeLite for C++ IDE. But, in Anjuta, when I try to compile, the Programme closes suddenly. And, in CodeLite, the entire Build Menu is faded, and can't be used. I discussed the matter with the #Ubuntu Channel Mebmers, and they told me that it is the problem related to Configuration. How can I set up their Configuration? (I have Blue Java working excellently here, but want C++ as well, because to me, Java + C++ = Perfect).

---

### Post by pirlo89 on 2010-02-23
in "C" , you type ```
#include<stdio.h>
``` for input and output functions.

in "C++" , you type ```
#include<iostream>
using namespace std;
``` for input and output functions.

and ```
#include<conio.h>
``` is a windows header file (i think).

and instead of ```
#include<math.h>
``` , would better be ```
#include <cmath>
```Remark: i am a beginner myself, but these adjustments should work.

---

### Post by pirlo89 on 2010-02-23
one more thing, you probably don't need ```
getch();
``` at the end in linux, i am assuming you are using it to see your output in windows.

---

