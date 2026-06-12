---
title: "update hosed system :("
date: 2010-02-07
forum: General Help
---

### Post by koalaJason on 2010-02-07
So this morning I get some forced learning. :-)

details :

Ive been using ubuntu for about a month. I had it set to log me in automatically on startup (not as root but as user jason). It never asked me for my password on logging in.

This morning I start up the computer and I get the ubuntu splash screen with a box with a list of users in it. Nothing i put in works : ubuntu/ubuntu or jason/********** or leaving it blank.

Mystery 2) Prior to this behavior (and again, only this morning) I got a "ubuntu is running in low-graphics mode" error. A list of radio buttons were offered, and I have followed each as far as they will go, to no avail. I believe it has something to do with the nvidia drivers.

I have also held down shift while booting and I have a few options there I am still exploring.

I can get to a shell prompt but am no guru on fixing things from there. Interestingly, the username / pass for jason/********** works there.

Ideas?

---

### Post by koalaJason on 2010-02-07
SOLVED

sudo /etc/X11/X

how... why... I have no clue.

What prompted me to try that? Researching x windows system, looking at /etc/X11/xorg.conf and seeing X in that folder, then running it out of curiosity and restarting when the screen just turned black.



/scared to restart now

---

### Post by rnerwein on 2010-02-07
> **koalaJason said:**
> SOLVED

sudo /etc/X11/X

how... why... I have no clue.

What prompted me to try that? Researching x windows system, looking at /etc/X11/xorg.conf and seeing X in that folder, then running it out of curiosity and restarting when the screen just turned black.



/scared to restart now

hi
how... why... I have no clue. --> it's a link to /usr/bin/Xorg
Xorg is a X11R7 X server  runs on a wider range of hardware and OS platforms.

where it comes from -> i guess you have updated your system ( auto mode ? ) and there is your nvidia driver gone.
ciao

---

