---
title: "Code Blocks help!!"
date: 2010-06-21
forum: General Help
---

### Post by vikasagartha on 2010-06-21
Hey everyone,

Im a relatively new user of ubuntu - still trying to figure somethings out....I know very little/no programming and i would give it a shot. Im used code blocks to write a few simple programs in c++ such as the default "hello world" program. Code Blocks saves all the files associated with the project in a directory with a few subdirectories and individual files within it. The files include: a bin directory, an obj directory, a "code blocks" file, a "main.cpp", and a layout file. I can run the program by opening code blocks and building/running, but is there a way i can run it from terminal? Which file do i execute, and how do I execute it. Just for fun, I wrote a program that can do a few basic calcs for my math class, and I want to be able to run it through terminal without opening codeblocks every time......can somebody please help?

---

### Post by Pollox on 2010-06-21
In playing around with CodeBlocks a little bit, I wasn't able to reproduce it generating bin and object directories.  But, if you make a file "main.cpp" and compile it with CodeBlocks, the executable will be called "main".  In terminal, use "cd" to navigate to the directory that it is in and type "./main" to run it, or just give the full path (e.g. /home/johndoe/hw1/main ).

I also suggest you become familiar with using g++ in terminal to compile files without CodeBlocks, and at some point look at using makefiles to specify how to compile things.  Another suggestion is to name your files descriptively, rather than calling everything "main.cpp".  Good luck and happy coding.

---

### Post by vikasagartha on 2010-06-21
Thank you for the help - but this produces more questions in my mind :) Could you give a brief idea of g++, and "makefiles"....

---

### Post by Pollox on 2010-06-21
g++ is a compiler (something that turns the code you write into an executable program) for C++.  Other languages have different compilers, and there's even some other ones for C++, but you should use g++.  Just type something like "how use g++" into google and you should get lots of results that you can choose from.  Here's an okay intro [http://www.network-theory.co.uk/docs/gccintro/gccintro_54.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_54.html), but perhaps you can find a better one.

Makefiles are just files you write (they're text files) to save having to write how the whole line for compiling something, and they also allow you to do some more advanced things when compiling.  Then you can just type "make" to run the commands in the file.  Again, you should be able to find lots of tutorials on makefiles via a search engine (I don't know of any good ones in particular).

---

