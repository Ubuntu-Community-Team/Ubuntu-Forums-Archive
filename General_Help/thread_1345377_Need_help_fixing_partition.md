---
title: "Need help fixing partition"
date: 2009-12-04
forum: General Help
---

### Post by akdms on 2009-12-04
I just noticed my partitions are completely messed up. I'd rather not have to re-install if I can avoid it. This is what I want:

sda1, ntfs, Windows restore, 5.22 Gib
sda2, ext4, /, 20 Gib
sda3, ext4, /home, 120 Gib
sda4, swap, 4 Gib


But, this is what I have:

unallocated, 1 Mib
sda1, ntfs, 5.22 Gib
unallocated, 4.46 Gib
sda3, extended, 8.68 Gib
sda6, ext4, /, 4.49 Gib
sda7, ext4, 273.13 Mib
sda5, swap, 3.83 Gib
sda2, ext4, 130.69 Gib

How do I clean this up? At the least I need to turn sda2 (130 Gib) into my home directory.

Is this possible, or do I need to re-install?

---

### Post by pqwoerituytrueiwoq on 2009-12-04
a live cd if you need to mess with the booted partition

sudo apt-get install gparted
or 
sudo apt-get install kparted
for kde

if you don't want a to use a live cd

note shrinking a partition can make it useless if it messes up 
in other words make a back up 1st

---

