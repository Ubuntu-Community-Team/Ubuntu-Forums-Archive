---
title: "Terminal permissions"
date: 2009-07-07
forum: General Help
---

### Post by sshannin on 2009-07-07
I'm try to use my laptop running Ubuntu to act as a serial terminal for a Sun Enterprise server.  I'm having problems connecting and I was wondering if anybody could help me.  Here is what I've tried:

Since laptops for the past few years no longer come with serial ports, I'm using a 25-pin serial to USB cable.  Ubuntu correctly recognizes this and creates a device node at /dev/ttyUSB0.  This is where I start having problems.  I try opening the channel with 
```
sudo cu -l /dev/tty0 -s 9600
```and this is what I get:
```
cu: open (/dev/ttyUSB0): Permission denied
cu: /dev/ttyUSB0: Line in use
```I have checked for a lock file, and can't seem to find one.  Any suggestions?

---

### Post by bear24rw on 2009-07-07
shouldnt it create a /dev/ttyS0 or something like that?

---

### Post by sshannin on 2009-07-07
Hmm, I have a S0-S3, which are present regardless of whether or not the USB0 node is.  Is there a way to check if it's linking to any of them?

---

### Post by sshannin on 2009-07-08
Does anybody else have any suggestions?

Thanks.

---

