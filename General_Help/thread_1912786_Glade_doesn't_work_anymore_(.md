---
title: "Glade doesn't work anymore :("
date: 2012-01-21
forum: General Help
---

### Post by Gawains Green Knight on 2012-01-21
Can anyone help with my glade problem? It suddenly stopped working! Same files and everything that used to work is no longer working?

My gcc line is: 

gcc -Wall -lm -g -o gst gst.c -export-dynamic `pkg-config --cflags --libs gtk+-2.0 --cflags --libs libglade-3.0 gmodule-3.0` -w

and the error is 


/usr/bin/ld: /tmp/ccPgdQcd.o: undefined reference to symbol 'sin@@GLIBC_2.0'
/usr/bin/ld: note: 'sin@@GLIBC_2.0' is defined in DSO /usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/libm.so so try adding it to the linker command line
/usr/lib/gcc/i686-linux-gnu/4.6.1/../../../i386-linux-gnu/libm.so: could not read symbols: Invalid operation
collect2: ld returned 1 exit status

---

### Post by imachavel on 2012-01-21
[http://glade.gnome.org/](http://glade.gnome.org/)

this?? Trying to write some code?? :popcorn:

ummm, why don't you un install it, then reinstall it via terminal or however you did it. I'm supposing all the code you've written is saved in extension files in certain directories. So go to those directories, and then I don't see why you can't re use the same file extensions and re open those directory files once you have uninstalled and reinstalled glade.

Or does glade have deeper working abilities then just writing code, is it configured into your file system some how? If not is some saved configuration somewhere dependent on glade? Otherwise it appears that glade simply is a code writing tool.

---

### Post by imachavel on 2012-01-21
sorry my mistake it writes code for front end gui code? Ok so then an application you've written or the gui OS reconfiguration for certain code is not working? Basically something front end gui isn't working because of this error and you need to fix it. And the front end code is probably coded in string to back end code??

well ****, I don't know what to tell you. I don't know code, I am learning my first helloworld in python, java, and c and barely know how to compile and open the files. I am learning functions and modules for my first week into this, and just don't know. Good luck though

---

### Post by Gawains Green Knight on 2012-01-21
Ahhh not too sure how it works, it always worked fine in the past though. I have a file that was created using glade which tells the program where the buttons and things are in the window, which gets read by the c code. There's some preamble to the c code, and some code to read inputs and respond to button presses. All of this used to work. 

I don't know what the error means though?

---

### Post by Gawains Green Knight on 2012-01-21
I'm thinking glade has updated and my code is still using th old stuff. I can't even open my glade file in glade anymore.... guess I need to redo all my glade stuff again.....

---

### Post by pbrane on 2012-01-21
The errors in the OP are about the linker failing to find libm. Try adding **-lm** *after* the pkg-config parameters. The order is important.

I don't know why you wouldn't be able to open your glade file though. I have glade files created several years ago that will open with the current glade version 3.10.0. The glade file is just a text file, have a look at it.

---

### Post by ahmet_der on 2012-04-22
You should install gcc-4.4 with development files and try to recompile with it.

---

