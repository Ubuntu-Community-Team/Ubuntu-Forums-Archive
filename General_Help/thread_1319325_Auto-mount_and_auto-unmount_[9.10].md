---
title: "Auto-mount and auto-unmount [9.10]"
date: 2009-11-08
forum: General Help
---

### Post by Find on 2009-11-08
Hi,

I had updated my Jaunty last week to Karmic Koala and the Koala was falling off the tree (crashing) VERY often, today, i decided to make a clean install, which sound to be much better, but there is a thing which I dont understand!

There are two users on this laptop, (+root), admi and usri. I have two other drives (one of them an XP).
while user has all the rights, (excluding Administator the system) s/he cannot mount the drives, and if I use my previlages to mount them, then when s/he logs off, i cannot mount those drives which are locked! [I didnt have this problem with Jaunty]

What the remedy is?

Thank you!
Find

Solution:
add the following to /etc/fstab 

/dev/sda1      /media/WindowsXP         ntfs    loop            0       0
/dev/sda2      /media/NoXO                 ntfs    loop            0       0

---

