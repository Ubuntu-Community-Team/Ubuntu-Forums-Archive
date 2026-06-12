---
title: "3 problems with 9.10"
date: 2010-02-09
forum: General Help
---

### Post by ct2000 on 2010-02-09
Hi everyone I have just recently downloaded 9.10 to my desktop. it is a dual boot system with windows xp. I am hiving 3 problems,
1 right in the middle of doing something it doesn't really matter what the computer freezes the mouse moves and it will highlight say a tab in firefox but if I click the mouse nothing
2 if I leave the computer overnight in the morning it doesn't work its just a black screen but the computer is on
3 this keeps happening to my wife, when she is playing a game (one of the ones that came loaded in ubuntu) it will all of a sudden close ubuntu and go to the login screen

 thanks for reading this and i hope you can help

---

### Post by Vaphell on 2010-02-09
1. freezing would mean cpu load spiking, run **top** in terminal and keep that window for some time. Look for anything with surprisingly high cpu %
3. probably bug in gfx drivers causes X (GUI on top of raw linux) to crash. try to disable compiz and see if things got more stable. what's the chipset btw?

---

### Post by jamesisin on 2010-02-09
Check to see if your system is set to sleep after some period.  You can disable that to see if that helps your situation.  (I am thinking of 2 above.)

System --> Preferences --> Power Management

---

### Post by ct2000 on 2010-02-09
jamesisin I checked those settings and they are set to never

Vaphell I have top running now and you will have to forgie me but how do I disable compiz and how do I see system info in ubuntu? I figure ill get all the info posted on here but I dont know how to get it

---

### Post by jken146 on 2010-02-09
System->Preferences->Appearance In the last tab (visual effects) choose 'none' to disable compositing (compiz).

As for finding out what graphics card you have, type ```
lspci | grep VGA
``` in a terminal.

---

### Post by ct2000 on 2010-02-10
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

o that is the chipset
on number 2 i think i have it resolved i just turned off the screen saver and come down this morning and it worked fine 
on number 1 i was watching system monitor and ff is eating alot of cpu as is gnome system monitor
as far as number three i have no idea I went to disable compiz but it already was so for the heck of it i tried to change the setting and it said it couldnt load the visual effects

---

### Post by ct2000 on 2010-02-10
ok just to update the freezing problem happened with nothing but the picture file opened i left the mouse hovering over a file stepped away from the computer for a couple of minutes and when i came back the computer the only thing that would work is the mouse

---

### Post by woodmaster on 2010-02-10
Had Random freezes as you described and this fixed my problems.  Ubuntu runs flwalessly now.  A very long time since it froze on me.
[HTML]http://ubuntuforums.org/showthread.php?t=1309015&page=15[/HTML]

---

### Post by ct2000 on 2010-02-10
woodmaster i tried what it said i idid get the kernel to update but noe it has some errors and when i tried the other it tells me permission denied. this is all very new to me i used 9.04 on my laptop but i messed around in the terminal and messed it up now all i get when  i start it  is GRUB 15 error

so anythign in the terminal will have to be explained sorry

---

### Post by ct2000 on 2010-02-14
ok well installing the newer kernel didn't work it still freezes up. so if you folks would be so kind to help me with the other step in the terminal I would greatly appreciate it. 
thanks for all the help to this point

---

### Post by iponeverything on 2010-02-14
> **ct2000 said:**
> ok well installing the newer kernel didn't work it still freezes up. so if you folks would be so kind to help me with the other step in the terminal I would greatly appreciate it. 
thanks for all the help to this point

Is your system up to date as far update manager is concerned? I have seen a few threads about lockup's on 9.10 that were resolved after the system updated..

Also, it might be useful for you to search around with google with your hardware spec's and 9.10, lockup and such.

---

