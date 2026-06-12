---
title: "how to copy one hdd onto another?"
date: 2010-12-07
forum: General Help
---

### Post by Paco62 on 2010-12-07
My comp has two hard drives: 1: 300gb, 10,000rpm  2: 500gb, 7200 rpm. (Both drives are SATA).  First drive is loaded with 10.04 and has many programs installed, tweaks and settings made etc.  Second drive has 10.10, but no changes or progs installed.  I want to wipe clean the second drive and copy the entire contents of first drive onto it.  This will save me the trouble of doing a clean install of 10.04 on the second drive and then having to install programs , change settings etc.  Is there a program available that will let me do this, so that I won't have to make any changes to second drive after the first drive has been copied to, ie I won't even have to install grub?  Note that I am a novice with linux and not very good with computers generally, so the program should have an easy to use gui.  Thanks in advance.

---

### Post by sikander3786 on 2010-12-07
Use clonezilla and clone your disks.

[http://clonezilla.org](http://clonezilla.org)

---

### Post by timgood on 2010-12-07
Clonezilla is good but you may also find that ddrescue is your friend. Once you have copied over the contents of the smaller drive to the larger drive, boot from a live CD and resize the ubuntu partition. There is a lot of help available online for ddrescue, Google 'ddrescue help' and you'll find all you need.

---

