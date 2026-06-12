---
title: "Turbo C libraries on gcc problem"
date: 2010-10-10
forum: General Help
---

### Post by Vishnu V on 2010-10-10
Hi
 I tried to add turbo c libraries to gcc according to this [link]("http://arun.wordpress.com/2006/01/21/graphics-in-linux/")

But when i tried to compile source i got the following error
```

root@vishnu-laptop:/media/storage/Backup/install/TurboC-source# make
cc -O0 -g -DWITH_X -I/usr/X11R6/include -Wall -c -funsigned-char -o arc.o arc.c
In file included from graphics.h:45,
                 from arc.c:36:
TurboC.h:60:21: error: ncurses.h: No such file or directory
In file included from graphics.h:46,
                 from arc.c:36:
conio.h: In function ‘getchNcurses’:
conio.h:213: warning: implicit declaration of function ‘getch’
conio.h: In function ‘ungetchNcurses’:
conio.h:223: warning: implicit declaration of function ‘ungetch’
conio.h: At top level:
conio.h:264: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
make: *** [arc.o] Error 1


```

Please help me to solve this

Thanks for any help

---

### Post by srs5694 on 2010-10-10
It looks like you need to install some ncurses header files package, probably libncurses5-dev. Try typing "sudo apt-get install libncurses5-dev" to install it, then try again. It's possible you'll run into another problem of the same sort. If so, look at the name of the file that's not been found (ncurses.h in this case) and use Synaptic to search for a development package (one with "-dev" in the name) with a similar name.

---

### Post by Vishnu V on 2010-10-16
Thank you very much . Problem Soved

---

### Post by richardpd on 2010-12-06
I am going to try this soon on my Ubuntu 10.04 (I'm on my VistaPC at the moment!).
 
I have already installed DosBox on my Ubuntu 10.04 & have BGI(?) TurboC setup in DosBox (TC.exe) but I think it would be simpler to install TurboC lib ([http://www.sandroid.org/TurboC/](http://www.sandroid.org/TurboC/)) directly in this way and compile & run from terminal in normal way if possible. I hope it will work when I can find time to try it over the next few days. 
 
I want to do some graphics programming in C and there are lots of code examples in BGI/TurboC so I hope to get some of these working in Ubuntu 10.04. I may try other C graphics libraries (in fact I have libgraph installed already) including SDL and even OpenGL. Most internet posts I have found on this subject seem to advise using DosBox or other emulator for TC but I think installing and using TurboC directly in terminal would be more useful. After I try this I will post an update of how successful it was for me.....
 
----------------------------------------
Ubuntu-Uwhatu

---

