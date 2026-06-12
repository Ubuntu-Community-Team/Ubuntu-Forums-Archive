---
title: "x11 installation (with no internet)"
date: 2009-07-23
forum: General Help
---

### Post by mauroz on 2009-07-23
Hi. I'm a new ubuntu user. Please excuse me for my english.
I need to install FLTK (Fast Light Tool Kit ). When I enter 
./configure, it says :
configure: error: Configure could not find required X11 libraries

./configure: line 10538: exit: aborting.: numeric argument required

./configure: line 10538: exit: aborting.: numeric argument required


I also installed GROMACS and it is supposed that a program named ngmx went also installed, but it  didn't appear. In a Makefile say : # Ngmx requires X11 - nothing is built if it doesn't exist.

When I enter “x11” in the search field in Synaptic, I get this packages: (I do not have internet connection, then i suppose they are already installed).

x11-common
x11-apps
pulseaudio-module-x11
libxkbfile1
x11-xkb-utils
xserver-xorg-input-wacom
dbus-x11
libxau6
x11-xfs-utils
libx11-data
libxxf86misc1

What can I do?
Thanks.

---

### Post by Tyke91 on 2009-07-23
you're going to want to install the xorg-dev package (as well as build-essential if you haven't already) if you want to compile fltk.

any reason you don't want to develop in gtk? :)

---

### Post by mauroz on 2009-07-23
[FONT=Times New Roman][SIZE=3]Hi.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I downloaded &#8220;xorg_7.0.0-0ubuntu45.tar.gz&#8221; but I don't know how to install it. There are no configure , readme or install file.   :( [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I  already installed build essential from de cd installer...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I need install fltk because this is a requisition of ProteinShop:[/SIZE][/FONT]
*[SIZE=3][FONT=Times New Roman]ProteinShop requires several libraries for various of its functions.[/FONT][/SIZE]*
*[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]*
*[SIZE=3][FONT=Times New Roman]            1. OpenGL or GL for 3-D rendering[/FONT][/SIZE]*
*[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]*
*[SIZE=3][FONT=Times New Roman]            2. FLTK for GUI                    [http://www.fltk.org/](http://www.fltk.org/)[/FONT][/SIZE]*
*[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]*
*[SIZE=3][FONT=Times New Roman]            3. AMBER for energy computation [/FONT][/SIZE]*
*[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]*
*[SIZE=3][FONT=Times New Roman]                        (pre-built AMBER libraries for Linux and Mac are included)[/FONT][/SIZE]*
[FONT=Times New Roman][SIZE=3]Thanks.[/SIZE][/FONT]

---

### Post by mauroz on 2009-09-18
Thank you. Finally I got internet and could install xorg-dev package.

---

