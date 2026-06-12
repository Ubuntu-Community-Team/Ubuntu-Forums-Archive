---
title: "Hard drive died! Please help me recover (LVM)"
date: 2010-05-27
forum: General Help
---

### Post by element_G on 2010-05-27
Today one of the Hard disks in my home server committed suicide. What I had setup was 3 hard drives (2 500GB and a 1TB) all tied together with LVM so it would appear as one big volume. The drive that failed was the 1TB drive leaving the 2 500GB. 

I managed to get the LVM back together by following this guide:
[http://www.novell.com/coolsolutions/appnote/19386.html](http://www.novell.com/coolsolutions/appnote/19386.html)

So now I have an active logical volume and volume group, however the filesystem will not mount and I cannot run fsck because it complains about a missing superblock.

Googling about superblocks has gotten me to run ```
e2fsck -b xxxx -y /dev/* 
``` (xxxx is a magic number and dev/* is the logical volume device

I have tried a lot of magic numbers but I keep getting the same complaint from fsck. I have run the following

```
# mke2fs -n /dev/sda3

and

# dumpe2fs /dev/sda3|grep -i superblock

```

but neither of these commands can find a valid filesystem superblock to use in the fsck command.

I am guessing that this problem is special because of the LVM, but I am now at my wit's end. Please help!!

---

### Post by element_G on 2010-05-27
politely bumping

---

### Post by jobix on 2010-05-27
You could try getting one of those external USB enclosures for your hard drive and see if you can retrieve data that way. It will be slow because of the USB connection.

---

### Post by element_G on 2010-05-27
thanks for the quick response, jobix but unfortunately things are not that simple because of me using LVM, I specifically need help mounting the LVM again now that I have swapped the drive for a funcioning HDD and then added that into my LVM in place of the busted HDD

---

### Post by element_G on 2010-05-27
OK, so I think the reason I cannot mount the LVM is because I used a 500GB drive to stand in for the 1TB drive that died. I am now waiting to obtain a 1TB drive to put into the LVM and from there hopefully I can mount it and recover whatever is left of my data off of the 2 500GB drives that are still healthy. Pending failure of that I will try my luck with testdisk as it claims to be able to recover data off of LVM partitions. 

If anyone reading this understands what I am about to attempt and is able to tell me if this has a chance of working please let me know your thoughts!

If anyone has been in the same boat and can offer help or advice in the meantime that would be appreciated.

For reference I found another tutorial similar to the one I posted in the OP here is the link:[http://kbase.redhat.com/faq/docs/DOC-3335](http://kbase.redhat.com/faq/docs/DOC-3335)

---

### Post by cryingthug on 2010-05-27
This is what you do! Get System Rescue CD. This CD is great. It has tons of tools! It helped me to fix my LVM. Boot off the CD then read the man pages to get the commands you need to remove the dead drive.

It worked for me. Luckily I did not have a dead drive the cable just came loose. But it did prepare me for when a hard drive says goodbye and  goes down to Davy Jones' Locker for good.

---

### Post by element_G on 2010-05-28
thanks for the tip cryingthug, do you have any tutorials you can point me to?

---

### Post by jobix on 2010-05-28
Maybe these might be useful?

[http://ubuntuforums.org/showthread.php?t=642329](http://ubuntuforums.org/showthread.php?t=642329)
[http://ubuntuforums.org/showthread.php?t=1205372](http://ubuntuforums.org/showthread.php?t=1205372)

---

