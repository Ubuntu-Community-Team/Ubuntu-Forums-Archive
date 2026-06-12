---
title: "some help is needed here"
date: 2006-04-15
forum: General Help
---

### Post by abdalla_salama on 2006-04-15
hi I'm a new ubuntu user 
I need a c compiler ,I've used add application and downloaded gcc 4.0 but I don't know from where I can start the program, I can't find it in the list 
thnx and waiting for ur help

---

### Post by Ramses de Norre on 2006-04-15
sudo apt-get install build-essential (gives the basic compilling tools)
Can you start a c compiler from menu? I always use the make file to compile a program.

---

### Post by oscar on 2006-04-15
The c compiler is a command line program and can only be accessed from there, or from a development program that calls it.

---

### Post by darkarchon on 2006-04-15
gcc is a command line c/c++ compiler, so it isnt in "applications" list.
so u need to run terminal in order to use it. try "man gcc" in terminal to get the list of all available parameters.
but what u prolly need is some kind of IDE, which makes a whole lot more sense if u actually wanna develop something. there is Anjuta for gnome and KDevelop for KDE, both are in repositories. use Synaptic to install either of them.
i hope this helps :)

---

### Post by abdalla_salama on 2006-04-15
I was using borland c on windows xp I need a program like it to use it on ubuntu

---

### Post by Anilkumar on 2006-04-15
u can type the program in vi

for example
type vi filename.c
 then just press i so that u cn write the program. now
come out from it by pressing esc.
now press shift+:.

\now u can compile the program by typing gcc filename .c
now ./a.out to execute it.

now u will have the c world in ur hands

if any error incurrs at any place know the error.make necessary error solving and 
by going into vi filename.c

anil

---

### Post by xenmax on 2006-04-15
[QUOTE=abdalla_salama]I was using borland c on windows xp I need a program like it to use it on ubuntu[/QUOTE]
Look at darkarchon's reply. I have personally not used either Anjuta or KDevelop - you might find more info on them in Programming Talk forum and on Google ofcourse.
Good luck and Happy coding in linux/ubuntu

---

### Post by Afief on 2006-04-15
if you need something similar to borland C you should use XWPE, it's interface is very similar.
to debug though you'll need to use DDD which is a seperate program.
it worked for me in my introduction to computer science college course. should work for you too

PS: for my second CS course: introduction to system programming i actually used Anjuta.

PPS: you will not find the conio.h library in ANY linux C compiler since that's a propertary borland library. but most commands in there can be replaced by the good old Ansi C, which is free for everybody's use and works on every compiler.

PPPS: please use better titles for your threads. "need a C compiler/IDE" or whatever similar title would have told people much more before answering here

---

