---
title: "wandering in the desert"
date: 2011-08-29
forum: General Help
---

### Post by faz67 on 2011-08-29
Hello All
I installed an old Windows hard drive as second sata it is not recognized anywhere.
File system viewer does not report it. fsck does not report it. How can I mount this
drive if I can't get information on it Also there is no etc/fstab in my file system?
The old drive has some pictures on it I would like to recover.
The drive is sata but my power supply did not have sata power connector
so I used the regular 4 pin power connector since the drive had a port.
I am a novice with ubuntu.

Any help appreciated
faz67

---

### Post by Wayne_V on 2011-08-29
so does the drive show up in the BIOS?

---

### Post by faz67 on 2011-08-29
Thanks for the quick reply

Both drives show up in the BIOS listing
HDD 1:   3M-WDC WDC2500AAKS-00VSA0
HDD 2:   4M-WDC WD3200KS-00PFB0

Do you know if the fstab has been moved from /etc?

faz67

---

### Post by Wayne_V on 2011-08-29
/etc/fstab should still exists.  What is the output of the following:

$ df -k
$ sudo fdisk -l /dev/sda
$ sudo fdisk -l /dev/sdb
$ dmesg | grep sd[abcd]

---

### Post by dino99 on 2011-08-29
have had some hard time with sata drives on a motherboard due to crappy chipset on it. So the first thing to do is reading again the MB doc: on which sata order the devices need to be plugged.
Into the bios, try either: ide, ahci, compatible
On the sata hdd should not find jumper, but ?

the fstab: set it minimal: boot partition & swap, nothing else, mountall deals on demand then.

---

### Post by ninjaaron on 2011-08-29
to get information about your drives, try:

```
sudo blkid
```

---

### Post by faz67 on 2011-08-29
I have attached a screen shot of the results of the sudo commands!

---

### Post by faz67 on 2011-08-29
Still not sure what is going on???
Now my pictures show up in the file viewer but they show up in a file folder
named after the computer I removed the drive from? I have to do some 
errands no but will check back later.
Please stay tuned to this station.
faz67

---

### Post by faz67 on 2011-08-29
Well Thanks All
Problem Solved
I'm assuming that the fdisk command fixed the problem anyway I can see my pictures now and now all I need to do is figure out is.
1. How to burn them to cd's?
Is there an Ubntu utility I can use or do I have to download something 
2. How do I mark this solved?

Thanks Again
Gary:P

---

### Post by ninjaaron on 2011-08-29
> **faz67 said:**
> Well Thanks All
Problem Solved
I'm assuming that the fdisk command fixed the problem anyway I can see my pictures now and now all I need to do is figure out is.
1. How to burn them to cd's?
Is there an Ubntu utility I can use or do I have to download something 
2. How do I mark this solved?

Thanks Again
Gary:P

There is a CD burning program packaged with a default Ubuntu called Brasero.  It's pretty self-explanatory once you get it started.

To mark the thread as solved, go to the "thread tools" near the top of the page.

Strong work. ;)

---

