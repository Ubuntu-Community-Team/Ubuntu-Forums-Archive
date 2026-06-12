---
title: "gedit c++"
date: 2011-10-13
forum: General Help
---

### Post by coreyscx on 2011-10-13
so today i learned that (stupid i know) you can make a c++ file type from anything basically even gedit.and can compile it using the g++ compiler from mingw..my questions are

1..why does ubuntu come with mingw (g++) yet in the repositories an software center mingw is NOT installed?

2. the executable file type that i create from compiling a g++ source code in gedit..can i turn that into ubuntu or linux native code so i can start making programs? (has to be native if the computer can read it off the bat) i mean can i turn them into .deb packages?

---

### Post by WorMzy on 2011-10-13
g++ is part of the GNU Compiler Collection (GCC), and is provided by the g++ package.

---

### Post by carranty on 2011-10-13
1. I'm not familiar with mingw but I'm pretty sure Ubuntu does not include it as standard.  From a google search it looks to be a Windows program. If you want to compile C++ code in Ubuntu  open a terminal and type 

g++ [File]

to compile the file.  Also 'clang' is a very good compiler for people new to programming.

2. I'm not sure what you mean by native code.  Whatever language you use to create a program, be it C, C++, Python, JAVA or whatever, the source code is just a text file (and yes you could use gedit to write it, though I'd recommend something more robust such as vim or emacs).  And you can view that text file on any Windows, Mac, or linux system. In some languages like C++ you use a compiler to convert the text file into an executable, and in some like Python you don't. 

How much experience have you with programming?  If your just starting out I wouldn't worry about .deb files yet.  Just learn how to program first.

---

### Post by carranty on 2011-10-13
I may have misunderstood your second question.  Are you asking how to run programs in Ubuntu that you have written in C++ and compiled with g++?  If so, they are already executable and will run quite happily in Ubuntu.

---

