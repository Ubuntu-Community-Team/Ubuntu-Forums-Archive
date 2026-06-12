---
title: "Fullscreen goes black or crashes app in Lucid"
date: 2010-05-19
forum: General Help
---

### Post by offrampextreme on 2010-05-19
Hi,
i've had this issue ever since i installed Lucid on the day it came out.
Whenever i maximize the view on both VLC or MoviePlayer, the applications crash. When i maximize Nautilus, it gives me a black screen. It doesn't even happen all the time (sometimes maximizing VLC will give me audio, but a black screen).
I helped myself with disabling compiz by entering "metacity --replace", but i sure want compiz on.
Anybody know what causes this and how i can get rid of the pronlem?
Thanks.

---

### Post by dino99 on 2010-05-19
the first places to get info are the logs:

into /home : .xsession-errors, unhide it into menu to see it

into system admin log viewer: mostly into xorg.0.log, syslog & userlog

but you need to check if your video driver is activated: system admin hardware driver

what is your graphic card and which video driver is installed ?

---

### Post by offrampextreme on 2010-05-20
First off: Thanks for the reply, dino. I had a Nvidia 7600GT installed and switched to an old 6600GT i had just to rule anything hardware-related out. I had no idea whether this was even possible, but i thought it couldn't hurt.
I have the current and recommended driver installed and activated. I tried the others too, but it wouldn't change anything.
I checked the logs (and as i maximized the log file viewer it happened again), but i didn't see anything screaming ERROR. I will check those and the .xsession-errors file again this weekend when i got more time.
Any hints what i am looking for in the files?

---

