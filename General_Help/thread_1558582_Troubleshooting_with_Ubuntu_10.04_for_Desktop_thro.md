---
title: "Troubleshooting with Ubuntu 10.04 for Desktop through CDRom"
date: 2010-08-22
forum: General Help
---

### Post by ETL09 on 2010-08-22
I searched for this problem but I can't seem to find the solution in any of the past threads.

Every time I reboot my laptop with the CD inserted to install Ubuntu it starts off fine. I get the keyboard with the man in the circle. Soon after I get the Ubuntu Logo with five dots under but after that I get this message.


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) mount:mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

Can someone please help me.

---

### Post by ETL09 on 2010-08-22
Can someone please help?

---

### Post by grief -l on 2010-08-22
initramfs = initiate loading (a special) file system to RAM. It needs to do this to be able to probe your hardware so it knows which drivers to load and where to unpack the real file system. 

It sounds like your box doesn't have enough RAM available

Usually too little RAM brings up a message abt "Kernel Panic" so maybe you have enough RAM but your CD is corrupted?

---

### Post by ETL09 on 2010-08-22
Yes, it did say something about (Kernel Panic). In which case, what should I do?

---

### Post by grief -l on 2010-08-22
How much RAM do you actually have?

---

### Post by cogier on 2010-08-22
Can you answer grief -l's question regarding the amount of RAM you have. If it is at least 512mb I would reboot, hit enter when you see the "the keyboard with the man in the circle". Select English, then press F6 and select NOMODESET and then boot the computer and see if that helps.

Further help on this is available here [http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/]("http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/")

---

### Post by dougalkerr on 2010-08-22
Can you download and burn version 9.04 XUbuntu for example and try that.
It will run on lighter systems and should still give you a half-decent system to work with. I have it running on a computer that is five years old coz it can't take version 10.04 or even 9.10.

Just like Windows, Linux versions have their limits but, other lightweight versions can give you just as much speed to work with if you still have the applications that you want.

Good luck.

---

