---
title: "Write to disc trouble...???"
date: 2009-12-27
forum: General Help
---

### Post by robertcoulson on 2009-12-27
Hi
I right mouse clicked on Ubuntu 10.04 ISO to write to a CD.....I am using 700meg CD's....It says I do not have enough space...Doesn't seem right....Please see attachment.
Bob

---

### Post by switch10 on 2009-12-27
Its not seeing your blank disk at all.  wait for the blank cd to show up on your desktop.  It should take about 5-10 seconds...

---

### Post by robertcoulson on 2009-12-27
Well, I tried that, but my CD did not show up on my desktop or anywhere else...I took the CD out and replaced it with another one and for a split second it said, I didn't have enough disc space...Got me confused (brand new CD's)...Is there a good ISO burning program to download...???
Bob

---

### Post by switch10 on 2009-12-27
> **robertcoulson said:**
> Well, I tried that, but my CD did not show up on my desktop or anywhere else...I took the CD out and replaced it with another one and for a split second it said, I didn't have enough disc space...Got me confused (brand new CD's)...Is there a good ISO burning program to download...???
Bob

Have you burned CD's before with Ubuntu?  I have a feeling the OS is not seeing the drive...

---

### Post by robertcoulson on 2009-12-27
You are correct...I can't see the CD drive...No, have not burned any CD's with Ubuntu....Is that going to be a problem...???
Bob

---

### Post by switch10 on 2009-12-27
is it a usb cd drive, or an internal one?  laptop or desktop?

---

### Post by robertcoulson on 2009-12-27
It is an internal drive on my desktop...I can always go to XP (dual boot) and write the ISO there, but I still won't be able to see my CD drive in Ubuntu.
Bob

---

### Post by switch10 on 2009-12-27
this is odd because the drive would have had to work to install ubuntu in the first place.  (unless you installed from a flash drive...)

try running this:
```
sudo fdisk -l
```

do you see anything that looks like it is a cd drive??  If so put in a cd and do this:

```
mount
```

hopefully your system will see the drive

---

### Post by robertcoulson on 2009-12-27
Well, tried that and when I do NOT have a CD in the drive and go to computer, I see attachment 2 (can see drive)...But as soon as I put the CD in the drive the CD icon disappears attachment 3 ...Strange.
Bob

---

### Post by robertcoulson on 2009-12-27
Well...Thanks for trying to help...I will just go to XP to burn CD's...No big deal...Thanks again.
Bob

---

### Post by robertcoulson on 2009-12-27
I can see the CD drive under "computer", but I can not click on it.....See attachment, maybe this is the problem...???
Bob

---

### Post by robertcoulson on 2009-12-27
Hi switch10
WOW...My mistake...I forgot to place the CD in the drive and type "mount" in the terminal window.....It now works....!!!!!

Thanks again switch10
Bob

---

