---
title: "Learning GTK | Can't compile the first 'C' GTK programme"
date: 2011-01-13
forum: General Help
---

### Post by gauravbutola on 2011-01-13
I am trying to learn GTK by myself, I have knowledge of C (I have learned C on winodows not in linux).

I started from here [http://zetcode.com/tutorials/gtktutorial/firstprograms/](http://zetcode.com/tutorials/gtktutorial/firstprograms/)
and unfortunately I got stuck on the very first programme :(

when I try to compile the given code, I get the error ...

> gaurav@gaurav-HCL-ME-Laptop:~/Work/Programming/GTK$ gcc -o simple simple.c `pkg-config --libs --cflags gtk+-2.0`
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
simple.c:1: fatal error: gtk/gtk.h: No such file or directory
compilation terminated.
gaurav@gaurav-HCL-ME-Laptop:~/Work/Programming/GTK$ 


What am I doing wrong here? Do I need to download a compiler or what?


Thanks 
Gaurav Butola

---

### Post by bouncingwilf on 2011-01-13
Looks like you haven't installed the gtk+ package. go to the gtk website for the latest [http://www.gtk.org/](http://www.gtk.org/) 

Also, if you go to the software centre and install the Dev help package, that includes the "official" gtk+ tutorial.

Bouncingwilf

---

