---
title: "BIOS problem with IDE and SATA Configuration"
date: 2006-05-06
forum: General Help
---

### Post by youthcyber on 2006-05-06
Dear Ubuntu Friends,

I have encountered two problems with the OS of Ubuntu. First of all, when I set the BIOS of the CD-RW drive to Fourth Master instead of 1st or 2nd Master the Ubuntu operating system cannot detect the drive. But if I change it to either 1st or 2nd Master, Ubuntu operating system is working fine; detecting the disc and loading the operating system perfectly.

Second problem encountered, the operating system cannot detect my S-ATA HDD. How can I configure it in order for the operating system to detect my hard disk?

Can Ubuntu operating system able to detect S-ATA HDD?

---

### Post by physcsdrk on 2006-05-06
I have PATA drives and SATA drives and it detected all of them.  For windows to see my drives I had to load a driver but ubuntu picked them right up.  So yes, it can detect SATA drives.  Beyond that, I don't know.

---

### Post by youthcyber on 2006-05-06
[QUOTE=physcsdrk]I have PATA drives and SATA drives and it detected all of them.  For windows to see my drives I had to load a driver but ubuntu picked them right up.  So yes, it can detect SATA drives.  Beyond that, I don't know.[/QUOTE]
In your BIOS you stated Legacy Mode or Native Mode?

---

### Post by rvergara on 2006-05-06
Yes, Ubuntu recognizes sata hard disks, it creates those devivices as sda1, sda2, etc.

Ramiro

---

### Post by youthcyber on 2006-05-07
For your BIOS your CD-ROM is detect under which Master?

For mine, My CD-ROM is detected under the fourth Master and I release Ubuntu can't detect my CD-ROM unless I change to either 1st or 2nd Master.

1st Master: SATA HDD
1st Slave: Nothing installed
2nd Master: Nothing installed
2nd Slave: Nothing installed
3rd Master: PATA HDD
3rd Slave: PATA HDD
4th Master: CD-ROM
4th Slave: Nothing installed

Help! :p

---

