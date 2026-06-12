---
title: "Can't Run Fortran Programs in ubuntu"
date: 2010-02-10
forum: General Help
---

### Post by nathan.chase on 2010-02-10
Dear community,
I am using the gfortran compiler to compile fortran 90 programs. I recently reformated and reinstalled the compiler. I can compile programs that work on other computers but they don't work on my computer. Any idea why I can compile functional fortran programs but can't run them in the terminal. 

I am dual booted Karmic Koala Ubuntu/Vista. 

thanks,
Nate

---

### Post by squaregoldfish on 2010-02-11
When you say they don't work, can you give some details? It's hard to help with what you've said so far.

---

### Post by nathan.chase on 2010-02-11
Normally when I compile a program I generate an execuatible and then enter that executable's name into the terminal and the program runs in the terminal. In this case the terminal errors and says "not a valid command" or something to that effect. Here is an example I entered into my terminal

> gfortran datasort.f90 -o RUNdatasort.exe
> (comes back with no errors from compiling
> RUNdatasort.exe (press enter)

error- not a valid command (or something to that effect)


On my windows side I can get things to compile and run on the command line now.

---

### Post by blur xc on 2010-02-11
> **nathan.chase said:**
> Normally when I compile a program I generate an execuatible and then enter that executable's name into the terminal and the program runs in the terminal. In this case the terminal errors and says "not a valid command" or something to that effect. Here is an example I entered into my terminal

> gfortran datasort.f90 -o RUNdatasort.exe
> (comes back with no errors from compiling
> RUNdatasort.exe (press enter)

error- not a valid command (or something to that effect)


On my windows side I can get things to compile and run on the command line now.
```

./proram-name
```Linux only looks in directories specified my your path environment variable, so even you are currently in the same directory as your executable, it won't run unless you explicitly specify to look in your current directory - ./

BM

edit -ps, you may also need to 
```
chmod u+x program-name
```to give your program executable permissions.


edit pps- Linux (all tne *nix's) don't use extensions to define the file type.  So, you don't see .exe files in linux.  And changing the extension does not change what type of file it is..  IIRC, the "file" command can tell you what kind of file they are...

---

### Post by nathan.chase on 2010-02-11
thanks alot I'll try running ./RUNdatasort.exe when I get over to my linux side later. Hope that will work. I only add the exe for when I want to run the program on windows computers.

-nate

---

### Post by lisati on 2010-02-11
> **nathan.chase said:**
> Normally when I compile a program I generate an execuatible and then enter that executable's name into the terminal and the program runs in the terminal. In this case the terminal errors and says "not a valid command" or something to that effect. Here is an example I entered into my terminal

> gfortran datasort.f90 -o RUNdatasort.exe
> (comes back with no errors from compiling
> RUNdatasort**[COLOR="Red"].exe[/COLOR]** (press enter)

error- not a valid command (or something to that effect)


On my windows side I can get things to compile and run on the command line now.

OK I think I see what's happening here. 
An "exe" file is a file that is ready to be run on Windows or MS-DOS, and won't run without help on Ubuntu.

Your options include recompiling the source file for Ubuntu (NOT the exe file) or running the EXE file with Wine.

By the way, is the name of the file really "RUNdatasort.exe" or is there a missing space?

---

### Post by blur xc on 2010-02-11
> **lisati said:**
> OK I think I see what's happening here. 
An "exe" file is a file that is ready to be run on Windows or MS-DOS, and won't run without help on Ubuntu.

Your options include recompiling the source file for Ubuntu (NOT the exe file) or running the EXE file with Wine.

By the way, is the name of the file really "RUNdatasort.exe" or is there a missing space?

I think he's compiling his program to run in Linux, but out of habit is sticking the .exe extension on it like you would in windows.  He's using gfortran (not a programmer here) which I would think is the gnu fortran compilier, just like gcc is the gnu c compiler for linux...

Lose the .exe extension - your linux friends will look at you funny.  And if you pass off a .exe to another linux user, they will try to run it in Wine and then get all pissed when it doesn't work.  

Extensions in linux mean nothing to the OS, they are just used in some cases for the benefit of the user.  

BM

---

