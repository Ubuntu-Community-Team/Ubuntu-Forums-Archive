---
title: "External Hard Drive"
date: 2009-09-28
forum: General Help
---

### Post by lrcaballero on 2009-09-28
Hi everyone,

I am running Ubuntu 9.04, I did a clean installation wiped-out Windows Vista. When I plug in my usb flash drive it is recognized by ubuntu, but not my external hard drive where I have all my music, photos, etc. I already did;
[COLOR=Blue]sudo aptitude update[/COLOR], also did [COLOR=Blue]sudo aptitude install ntfs-config[/COLOR] and when I go to check it[COLOR=Blue]   sudo[/COLOR] [COLOR=Blue]fdisk -l[/COLOR], it is recognized in the terminal, it shows 3 storage devices, my internal HD, USB Flash Drive and my Seagate 160 GB, although this last one does not appear in my desktop. Can someone help me please!!! what else do I need to do??

Thank you!![IMG]file:///home/lrcaballero/Desktop/Screenshot.png[/IMG]

---

### Post by hazyumps on 2009-09-28
try to make a new folder in /mnt

sudo mkdir /mnt/exthdd

then mount (im assuming that the last sdb is what your getting after)

sudo mount -t vfat /dev/sdb1 /mnt/exthdd

then you should just be able to access this from your filesystem

---

### Post by Bigneil on 2009-09-28
i once had a external drive that wouldn't mount until i had plugged it into a windows computer then clicked the 'safely remove hardware' icon in the tray. then i plugged it back into ubuntu and it worked fine.

i think if a drive wasn't dismounted properly from a windows machine prior to being plugged into ubuntu it gets a bit upset.

worth a try?

---

### Post by lrcaballero on 2009-09-28
Thanks! for your feedback, I will try that. :)

---

### Post by scouser73 on 2009-09-28
> **Bigneil said:**
> i once had a external drive that wouldn't mount until i had plugged it into a windows computer then clicked the 'safely remove hardware' icon in the tray. then i plugged it back into ubuntu and it worked fine.

i think if a drive wasn't dismounted properly from a windows machine prior to being plugged into ubuntu it gets a bit upset.

worth a try?

+1 for that tip, it's well worth knowing about the safe removal of hardware from Windows machines as I've encountered that myself.

---

