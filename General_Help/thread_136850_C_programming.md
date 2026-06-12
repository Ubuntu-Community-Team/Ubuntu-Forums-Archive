---
title: "C programming"
date: 2006-02-26
forum: General Help
---

### Post by simoncoul on 2006-02-26
Alrite in school I am currently taking a C eng programming class, and it is not what I excepted lol.   I said I was gonna make pong by the time I was finished the course but clearly that won't happen, every program that I have to write has all been text based, bank machine, calculator, and encryption.   They all run in the dos prompt(I know, but they teach us in windows so I'm just using windows for now).

Now are u able to write programs that have GUI with C, or do you need to use another language to create them.   It's not  really a big deal but like I have some ideas from some simple programs that I have not seen for linux and I'd wanna make in the summer once I get some free time.

Thanks 

Coulson

---

### Post by az on 2006-02-26
[QUOTE=simoncoul]Alrite in school I am currently taking a C eng programming class, and it is not what I excepted lol.   I said I was gonna make pong by the time I was finished the course but clearly that won't happen, every program that I have to write has all been text based, bank machine, calculator, and encryption.   They all run in the dos prompt(I know, but they teach us in windows so I'm just using windows for now).

Now are u able to write programs that have GUI with C, or do you need to use another language to create them.   It's not  really a big deal but like I have some ideas from some simple programs that I have not seen for linux and I'd wanna make in the summer once I get some free time.

Thanks 

Coulson[/QUOTE]


C is C.  You can use C to write GUI based apps.  You need to use those GUI libraries C interface.

To make an interface, you can use glade and add in the C code.  That's a rapid application development tool.  You can use C to make the command line tool for whatever you want to get done and write the GUI interface for it afterwards.  You can write the GUI interface for a command line application in another language, like python.

You can use Glade with python, too.

Python + glade, as a frontend to a tool written in C is very common.

---

### Post by simoncoul on 2006-02-26
I guess that doesn't seem to hard, would I write each part into a different peice and then put it together in glade?

---

### Post by queenorych on 2006-02-27
See Gtk.  Here is a nice tutorial [http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/) .  GTK is a C gui library.  Others are Qt (C++), wxWidgets (C++), fltk, and many others.  All of the ones I listed will also compile on windows.  For GTK,Qt,FLTK you need the respective windows library installed.  wxWidgets uses native libraries.

Though to start off forget about windows, and just play with GTK on linux.  Start with the hello world tutorial.  Once you learn one GUI system, you've pretty much learned them all.

Good luck.

---

### Post by Gustav on 2006-02-27
To make games and such it can be a good idea to use SDL ([www.libsdl.org](www.libsdl.org) has lots of tutorials).

Just install libsdl1.2-dev and libsdl1.2debian-all and you're ready to go.

---

### Post by simoncoul on 2006-02-27
Hey thanks for the help guys!

---

