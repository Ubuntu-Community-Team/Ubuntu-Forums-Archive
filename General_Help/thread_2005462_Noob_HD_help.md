---
title: "Noob HD help"
date: 2012-06-17
forum: General Help
---

### Post by illinraja on 2012-06-17
I am a noob and not a programmer.  I have been using Ubuntu for about 4-5 months.  Really just use it to surf the internet.  

I was watching a dvd and closed my laptop lid. came back to it a half hour later.  Started the dvd over again and it played for about 5 minutes then my computer froze.  Tried everything to turn it off nothing worked.  I popped out my battery and when i started up again I got an error.

PXE-E61: Media Test Failure, Check Cable
PXE-MOF: Exiting INTEL boot agent

Checked my boot sequence and it was correct as network was 7th, cdrom 1st, usb 2nd, etc.

I used the liveCd to recover however I was near by hard drive's storage limit, I thought I had more but It did not have the 4.4gb or whatever free.  so i couldn't install the os again.  i tried to use gparted to delete partitions but nothing was found.

So, i figured I use a windows cd to erase the hard drive.  but i tried to do this and no partition will come up again.  i used the boot repair cd and i got this

[http://paste.ubuntu.com/1045027/](http://paste.ubuntu.com/1045027/)

so i guess that the hard drive isn't being read.  but i have no idea on how to fix this.  i really don't want to have to buy a new one.

---

### Post by Cheesemill on 2012-06-17
It seems like your computer can't see the drive at all anymore, you could well have a dead hard disk.

Can you see your drive when booted from a Live CD?

---

### Post by illinraja on 2012-06-17
no, well i use disk usuage and only 1.4 gb's come up.
using gparted nothing at all comes up.

---

### Post by Mopar1973Man on 2012-06-17
How about checking in BIOS to be sure the drive is being reported properly. I would start there then move forward to the OS (Ubuntu).

---

### Post by illinraja on 2012-06-17
how do i do that?

---

