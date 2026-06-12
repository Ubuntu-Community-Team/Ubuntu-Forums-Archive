---
title: "gdb in emacs"
date: 2010-03-09
forum: General Help
---

### Post by belnac on 2010-03-09
Hi, 

Been trying to make emacs my development IDE on Linux but somehow I cannot seem to debug from within it.

Here's an example of the steps I've taken to get gdb up and running from within emacs.

I have compiled a very simple C++ test program by issuing the command:
g++ -g test.cpp -o test.so

I then issued another command to get gdb up and running:
Run gdb (like this): gdb test.so

The issue I'm having is the binary loads up just fine but I'm unable to get gdb to run the program. 

Tried executing Run from the Gud menu and I get an error message:
Symbol's function definition is void: gud-go

I am also unable to run any commands from within gdb's frame -- after (gdb). I can type them but nothing really happens (like r to run.) 

What am I doing wrong? I am using emacs 23 on Ubuntu 9.1.

---

### Post by belnac on 2010-03-10
I should point out that I'm a Linux noob and may be missing packages perhaps or may have not configured the system properly.

I don't even know how to diagnose whatever's wrong with emacs. So I'd appreciate some pointers that may help me get to the root of these issues.

---

