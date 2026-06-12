---
title: "over 50% of cpu cycles being used whlie idle"
date: 2009-08-23
forum: General Help
---

### Post by serpantman on 2009-08-23
I just noticed that even while idle, 50% or more of my cycles are being used. I am not noticing any slow down though. I have pidgin, compiz, truecrypt, nautalius, audio player(not playing anything though), firefox, and a terminal open. oh and gkrellm. These shouldnt be using CPU cycles when im not using them though?

K, now i just closed half that stuff and im using about 60% of my cycles per second on average? What are these cycles doing?

EDIT: I'm looking in system monitor but i cant see what using them all

Solved.
Restart took care of it, i should have ran some ps commands. I would like to have known what was going on.

---

### Post by XCan on 2009-08-23
System monitor by itself is a serious resource hog. I recommend you type ```
 top 
``` in a terminal to find out what is leeching the cycles. There is an alternative called htop as well, but top should suffice for now.

---

### Post by dumblebee100 on 2009-08-26
> **XCan said:**
> System monitor by itself is a serious resource hog. I recommend you type ```
 top 
``` in a terminal to find out what is leeching the cycles. There is an alternative called htop as well, but top should suffice for now.

I too observed it ..

on my jaunty which is stable 

my system monitor took around 25 % of resource ..

and on my karmic alpha 4 
it uses nearly 70% of cpu ...so now I dont even open it ..

till jaunty I know about ps command but I know max things about it ....because Im lately using only ps command for day today work ....

cant touch system monitor at present ..till bugs are fixed

---

