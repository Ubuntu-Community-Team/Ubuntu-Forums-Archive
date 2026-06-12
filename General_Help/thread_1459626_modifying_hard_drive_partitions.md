---
title: "modifying hard drive partitions"
date: 2010-04-21
forum: General Help
---

### Post by gechert on 2010-04-21
I recently installed a new 1 TB hard drive on my dual boot (Windows and Ubuntu) setup.  I used Clonezilla to copy the partitions over from my old drive.  Everything works - but I cannot resize or move the partitions.  Apparently that is because I have the max number of allowable partitions.   So I have 750 GB of unallocated space and am running out of space on my Ubuntu partition. 

Gparted shows sda1 as Karmic, sda2 as "system reserved" (I believe that's the Grub partition), sda3 as ntfs, sda4 as extended, and sda5 as linux-swap.  Sda1,4,and 5 are locked and can't be changed - even if I boot from the live CD.

Any help would be appreciated!

---

### Post by egalvan on 2010-04-21
> **gechert said:**
>   Everything works - but I cannot resize or move the partitions.  Apparently that is because I have the max number of allowable partitions.   So I have 750 GB of unallocated space and am running out of space on my Ubuntu partition. 


the 4 partition limit does NOT impact resizing and moving partitions.

> 
Gparted shows
sda1 as Karmic,
sda2 as "system reserved" (I believe that's the Grub partition), sda3 as ntfs,
sda4 as extended,
__ sda5 as linux-swap.

Sda1, 4,and 5 are locked and can't be changed
 - even if I boot from the live CD.


You must use a live cd, such as an Ubuntu install, or PartedMagic.
PartedMagic touches nothing else on the drive, so I use it for all partition work.


Booting almost any Linux system will find and use a valid swap.
so you have to turn swap off.
Check if it's mounted... right-click on the swap partition.
If so, "swap-off"
Then un-mount each partition  that is mouted...
right-click and choose "un-mount"

choose "apply actions" when done,
then partitions should all be un-mounted.

---

### Post by oldfred on 2010-04-21
Even from a liveCD it usually mounts the swap partition to speed things up. You can right click on the swap partition and swapoff.

You should not get the other primary partitions locked if you use the liveCD.

If you are expanding/moving partitions you have to also move the extended first then add a new partition inside the extended. If the space is to the right of the extended then you can expand the extended all the way and add many partitions. If you end up deleting swap to be able to move things around you will have to edit fstab with the new swap UUID or you will not be able to boot.

---

### Post by egalvan on 2010-04-21
> **oldfred said:**
> If you end up deleting swap to be able to move things around you will have to edit fstab with the new swap UUID or you will not be able to boot.


OR you could save swap's original UUID, 
make the changes to the partition,
then replace that original UUID.

No need to edit fstab or update GRUB.

this will show the UUID of all partitions
```
sudo blkid
```

my example...
```
 sudo blkid
/dev/sda1: UUID="805424F85424F318" TYPE="ntfs" LABEL="gx280-xp" 
/dev/sda5: UUID="0933d680-d893-40fa-a01d-3c819f0b2ea3" TYPE="ext3" 
/dev/sda6: LABEL="puppy" UUID="3119f61a-7ab2-4b91-b9c8-44fa795dfae5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: TYPE="swap" LABEL="swap" UUID="**7f9f938e-90da-4c2d-a75a-bd680b97aa4e**" 
/dev/sdb1: LABEL="750-data1" UUID="ea49cca2-75fc-4082-a4d7-4bc040df5d8b" TYPE="ext3" 

```

the part in **bold** is what should be saved..
cut-n-paste to a text file.
for me, simpler than editing and updating...

But I'm lazy, and Your Mileage Will Vary :)

---

### Post by gechert on 2010-04-23
Well I was able to move and resize the partitions.  Now Ubuntu works fine but Windows will not start I ran update-grub2 and Windows 7 loader shows up but will not start.

---

### Post by oldfred on 2010-04-23
Did the windows boot after you moved it to the new drive? You may have to run windows repairs.

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

