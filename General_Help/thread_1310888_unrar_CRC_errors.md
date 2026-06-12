---
title: "unrar CRC errors?"
date: 2009-11-02
forum: General Help
---

### Post by Braveheart1980 on 2009-11-02
I have just fully upgraded to 9.10
Everything went fine except this : unrar

The problem i am facing is with the current version of unrar 

I installed unrar fine (sudo apt-get install unrar) to version UNRAR 3.90 beta 2 freeware

But when I try to unrar a set of files I ALWAYS get a CRC error , which in the end fails the whole process

BUT if I unrat the same files from withinh WinXP with WinRAR I get NO error and the archive is extracted correctly!!

Any workarounds/ideas?

PS This is happening to MANY archives,not just one.

---

### Post by phoenix116 on 2009-12-08
I am having the same problem here(x86_64 karmic)
This bug concerns only very big .rar archives(I had it with 8GB+)

It appears in both unrar and p7z with .rar module,
I personally think its somewhat 64 bit related, has anyone had this bug on 32 bits?

It is somewhat annoying because it extract successfully, but if you always use -kb (keep broken), it at least doesnt delete your files ;)

---

### Post by gyurka on 2009-12-27
I have the similar problem. unrar and unrar-nonfree somtimes work sometimes don't. I tested it on a DVD film packed into several parts (89 RAR file) containing only one DVD ISO file. The following worked:

$ unrar-free e -kb ./the_hangover.rar

Note that it always prints the following message:

the_hangover.iso : packed data CRC failed in volume the_hangover.r00
the_hangover.iso : packed data CRC failed in volume the_hangover.r01
the_hangover.iso : packed data CRC failed in volume the_hangover.r02
...
the_hangover.iso : packed data CRC failed in volume the_hangover.r88


furthermore, unrar-nonfree does not work at all on my computer. I am using Ubuntu 9.10 Karmic Koala

---

### Post by killfiend on 2010-04-18
Think I am having a similar problem in Debian Lenny x86_64. unrar v 0.0.1 but I don't have the -kb option. Has anyone found a fix?

---

### Post by Ozdemon on 2010-04-18
I also had this problem on 64-bit.  Switched to 32-bit, same problem.  Could it be related to nautilus or Gnome?

I will try the cli when I get home to see if that also has errors.

[Edit] Yep, have this error on Ubuntu 9.10 and Archlinux, including cli.

---

### Post by DarkPhoenix7878 on 2010-05-07
same issue with 10.04 on 64 bit >.>...

---

### Post by Ozdemon on 2010-05-07
I was finally able to diagnose my problem.  It was faulty RAM, specifically G-SKILL F3-12800CL9D-4GBNQ.

It is presently in for refund/replacement.  As to how weird this memory is see [http://gskill.us/forum/showthread.php?t=4952]("http://gskill.us/forum/showthread.php?t=4952")

Bottom line, if you are getting crc errors, it is probably a hardware issue - memory, HDD, motherboard, etc.

---

### Post by intel352 on 2010-10-09
I'm running Linux Mint 9 (Ubuntu 10.04), using unrar interface returns a CRC error for every archive in a set, yet the file always extracts out perfectly fine.

I don't believe this is an issue with faulty components. Sure, maybe sometimes, but when I use Windows 7 on this same hardware the day before to extract large archive sets, and then switch to Ubuntu to do the same, Ubuntu is what returns the errors on a file that has no issues.

---

