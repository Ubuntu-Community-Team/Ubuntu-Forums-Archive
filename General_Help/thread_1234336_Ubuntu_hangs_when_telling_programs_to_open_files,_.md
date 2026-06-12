---
title: "Ubuntu hangs when telling programs to open files, or when saving files."
date: 2009-08-07
forum: General Help
---

### Post by bluekage on 2009-08-07
So, I encountered this problem last night right before going to bed. I was surfing the tubes and I had quite a few tabs up in Firefox, when suddenly  firefox started to hang whenever I tried to save a page, or image. At first I thought it was Firefox itself, but I've noticed that it does the same thing whenever I tell a program, gimp for example, to either open or save a file, the program that initiates the action will always hang for about 15-30 seconds.

My issue seems to lie somewhere within the file browsing window itself, does anyone know what might cause this and how I can go about fixing it?

Many thanks in adavance.

---

### Post by ubudog on 2009-08-07
It looks like somethings wrong with nautilus(the file manager).  Have you rebooted?

---

### Post by knuthf on 2009-08-07
Yes - when you reboot, it removes the problem. It is not related to Firefox - but a general Ubuntu bug.

My guess is that it is a file system semaphore that looses a signal. There are some programmers that do not trust signals - because they do not know how to code a trap, and never bothered to learn it. The result is that you find a pile of processes hanging in "do_poll". 
If you "poll" (check every 1/10 of a second) - you use a lot of CPU. In particular, if you poll a device that has responded a long time ago - far down in the file system. So, then it is first when some code at a higher level triggers everything to wake up. 
You use a lot of file system resources - in particular in X/Windows management - its all "sockets" and uses standard file operations if set up correct. 

The system degradation is notable and consistent. The simple answer is just to reboot. Now I doubt anyone has the resources to debugg the system until there is a commercial requiremewnt to rid the system of the performance bug. 
-K :-)

---

### Post by bluekage on 2009-08-08
Thanks for the replies guys, and sorry it took me so long to get back to this, but rebooting was the first thing I tried. Unfortunately it doesn't seem to help.

---

