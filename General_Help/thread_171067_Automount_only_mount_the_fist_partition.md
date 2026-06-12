---
title: "Automount only mount the fist partition"
date: 2006-05-05
forum: General Help
---

### Post by Camulus on 2006-05-05
Hi to all. This is my first post as a (K)Ubuntu user.
Everything seems to work ok (more or less). I have a problem with an external hard disk (80Gb MAXTOR). When I switch on, Automunt detects it and mounts /dev/sde1 as /media/sde1 which is a FAT32 partition of 15Gb. But NOT MOUNT /dev/sde2, my Warehouse 65Gb FAT32 partiton.
I've looking for a similar problem but I get no answer.. can somebody help me?

---

### Post by kzutter on 2006-05-05
Hmmm.... 65gb FAT32 .... Thats BIG!
Windows XP and Windows 2000 limit partition creation to no larger than 32GB on FAT32.
They can use a FAT32 partition bigger than that, but you must have used Win98 or WinME to create it.

Its possible that linux is choking on its size.
How did you create it?
Can you mount it manually?

---

### Post by Camulus on 2006-05-06
Hi. I thinks it's not the problem. The partition was created some time ago from a linux system, my old Gentoo system (I come from a Gentoo system) and yes, I can mount it manually only as a root. 
I think it's a problem of udev rules, but it's a theme I don't know how to start with it. 
I will investigate this!

---

### Post by MJN on 2006-05-06
I could be barking up the wrong tree here (having no experience of external HDDs) but what does your /etc/fstab say? Does it have entries for /dev/sde1 and /dev/sde2? I'd guess that /dev/sde1 is in there (with an 'auto' option specified, amongst other things) whereas /dev/sde2 isn't (or it doesn't have the 'auto' option)?

Mathew

---

### Post by kzutter on 2006-05-06
I agree that looking at your fstab is next.

Here is a source for learning about udev rules- in case you are interested

[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

---

### Post by Camulus on 2006-05-07
Hi to all and thanks. My ftab don't have any entry about sde1 neither sde2 (and sde1 appears in Desktop as I plug in). I add these entries and all I get is the possibility to mount sde2 as a user, by the way of put a icon linked to /dev/sde2.
I think it's a problem with udev rules, but I don't get the answer.. Grr!

---

