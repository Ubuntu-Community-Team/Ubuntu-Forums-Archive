---
title: "GCC programming with GTK frontend."
date: 2009-12-08
forum: General Help
---

### Post by akshay.sulakhe on 2009-12-08
Hello friends,
             Currently working on some college project where i would like to develop an application where GCC is the backend and frontend designed by using GTK. How to achieve that. I am not expecting any source code. Just need an idea like how to use it inline,command line parameters to compile that application,and packaging. Any links would be appreciated. Also i am preparing a address book. Considering that it is a small application,can you please suggest me such short application which can be prepared easily. Any ideas. Do reply. Thanks. adios.

---

### Post by akshay.sulakhe on 2009-12-08
Also is there any IDE available to do that job. Does Anjuta work for the same.

---

### Post by lewisforlife on 2009-12-08
When you say your program will have a GCC backend, do you mean you will be writing a C program using GTK+ for your GUI?  If so you can compile your GTK+ program written in C like this if the name of your source file was test.c:

```
gcc -Wall test.c -o test `pkg-config --cflags --libs gtk+-2.0`
```

There is a great tutorial @ [http://library.gnome.org/devel/gtk-tutorial/stable/](http://library.gnome.org/devel/gtk-tutorial/stable/).  FYI, you definitely need basic programming knowledge, if not, I would start out with basic C programming, or Python.

---

### Post by WitchCraft on 2009-12-08
> **akshay.sulakhe said:**
> Also is there any IDE available to do that job. Does Anjuta work for the same.

Anjuta is an overkill. Use geany.

---

### Post by lewisforlife on 2009-12-08
There are many IDE's available for use.

[LIST]
[*]GEdit
[*]Anjuta
[*]Emacs
[*]Eclipse
[/LIST]

If you are just starting out, I would recommend just using gedit.  I particularly enjoy Emacs though, but it takes a little getting used to.

---

### Post by jollysnowman on 2009-12-08
> **akshay.sulakhe said:**
> Hello friends,
             Currently working on some college project where i would like to develop an application where GCC is the backend and frontend designed by using GTK. How to achieve that. I am not expecting any source code. Just need an idea like how to use it inline,command line parameters to compile that application,and packaging. Any links would be appreciated. Also i am preparing a address book. Considering that it is a small application,can you please suggest me such short application which can be prepared easily. Any ideas. Do reply. Thanks. adios.

What is the functionality of this address book?

---

### Post by akshay.sulakhe on 2009-12-09
Thanks everybody...Its a small college project. Would like to use that address book to manually add adresses in it or read a csv file.

---

