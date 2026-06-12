---
title: "Windows 7 upgrade screwed up everything"
date: 2010-01-12
forum: General Help
---

### Post by X1R1 on 2010-01-12
Hi all, 

I know this problem has been answered tons of times...but my problem is a little more complicated and I have no idea how to proceed from now on...

I upgraded my acer aspire 5810tz from vista to windows 7, but now...I cant access any of my other linux installations (Ubuntu and ArchLinux). Last time I did a windows upgrade. I just inserted super grub disk, and automagically grub appeared again with all my installations. 

But now, after the windows 7 upgrade...Super Grub disk cant find anything...not even the acer recovery partition. Only thing that boots its windows 7, any help?? maybe some Super Grub disk specific commands or something??

thanks in advance

---

### Post by underquark on 2010-01-12
Has Windows taken over the whole disk space (bad news) or are there any other partitions remaining?

---

### Post by X1R1 on 2010-01-12
> **underquark said:**
> Has Windows taken over the whole disk space (bad news) or are there any other partitions remaining?

I can see ALL partitions with proper space and filetype (ext3 and ext2). just to double check I installed EASEUS partition manager home under W7 and they also appear there.

---

### Post by amsterdamharu on 2010-01-12
Not sure what if supergrub will give you a grub boot menu, maybe try pressing c in the menu for commandline and then
find /boot/grub/menu.lst
or
find /boot/grub/grub.conf

This should return with hd(0,1) or whatever harddisk and partition menu.lst or grub.conf is found on.

The tab command completion might work, you can try
find /boot/vlinuz(press tab)

These would be the commands to start ubuntu (have to know what version of the kernel you have) The root you'll find depending on the find output.
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-24-generic single
initrd        /boot/initrd.img-2.6.24-24-generic

---

### Post by X1R1 on 2010-01-12
> **amsterdamharu said:**
> Not sure what if supergrub will give 

The tab command completion might work, you can try
find /boot/vlinuz(press tab)



Just an observation, there is a typo there, its vmlinuz not vlinuz, sometimes people write the commands exactly the same as typed on the forums so its worth noticing.

Regarding the other part of the post, thanks a lot for the info. I remember that when I tried the automatic Super Grub Disk method it said something like "file not found" Error 15.

but sure enough I will try the commands you posted and come back with results.

---

### Post by amsterdamharu on 2010-01-12
Yes, sorry about the typo, here is my output from grub (old one on hardy).

grub> find /boot/grub/menu.lst  
 (hd0,4)

grub> find (hd0,4)/boot/vmlinuz-(pressed tab)
 Possible files are: vmlinuz-2.6.24-24-generic vmlinuz-2.6.24-25-generic vmlinu
z-2.6.24-26-generic vmlinuz-boot


Then my commands would be:
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-24-generic single
initrd        /boot/initrd.img-2.6.24-24-generic 
boot

Note that the "single" kernel parameter is for recovery mode and should allow you to repair grub again.

---

### Post by X1R1 on 2010-01-12
Im writing this from my newly recovered Ubuntu installation, every command worked like a charm. THANKS A LOT

problem solved

---

