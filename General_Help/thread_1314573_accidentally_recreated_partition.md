---
title: "accidentally recreated partition"
date: 2009-11-04
forum: General Help
---

### Post by Allochtoon on 2009-11-04
Hi, i accidentally removed a partition from disk and then made a new partition in exactly the same place. However, testdisk can only find the new empty partition; which lists as empty. Even after performing a deeper search.  

I am particularly looking for a set of html files under 1 specific directory. I know exactly the name of this directory. The partition filesystem is NTFS and contains some logs i wish to transpose to my linux system. 

My hope goes out to you :)

---

### Post by ST3ALTHPSYCH0 on 2009-11-04
If you made a new partition.... game over.
You can recover deleted files if the disk sector hasn't been overwritten, but deleting the partition erases data forever.

---

### Post by ST3ALTHPSYCH0 on 2009-11-05
I may have been a little hasty. Try [this]("http://www.hiren.info/pages/bootcd").

Make that [here](http://www.hirensbootcd.net/). I couldn't find a download link on the first page.

---

### Post by Allochtoon on 2009-11-08
> **ST3ALTHPSYCH0 said:**
> I may have been a little hasty. Try [this]("http://www.hiren.info/pages/bootcd").

Make that [here](http://www.hirensbootcd.net/). I couldn't find a download link on the first page.

Thanks man, your help is much appreciated :) 

ill report back if i managed to salvage :)

---

### Post by efflandt on 2009-11-08
Actually just deleting a partition does not destroy any data on it. but if you format or write anything over it, that can make it very difficult to salvage anything.  It is best to save the output of **sudo fdisk -l** before tampering with partitions.  You have to recreate the partition with exactly the same begin and end blocks for it to work like nothing happened.

Just this week I was trying to make more room on a disk that already had 4 primary partitions, and was able to shrink Windows (sda2) down after disabling virtual memory and defragging.  Since I could not make more primary partitions, I tried to see if I could make an extended partition sda3 containing sda5 (swap), sda6(to be ext3), sda7(former sda3), and sda8(former sda4) using fdisk.  But gparted could not see any filesystem on sda7 or sda8.  So I removed sda3 and everything in it, made sda3 extended end just before the old sda3 primary, and made the old sda3 into sda4.  I left what was sda4 unassigned since I already had what I needed from it.

Once I adjusted grub to boot (hd 0,3) instead of (hd 0,2) I was able to boot into the former sda3 that was then sda4, and all was well.  After doing some testing just to prove to myself that it all worked, I have since deleted and rearranged everything after sda2.

So removing a partition does not destroy anything **IF** you can recreate it exactly like it was.  But format or overwrite any of it, and all bets are off.

---

