---
title: "gtk+ dev using problems"
date: 2010-01-02
forum: General Help
---

### Post by ementos on 2010-01-02
Hi.
I discovered GTK+ library for programs in c++, but when I installed it by:
```
sudo apt-get install libgtk2.0-dev
```
and I've tryed to compile it, I saw my system don't append the librarys I got:
> jozio@ementos-desktop:~/programy/c++$ c++ gtkpp.cpp
gtkpp.cpp:1:21: error: gtk/gtk.h: No such file or directory
gtkpp.cpp: In function ‘int main(int, char**)’:
gtkpp.cpp:5: error: ‘GtkWidget’ was not declared in this scope
gtkpp.cpp:5: error: ‘window’ was not declared in this scope
gtkpp.cpp:7: error: ‘gtk_init’ was not declared in this scope
gtkpp.cpp:9: error: ‘GTK_WINDOW_TOPLEVEL’ was not declared in this scope
gtkpp.cpp:9: error: ‘gtk_window_new’ was not declared in this scope
gtkpp.cpp:10: error: ‘gtk_widget_show’ was not declared in this scope
gtkpp.cpp:12: error: ‘gtk_main’ was not declared in this scope

What have I do to do my gtk+ dev work?
Greet

---

### Post by ementos on 2010-01-15
Okay. I found answer there > [http://ubuntuforums.org/showthread.php?t=134695](http://ubuntuforums.org/showthread.php?t=134695)

Only
```
$ g++ prog.c -o prog.out `pkg-config --libs --cflags gtk+-2.0` 

```
enough.
I always write gcc (as most toturials) not g++ so there were error xD

---

