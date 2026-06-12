---
title: "Blank screen after force restart on 9.10 (help me please...)"
date: 2009-11-29
forum: General Help
---

### Post by Hyper Tails on 2009-11-29
Hi I run 7 and Kamatic and I was looking for a new wallpaper for my ubuntu desktop and It froze up on me and i had to restart the computer ( I'm aware that ctrl-alt-backspace restarts xserver but that didn't work)and I booted it back in the splash screen shows up but after its gone all i get is a blank screen and nothing happens, the hardrive isn't doing diddly crap and I tried the second one on the list and it does the same thing!

Please help, any help will be thanked

---

### Post by Hyper Tails on 2009-11-30
....................................................................................................................................................................................................................................

---

### Post by halovivek on 2009-11-30
Did you upgrade from ubuntu 9.04 to 9.10?
For mine also i got the same thing and i did a fresh install. can some one give the solution for the same?

---

### Post by Hyper Tails on 2009-11-30
I did a fresh install for 9.10

---

### Post by Snow986 on 2009-11-30
Did you try ssh'ing into it with another computer on the network?

---

### Post by Hyper Tails on 2009-11-30
no and no i don't have a network

---

### Post by Hyper Tails on 2009-12-01
any one?

---

### Post by doas777 on 2009-12-01
well, to shut it down gracefully, you can use the sysreq REISUB thing.

just hold down Alt + Printscrn and while holding, slowly type r e i s u b (no spaces).

Ctrl+Alt+Backspace no longer works for killing x, and if you do kill x (sudo killall gdm) then x just restarts.
the new method for killing x is 
```
sudo service gdm stop
``` or start, as the case may be.

as for your issue, I would start by dropping into vtty 1 (ctrl + alt + F1) and stopping X. then try to restart it from the tty, and it will hopefully give you error messages indicating the origin of the issue. 

you can also check your debug log with 
```
sudo dmesg | tail
``` right after a failure to see if it is logged.
the syslog and messages logs (both in /var/log) may be of help too.

---

