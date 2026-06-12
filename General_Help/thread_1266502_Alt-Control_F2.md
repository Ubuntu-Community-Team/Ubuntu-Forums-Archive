---
title: "Alt-Control F2?"
date: 2009-09-14
forum: General Help
---

### Post by rmcellig on 2009-09-14
I accidentally pressed this key combination and I found myself at a command line and couldn't get out of it. I restarted the machine and everything is fine now. What does that key combination do and how do I get out of it so that I am back to my normal desktop?

---

### Post by Vaphell on 2009-09-14
ALT+CTRL+F7

ALT-CTRL-Fx switches to another terminal session, by default GUI is at tty7

it's pretty useful when GUI freezes - just switch to another tty, log in and kill that rogue process.

---

### Post by denver on 2009-09-14
In most linux distributions you have 7 tty's (tele type terminals). 1-6 are all command line terminals, and 7 is the graphical Xorg interface (Gnome on ubuntu). As Vaphell already mentioned, pressing Ctrl+Alt+F7 brings back the graphical user interface.

---

### Post by rmcellig on 2009-09-14
Thanks for the explanation denver. I am new to all this so now I have a better understanding. Much appreciated!!

---

### Post by stderr on 2009-09-14
What you stumbled on is a great way to recover a system when you're having problems. For example, on occasion an application goes wrong and you may be left with a semi-frozen system (more common in 3D games). 80% of the time, you can still switch to another tty with the likes of Ctrl+Alt+F2 etc, from which you can login and kill the offending application.

You can have a little play around if you like: entering

```
top
```

(then enter) will give you a list of processes running, sorted by CPU usage. So if an application is chewing CPU (hence rendering your GUI largely unusable), that'll be at the top of the list.

```
ace@ace1:~$ top

top - 23:23:08 up 1 day,  3:55,  6 users,  load average: 0.05, 0.17, 0.12
Tasks: 173 total,   1 running, 172 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.4%us,  1.5%sy,  0.1%ni, 84.3%id,  1.5%wa,  0.1%hi,  0.1%si,  0.0%st
Mem:   3630680k total,  3067960k used,   562720k free,    71736k buffers
Swap:  6835616k total,     5392k used,  6830224k free,  2118820k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
** 2865 ace       20   0  173m  66m  21m S   97  1.9   4:59.64 rhythmbox          **
 5296 boinc     20   0 14700  11m 3016 S    2  0.3   2:50.66 boinc      

etc...

```

If you press q, you exit top. So you'll notice in my example rhythmbox is using 97% of the CPU... to "kill" rhythmbox, there aare many ways, but one would be to note the PID (Process ID) number beside it (2865 in this case), and then type:

```
kill 2865
```

You can then switch back to your graphical tty with Ctrl+Alt+F7 to see if it worked. If it didn't, you can switch back and try a far more aggressive approach with

```
sudo kill -9 2865
```

You could also do things like

```
killall rhythmbox
```

or

```
kill $(pidof rhythmbox) 
```

Anyway, just giving you a few (hopefully useful) ideas :) Such is the likes of Ubuntu - you can delve into the innards of Linux or remain in the relative comfort of a Windows-like graphical environment - it's up to you!

---

### Post by rmcellig on 2009-09-14
One thing I love about this forum for the most part is the way I am blown away by the answers. Thanks stderr for a great explanation. Being a heavy Mac user I prefer staying in the GUI but know that with Ubuntu there are all of these options, it's nice to know. I guess the same could be said about Mac OS 10.6. Thanks again!

---

