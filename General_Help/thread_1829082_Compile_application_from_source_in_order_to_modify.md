---
title: "Compile application from source in order to modify"
date: 2011-08-20
forum: General Help
---

### Post by FireStormOOO on 2011-08-20
Hello, users of the mighty Ubuntu, I'm fairly new to the Linux world, and while I have written programs before on Windows, Ubuntu seems to be a whole new beast.

I have the source of the application I want to modify, as well as the list of dependencies I need in order to compile.  I got the source code for those and compiled/installed them.  I'm fairly sure that all of the dependencies are installed.  However, when I go to run the compiler it crashes while parsing some of the code.

I had the application installed before, and it ran.  After tinkering around trying to get the source to compile, the app no longer runs either.  It crashes, and if run from the CLI, spits out something about not finding one of the files from the SDL library.

So obviously I did something wrong to mess everything up, because I'm in a deeper hole than when I started:confused:.  Anyone know how I would go about fixing this?  Or even starting with a clean slate so that I can have another go at it?

---

### Post by AbtZ on 2011-08-20
Generally speaking, if something is in the repository, and is a recent enough version, you should get it from there rather than compile it from source. In other words, don't compile the dependencies unless you cannot find them, or their required version, in the repo.

**Tip**: To have apt install the required dependencies automatically, try running
```
sudo apt-get build-dep <application name>
```

As for your problem specifically, I'm not sure what exactly went wrong, without more provided information. Which compilations succeeded? Where did it fail? All I can say now is that it seems that either there is a dependency missing, or your tinkering with the code has it fail. Try uninstalling everything, then compiling & installing the application without modifying the code at first.

Good luck!

---

### Post by FireStormOOO on 2011-08-20
Thanks for the reply.  I realized after the fact that I didn't need to compile the dependencies from source.  I think something went wrong when I compiled and installed the dependencies.  The code I have is the unmodified release of Globulation 2.  I'm currently trying to get it to compile and run from source BEFORE I start making changes.

So I guess the question to ask now is how do I figure out what I installed where, and how do I undo the damage I did?  I used checkinstall to install the programs from source.  I might have accidentally installed some multiple times.  Specifically, I think the problem lies within SDL, simple direct-media layer.

Edit:  Just ran the code you gave me and it fixed the app!  Going to try compiling now.  It appears that I installed something incompatible as well as removing a bunch of dependencies somehow.  Going to try compiling now.

---

### Post by FireStormOOO on 2011-08-20
I can hardly believe it was that simple.  I'm up and running 100% :D

---

