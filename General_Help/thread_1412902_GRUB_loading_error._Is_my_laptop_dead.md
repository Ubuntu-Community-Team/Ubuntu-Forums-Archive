---
title: "GRUB loading error. Is my laptop dead?"
date: 2010-02-21
forum: General Help
---

### Post by Lobo89 on 2010-02-21
Hi, I'm pretty new to Ubuntu and Linux in general so please bear with me. 

I have a Dell Inspiron 1545 with windows 7 and ubuntu 9.10 dual boot. I been running both OS's for a few months now with no major problems besides wireless internet issues. 

Today, however, as I go to boot my laptop up, the Dell logo loads with the F2 and F12 boot and setup options which both work. Directly after that though I get the message "GRUB loading. Symbol '?' not found. Aborted. Press any key to Exit." then it repeats when I push a key, and then it tells me to press F1 to retry, F2 to go to setup, or F5 to run diagnostics. It passes all the tests in diagnostics. I've tried booting off of the ubuntu cd I used to load it initially with no luck. 

So I'm stuck at either that error message or in setup but I can't go any further, and it does not change anything when I tried to boot from the cd. Is there any hope for my laptop?

---

### Post by x33a on 2010-02-21
Do you have another live cd at hand. If you have access to another computer, download and burn puppy linux, try that with your laptop and see if it is able to boot.

Also you can give supergrubdisc a try, and see if it manages to fix grub.

---

### Post by Lobo89 on 2010-02-22
Ok so I burned a new Ubuntu CD and I can boot it up now, but I'm not sure where to go from here as far as solving the problem. 

With the Super Grub Disk, it looks like it might be able to solve my problem but I don't really know anything about it and I don't see my specific problem on any of their walk-throughs.

Any more suggestions?

---

### Post by jenaniston on 2010-02-22
> **Barack Obama said:**
> Hi, I'm pretty new to Ubuntu and Linux in general so please bear with me. 

. . . Is there any hope for my laptop?

. . . Any more suggestions?


OK Mr. President . . .

I wouldn't give up on the laptop . . .
if you can boot from the CD drive or USB you will be fine.
 
First, I'd recommend using a "live" iso version for troubleshooting using linux . . .
a USB with some overlay (extra space) that can save changes would be great . . .
 2GB or better but even a 1 GB U9.04 Live USB works well (what I'm using now on a campus computer btw)
 a live CD would be fine though.

I'd recommend 9.04 Live rather than the grub2 bootloader with U9.10 as easier for novices.

Those live versions won't install anything - until you later want to run the "Install to Hard Drive"-
and in Ubuntu 9.04 and others you can use the live CD to even ***create*** the USB live operating system.

Good luck.

---

### Post by x33a on 2010-02-22
Well if you can boot with the live cd, then it means your laptop isn't dead :popcorn:

Now, first you should try to reinstall grub.

give this a try:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

or try supergrubdisc.

---

### Post by Lobo89 on 2010-02-22
Thanks for everyone's help. So just to be sure before I get started, what jen is suggesting is that I just install a different distribution over the ubuntu partition I have now? And this should allow me to access the new distribution and windows 7 like a normal dual boot, without needing a CD or thumb-drive every time, right?

---

### Post by Lobo89 on 2010-02-22
> **x33a said:**
> Well if you can boot with the live cd, then it means your laptop isn't dead :popcorn:

Now, first you should try to reinstall grub.

give this a try:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

or try supergrubdisc.


Ok, I will give this a try first.

---

### Post by Lobo89 on 2010-02-22
Success! I redid GRUB2 and everything is working great now. Thank you all so much for your help.

---

### Post by x33a on 2010-02-22
Congrats and please mark the thread as solved.

---

