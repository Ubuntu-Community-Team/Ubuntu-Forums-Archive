---
title: "CD won't eject via button"
date: 2009-12-15
forum: General Help
---

### Post by jt_04 on 2009-12-15
When I press the CD eject button on the drive, nothing happens.  I have to type "eject" at the command line to make the drive open.  This is a huge pain on my htpc because I have to walk all the way back to my couch to get my keyboard.   :frown:

I search briefly and saw that there were some bug reports for this but didn't see any fixes.  anyone know of a fix?

---

### Post by Johnny B on 2009-12-15
this sounds like a hardware problem to me, try another drive

---

### Post by jflaker on 2009-12-15
APPLICATIONS>ACCESSORIES>TERMINAL

type 

sudo eject

likely that YOU didn't insert the disk so YOU can't eject it.

---

### Post by Cityscape on 2009-12-15
I've had the same problem. What i found is the you have to right-click the cd/dvd icon on your desktop then click eject.

---

### Post by jt_04 on 2009-12-16
The hardware button works when I boot into windows, so it's definitely not a hardware issue.

yes, i can eject from the command line.  I don't even need to use sudo.  _But that's not the point!_  

The point is, in windows I can use the button to open the drive, insert & play a dvd, then press the button again to open & extract the disc.  

In ubuntu, i can use the button to open the _empty_ drive and insert the dvd, but then the drive becomes **LOCKED** and the ONLY way to open the drive is via software.  this is plain unacceptable in my opinion.

ideas?  this only started after the recent karmic & kernel upgrades.  jaunty worked fine.

---

### Post by uniden9 on 2009-12-16
It will not let you eject a mounted drive.  Some automounter is running and this is preventing you from ejecting.  You can hard prevent the locking if you want.  

edit the /etc/sysctl.conf with your editor of choice
Append the following line:
dev.cdrom.lock = 0

Then for it to take effect,
$sudo sysctl -p 
Or reboot.

The prevents the locking of the drive at the kernel level.

---

### Post by sophicsage on 2009-12-16
> **jt_04 said:**
> When I press the CD eject button on the drive, nothing happens.  I have to type "eject" at the command line to make the drive open.  This is a huge pain on my htpc because I have to walk all the way back to my couch to get my keyboard.   :frown:

I search briefly and saw that there were some bug reports for this but didn't see any fixes.  anyone know of a fix?

I have another linux based program I use for work.  It also doesn't let you use the eject button itself, but rather ejects when IT'S ready from within the program.  That's one difference I've heard is very common with Linux.  Linux basically sees a drive differently from Windows.  I have the same issue as you, but I just open up the CD playing program and click eject and it opens.  Works fine for me...and I'm probably wearing out the parts less by letting the computer do the work when it's ready.  This is really a non issue for me.

---

### Post by jt_04 on 2009-12-17
> **uniden9 said:**
> edit the /etc/sysctl.conf with your editor of choice
Append the following line:
dev.cdrom.lock = 0

Then for it to take effect,
reboot.


This fixed the problem for me!  thank you very much, this is exactly what i was looking for.

---

### Post by jt_04 on 2009-12-17
> **sophicsage said:**
> Linux basically sees a drive differently from Windows.  I have the same issue as you, but I just open up the CD playing program and click eject and it opens.  Works fine for me... This is really a non issue for me.

I understand this, and I probably would get used to software ejecting over time.  

i'm glad it's a non-issue for you, but it really is a big issue for me.  when i'm gone and my wife or house guests try to play a dvd on my htpc, they expect to hit the button and get the disc back.  when nothing happens, "the computer's broken" and they have no idea how to get it out.  They are not well versed in the intricacies of how linux treats a mounted CD, and honestly, they shouldn't have to be...they should be able to punch the button and get their disc back no matter what.

---

### Post by BoxOfSnoo on 2009-12-25
Thanks for posting the solution (which worked for me too), and I strongly agree with jt_04 here... it's definitely a problem, especially for a set top box, where you don't have a mouse or a keyboard at hand.

---

### Post by jaygo on 2010-01-16
slick solution! I agree with the latter two posts ... the default setting breaks the intended function of the eject button. I don't see a reason why the physical eject button shouldn't trigger the same events that clicking an unmount icon in the GUI does ... but I don't code linux either. And Linux & I have disagreed many times about a user with physical access to the PC deserving read/write/mount/unmount access to the disks sitting in front of them.

---

