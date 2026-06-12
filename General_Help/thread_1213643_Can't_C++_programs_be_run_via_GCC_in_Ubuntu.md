---
title: "Can't C++ programs be run via GCC in Ubuntu?"
date: 2009-07-15
forum: General Help
---

### Post by sreejithbabu on 2009-07-15
I recently installed the Ubuntu 9.04 version.
I found out that C programs can be run by GCC in the terminal window.
It is showing some errors while running C++ programs.
[B][I]Are we able to run C++ programs via GCC?
Or do we have to install a separate program for that? If so how?[/I][/B]

---

### Post by QIII on 2009-07-15
What are you typing in the CLI to run the program and what are the exact error messages you are getting back?

---

### Post by lisati on 2009-07-15
gcc is for C programs. For c++ you need to use g++

BTW, gcc and g++ are *[compilers]("http://en.wikipedia.org/wiki/Compiler")* - you don't actually run the program with them, you use them to preapre a self-contained version of your program that runs by isself.

---

### Post by sreejithbabu on 2009-07-15
> **QIII said:**
> What are you typing in the CLI to run the program and what are the exact error messages you are getting back?

What do you mean by CLI?

---

### Post by sreejithbabu on 2009-07-15
> **lisati said:**
> gcc is for C programs. For c++ you need to use g++

BTW, gcc and g++ are *[compilers]("http://en.wikipedia.org/wiki/Compiler")* - you don't actually run the program with them, you use them to preapre a self-contained version of your program that runs by isself.

Is g++ compiler present in ubuntu?

---

### Post by sreejithbabu on 2009-07-15
How to use the g++ compiler if so present?

---

### Post by QIII on 2009-07-15
You can add it from Synaptic.

Sorry -- Not descriptive enough if you are new to Ubuntu/Debian...

Are you familiar with the Synaptic Package Manager?

---

### Post by QIII on 2009-07-15
CLI -  Command Line Interface.

The terminal.

---

### Post by sreejithbabu on 2009-07-15
How do you get to the Synaptic?

---

### Post by mthalis on 2009-07-15
System->Administrator->Snaptic Package maneger and type package name serch

---

### Post by lisati on 2009-07-15
If your system doesn't already have g++. you can install it from the command line (on the menu at Applications->Accesories->Terminal) using this:
```
sudo apt-get install g++
```
You will be asked for your your password. Don't worry if it doesn't show when you type, this is a normal Ubuntu security precaution, just in case someone is looking over your shoulder.

---

### Post by QIII on 2009-07-15
When you are done, you should be able to go something like this


```
g++ hello.cc
```
```
./a.out
```

and get your output (or whatever...)

```
Hello world
```

---

