---
title: "help - cloning bootable hard disk"
date: 2011-02-21
forum: General Help
---

### Post by craig.brisbane on 2011-02-21
Recently my had disk crashed. It has taken me over a day to install and setup the drive - time I can't really afford. 

I'd like to know how I can clone a second as a bootable copy of the main hard drive and update from time to time. Therefore if the main hd fails again, I can simple boot from the second drive.

How can I do this? I have two sata drives in the box, running 10.10 desktop.

Tks 
Craig

---

### Post by aeiah on 2011-02-21
you could do it with dd, clonezilla, or even rsync. if you purely want to protect against hard drive failures, you could just put the two drives into a raid array, so the data is mirrored across both drives. you wouldnt have to worry about updating the backup drive then, but it also means that if you break your system through misconfiguration, it'll be broken on both drives :p

if you want to take the manual approach, and give yourself a little protection against misconfiguration or accidental deletion, then go for clonezilla

---

