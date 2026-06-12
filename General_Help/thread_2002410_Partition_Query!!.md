---
title: "Partition Query!!"
date: 2012-06-12
forum: General Help
---

### Post by sohail webconnect on 2012-06-12
Hello!! I just wanted to know how to increase the Ubuntu and swap partition size..

Partition 1 -- 387 GB(Windows 7)(NTFS)

Partition 2 -- 38 GB(Ubuntu ext4 36 GB) & (Swap 1.6GB)

Partition 3 -- 75 GB (Formatted)(NTFS)

-----------------------------------------------------------------

I want to make it like this..

Partition 1 -- 387 GB(Windows 7)(NTFS)

Partition 2 -- 112.6 GB(Ubuntu ext4 110.6 GB) & (Swap 2GB)

-----------------------------------------------------------------

I mean from Partition 3 (75 GB) I want to give 74.6GB to ext4 and 0.4GB to swap.

Please help Me I am a 15 year old Ubuntu newbie..

---

### Post by kanikilu on 2012-06-12
I'd use GParted on the Ubuntu or GParted Live CD, and then do the following:

*Note, I'm assuming here that there is nothing on the current "3rd partition" (75GB) since you say it's formatted.

1) Delete the existing 75GB NTFS partition and the swap partition.
2) Create a new swap partition to whatever size you want.
3) Extend/grow the current Ubuntu partition (#2 in your list) to use the remaining free space.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

