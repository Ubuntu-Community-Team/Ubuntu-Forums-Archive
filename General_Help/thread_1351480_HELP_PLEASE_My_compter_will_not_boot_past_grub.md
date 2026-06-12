---
title: "HELP PLEASE My compter will not boot past grub"
date: 2009-12-10
forum: General Help
---

### Post by UmbrInKID on 2009-12-10
PLease any help is much appreciated! recently my computer has been hacving  problems with shutting down and i just ran some updates and restarted.. now my computer will not boot at all past grub..

Heres as much info as I can think may help

I am running Ubuntu 9.10 with the gnome desktop
My kernel was just upgraded to 2.6.31-16-generic
I am using 64bit ubuntu ver. on a AMD64 turion laptop

What other info will help in diagnosing this? I really cant lose all my info on my computer. I also tried just using a live disk and taking my documents off then reinstalling but I had encrypted my home folder so that attempt failed as well.\


Thanks in advance for any help

---

### Post by prem1er on 2009-12-10
Are there any errors on the screen when it tries to boot? Have you recently changed any grub configurations? What problems has 'your computer had shutting down' prior to this? Do you have a liveCD handy that you could boot off of to rule out any hardware issues?

---

### Post by kestrel1 on 2009-12-10
If you press ESC before grub continues to boot to get in to the grub menu you should see previous kernel versions. Are you able to boot any of them?

---

### Post by UmbrInKID on 2009-12-10
> **prem1er said:**
> Are there any errors on the screen when it tries to boot? Have you recently changed any grub configurations? What problems has 'your computer had shutting down' prior to this?
I have not changed any grub settings. Last thing done was auto updates in which im not sure what all was being updated for sure. In shutting down it just didnt. It would go to shut down, open a "x terminal" screen with my login (i never logged in) than quickly changed to some kill actions of different programs as if maybe closing them? than nothing. stayed on that screen with a blinking curser so I had to always shut it down manually. I hope this helps sorry Im not very educated with all the tech side of linux. eager to learn though so hopefully in the future i can better diag these problems myself.

---

### Post by UmbrInKID on 2009-12-10
> **kestrel1 said:**
> If you press ESC before grub continues to boot to get in to the grub menu you should see previous kernel versions. Are you able to boot any of them?

Unfortunately I had just cleaned up my computer as well so I do not have any other option for kernels except the current ver..

---

### Post by UmbrInKID on 2009-12-10
Oh and the only error (if its indeed an error) displays too quik to read before redirecting to a blank black screen. what i do catch is the word depressed?

---

### Post by cholericfun on 2009-12-10
not sure bout the shutting down part but *maybe* the update included something in relation to grub and changing the menu.lst file?
maybe have a look in there or even try and rewrite grub from the liveCD.

also have a look at encryption - i cant believe that *you* cannot get at your files. (no ideas on my part again...) and make a back-up of those before anything else if they are important to you (i.e. should have done that anyway...)

---

### Post by UmbrInKID on 2009-12-10
> **prem1er said:**
> Do you have a liveCD handy that you could boot off of to rule out any hardware issues?
I have an UE 2.5 64bit, ubuntu 9.10 64bit, and ubuntu 9.10 32bit

---

### Post by prem1er on 2009-12-10
> **prem1er said:**
> Do you have a liveCD handy that you could boot off of to rule out any hardware issues?

?

---

### Post by UmbrInKID on 2009-12-10
> **cholericfun said:**
> not sure bout the shutting down part but *maybe* the update included something in relation to grub and changing the menu.lst file?
maybe have a look in there or even try and rewrite grub from the liveCD
Not sure how to do this or what to even look for?

> **cholericfun said:**
> also have a look at encryption - i cant believe that *you* cannot get at your files. (no ideas on my part again...)
Some reason on the live all it says is I do not have permissions to access files.. no idea why either. I used to keep all files on an external hard drive but it fried up and haven't replaced it.. ugh. only way i knew how to bypass encryption was logging in using password at start up.. which I cant do..

---

### Post by UmbrInKID on 2009-12-10
> **prem1er said:**
> ?
yes

---

### Post by cholericfun on 2009-12-10
re encryption i just had a look myself and just found this
[http://ubuntuforums.org/showthread.php?t=708291](http://ubuntuforums.org/showthread.php?t=708291)

maybe start a new thread on the subject to draw more attention to this particular subject.


anyhow:

the usual game with grub errors:
from the LiveCD:
lets have a look at
```
sudo fdisk -l
```

and paste this file here as well:
```
 gedit /boot/grub/menu.lst
```

this way we should be able to see if theres something wrong with grubs menu.

---

