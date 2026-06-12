---
title: "Blank CDs read with 0 bytes memory"
date: 2010-01-14
forum: General Help
---

### Post by Keaton_Brown on 2010-01-14
I really need some help here. Every single blank CD i put into my computer show it has 0 bytes of memory and i cannot write things onto them. I dual boot 9.10 and Windows XP, and Windows reads them just fine. Ubuntu will mount the disk as "Blank CD-R Disc, i can access it, and everything works except when i look at the properties it says there are 0 bytes used and 0 bytes free. The drive reads discs with data on them just fine, and they work flawlessly, its just blank discs that dont work. 
What i need to know is if there some property i need to change or a line i need to put in the terminal to make it read blank discs? Or am i completely screwed?

---

### Post by michy99 on 2010-01-14
Maybe it just shows it as 0 because there isn't anything on it yet. Have you tried burning anything to it?

---

### Post by ajgreeny on 2010-01-14
> when i look at the properties it says there are 0 bytes used and 0 bytes free.That's because there are no bytes free as far as the system is concerned, ie there is no free space on which you can just drop files like a hard disk.  The only way you can see if the disks are OK is to try to write to one using brasero, or whatever disk burner software you use.

I have no idea what windows says in the same situation regarding blank disks, but I suspect it is the same.  I no longer run windows so can't say for certain.

---

### Post by osmorphyus on 2010-01-14
i agree.  the problem here sounds to be the user is expecting an XP related popup box for when he inserts his blank media.

so far, the system is acting as it should.  write to the disc then ask questions if there is a problem after that.

> [i]...Ubuntu will mount the disk as "Blank CD-R Disc, i can access it, and everything works...

[/i]

so exactly where is the problem?

---

### Post by Keaton_Brown on 2010-01-16
I shouldve been more clear. im not waiting for the xp box. i know there isnt one. the problem i have is with 9.04 i put a blank disk in and rythmnbox recognized it. i could write things to them. but with 9.10 it doesnt recognize them. the disk pops up in the media but i cannot write anything to it because it has no memory. ive tried brazero but it doesnt work. and if i drop files from the desktop into the disk folder it says something like "cannot be written. not enough memory". id check but im not using my desktop right now. the problem is- it finds the disks, but nothing can be written to them because it has 0 bytes memory.

---

### Post by withaar on 2010-12-16
I have the same problem. My hardware is an external, USB attached device. It is recognized fine and I can make audio CDs fine. I have been on linux since the mid 90's, so that excludes the XP pebkac. Tisk - language.

There is a bug trace:

[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/675387](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/675387)

---

