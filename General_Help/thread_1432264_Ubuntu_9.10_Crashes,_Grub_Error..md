---
title: "Ubuntu 9.10 Crashes, Grub Error."
date: 2010-03-17
forum: General Help
---

### Post by futureismo on 2010-03-17
Hi there,

My desktop has been running 64 bit 9.10 since an upgrade from 9.04 for 6 months with no problems.

Recently however, my system crashed for the first time. All windows closed and the system hung, attempting to open anything did not work. I would click on an icon or type Alt +F2 and nothing happened . Although my cairo-dock at the bottom of the screen was still running perfectly (including animations Etc.) albeit without any programs working. Trying to click on system manager gave me the message.

"Failed to execute child process 'gnome-system-manager' Input/Output Error"

Trying to reboot several times and selecting previous kernels brought me to a prompt where I was able to check all my important documents were still there, but do nothing else. Recovery mode also did not work.

Eventually I left the computer overnight and started it and Ubuntu loaded normally, then after around 15 minutes the system hung again with identical systems to the first time. Although this time Firefox greyed out first.

This has happened every time I try to boot the computer since and last time it gave me a screen saying Grub Read Error which after 3 reboots has finally allowed me to access my computer (from where I am typing with haste!).

Using lm-sensors I am sure there is not an over heating problem. Am I right in thinking this may be a problem with my hard drive? And if so what is my best course of action? Apologies for the length of this post and thanks for reading.

---

### Post by blueridgedog on 2010-03-17
Are errors reported on your hard drive?  system - administration - disk utility, select your drive on the left, then "more information" on the right.  Any errors?

I too suspect your hard drive, your hard drive controller, the cable or your system memory.  I suggest you boot off of a LiveCD and report any issues you have.  It will either confirm that the problems persist and point to memory or controller issues or that they do not, which points to a hard disk.

---

### Post by futureismo on 2010-03-19
Thanks for the reply.

The problem seems to have miraculously disappeared as yesterday I had over 5 hours of uptime before I switched the computer off. 

I checked the disk utility and there don't seem to be any problems and managed to boot into a LiveCD successfully, which ran fine as well. I also checked all the connections within my case and everything seemed fine (I did this after the 5 hour uptime). 

I won't mark the thread as solved just yet in case the problem returns next boot.

---

### Post by futureismo on 2010-03-19
The problem has not returned with a current uptime of 4h 11m. I presume the problem was a physical one of a cable which had become dislodged and has now moved back into place. Otherwise I have no idea. I will mark the thread solved.

Thanks for your help blueridgedog.

---

