---
title: "Program (MATLAB) not showing up in Software Centre"
date: 2011-08-19
forum: General Help
---

### Post by axeld93 on 2011-08-19
Hi, I'm running Ubuntu 11.04 (Natty Narwhal, right?). Switched from Vista a few days ago and I'm already loving it! Feels like I'm using a powerful machine again instead of some rusty, buggy contraption.

Anyway, just installed MATLAB off a CD. Installation went fine and program seems to be working on par as far as I can tell (apart from that it crashes when I try to load a .fig, but can get around that). However, it is not showing up in the Software Centre, even though it appears to be in the applications folder. Attempts to keep it in the launcher bar fail - it stays there but clicking on the icon doesn't do anything. Any help? Don't want to have to go the applications folder every time I want to run MATLAB...

---

### Post by ubun2freak on 2011-08-19
you just need to make a tiny script, for example: 
#! /bin/sh
DIR=/usr/local/MATLAB/R2010b/bin/
cd $DIR
./matlab
and in desktop, make a new launcher with excecute path to the above script location, choose a picture for your launcher (can download mathlab icon from the internet) -> Done, you have a matlab icon in desktop just like in Window. 

Have fun!

---

### Post by axeld93 on 2011-08-21
Will try that, thanks. :)

---

