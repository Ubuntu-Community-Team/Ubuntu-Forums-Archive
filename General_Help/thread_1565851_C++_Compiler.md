---
title: "C++ Compiler"
date: 2010-09-01
forum: General Help
---

### Post by borth92 on 2010-09-01
Love linux and Ubuntu in particular. I'm majoring in comp science and software engineering  in college (entering my freshman year). So I Think It would be appropriate to learn to program C and C++ before I get into complex computer classes. What compilers are out there for linux?

---

### Post by steve.horsley on 2010-09-01
The one Ubuntu uses is **gcc**. The command **sudo apt-get install build-essential** will install gcc and some other stuff that you will probably need.

---

### Post by borth92 on 2010-09-01
where does ggc come up? it is not in applications...

---

### Post by Frostshock on 2010-09-01
You run it from the command line.

gcc foo.c -o bar
./bar

This compiles a C source file foo.c to a file called bar, which you can then execute.

g++ foo.cpp -o bar
./bar

This compiles a C++ source file foo.cpp to bar and executes it.

---

### Post by QIII on 2010-09-01
Frostshock's point is that you don't "run" gcc and g++ as you might be used to "running" an application with a GUI.  You'll be doing it in the CLI as he describes.

I highly recommend getting a good book on something like GNU Emacs (which would be a great text editor for starting out.)  I think the one from O'Reilly has a pretty detailed section on all the options available for using various compilers.

I would be willing to be cash money you won't be using an IDE in your coursework to begin with.  Learning what compilers and linkers are and how they behave is part of the deal.  But when you do get to that point, most IDE's will detect the presence of compilers when they are installed and use them.  You won't even see them working any more -- except for the inevitable warnings and errors they will throw back through the IDE.

---

