---
title: "Combine two partitions to make larger swap part, Ubuntu 10.10"
date: 2011-01-09
forum: General Help
---

### Post by djaunl on 2011-01-09
Hi all,

I've searched for a solution to this for awhile but cannot seem to find anything that solves my problem. 

I have a very small swap partition, about 500MB. I have a partition of essentially free space, formatted to ext4, mounted at /space. This has 10GB. I want to unmount /space and merge it into my swap partition so my swap partition will then have 10.5GB of memory. 

When viewing my partitions with gparted, these partitions are both part of /dev/sda4. /space is located at /dev/sda6, and linux-swap is at /dev/sda5. 

Alternatively, I have about 9GB of "unallocated" memory, and I can merge that to my swap partition if possible. I have Ubuntu on a separate partition, /dev/sda2, and I have Windows 7 on another partition, /dev/sda3. 

I cannot find anything that describes how to merge two partitions together, whether it's using a graphical program like gparted, the Ubuntu boot disk, or just a plain ol' command line tool like fdisk. 

Here is the output of fdisk -l:

```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x98000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          21      168651   de  Dell Utility
/dev/sda2   *        7736       77826   562992128   83  Linux
/dev/sda3            1146        6462    42700510    7  HPFS/NTFS
/dev/sda4            6462        7736    10240001    5  Extended
/dev/sda5            7677        7736      481280   82  Linux swap / Solaris
/dev/sda6            6462        7677     9758720   83  Linux

```

In summary: how do I merge an existing partition, or a block of unallocated memory, into my swap partition?

I would greatly appreciate any help in solving this problem. Please let me know if I need to provide any more information. 

Thanks!

---

### Post by Quackers on 2011-01-09
Welcome to UF.
What is on your sda6 space partition?
How much ram does your machine have?

---

### Post by djaunl on 2011-01-09
> **Quackers said:**
> Welcome to UF.
What is on your sda6 space partition?
How much ram does your machine have?

Thanks for the reply Quackers. /space is empty except for a lost+found directory. I have no qualms completely formatting the partition and erasing whatever may be on it. My machine has 8GB ram.

---

### Post by kevxh on 2011-01-09
As the swap partition sda5 and spare partition sda6 are consecutive simply delete them both and create a new swap partition in the space created.

---

### Post by Quackers on 2011-01-09
With 8GB of ram you would probably get away without a swap partition, unless you intend to use hibernate.
If you want to delete sda6 you should boot from the live cd/usb (so the system is not mounted) then right-click on the swap partition (sda5) and select "swapoff". You can then delete sda6, by right-clicking on it and selecting delete, then click on the green tick in the toolbar to apply the change.
You can then extend the swap partition in to the free space left by sda6, by clicking on the right edge of sda5 and dragging it to the end of the free space, then clicking on the green tick to apply the change.
You should then right-click on your larger sda5 and select "swapon", then reboot.
Having said all that, 10.5 GB is a HUGE swap partition and is almost certainly not needed.

---

### Post by djaunl on 2011-01-09
Thanks for the replies. I do indeed wish to use hibernate, which is why I'm trying to do this. Sorry for not mentioning that in my original post. I will try your suggestions after I get home from work tonight and report back. 

I have one followup question. Rather than booting from the Ubuntu live CD, can I delete the line about /space in /etc/fstab, use umount -a, then delete and extend the partitions using something like gparted?

---

### Post by Krytarik on 2011-01-09
There is another -not really unimportent- thing you have to take care off after merging the two partitions to a new swap partition: imo the UUID will change, thus the entries in /etc/fstab and /etc/initramfs-tools/conf.d/resume have to be updated. Look here for details:
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

---

### Post by Quackers on 2011-01-09
The info I gave above was using gparted. It is usually safer to do partition changes when the file system is not mounted. However, in your case, as you only intend to change the swap arrangement, it may be possible to do it from your mounted Ubuntu system.
It would be interesting to see if other users agree with that view.
If that is ok, you would effectively remove the etc/fstab entry for /space by running ```
sudo update-grub
``` in a terminal - BEFORE you reboot.

I believe the UUID of the swap partition will not change if you only extend it. If you delete it then make a new swap partition the UUID will be changed.

---

### Post by Krytarik on 2011-01-09
> **Quackers said:**
> If that is ok, you would effectively remove the etc/fstab entry for /space by running ```
sudo update-grub
``` in a terminal - BEFORE you reboot. Eh, this would not touch fstab imo?!
> **Quackers said:**
> I believe the UUID of the swap partition will not change if you only extend it. If you delete it then make a new swap partition the UUID will be changed.
You maybe right, though I would indeed choose to delete both and then create a new one, since gparted always failed in resizing a partition, at least FAT/NTFS.

You may try it this way:
- unmount /space partition (sudo umount /space)
- remove the entry from fstab
- use gparted to merge/create the swap partition
- take care fo the UUID thing
- reboot

---

### Post by Quackers on 2011-01-09
Hold the bus! :-)
Let me get some clarification on this etc/fstab point as I'm not sure about it.
I'll be back :-)

---

### Post by oldfred on 2011-01-09
You should be able to resize a partition without changing UUID. If you delete and recreate that will be a new UUID and you will have to edit fstab. 

Often updating grub is also required, but if you are just changing swap, I do not think it is required. And the update to grub does not fix fstab. The only way I know to update fstab is manually.

---

### Post by Quackers on 2011-01-09
If there is an entry in etc/fstab that mounts your /space partition, it would need to be deleted manually after the partition is deleted, as Krytarik said. 
The UUID for the swap partition would not change if it is extended so that entry in etc/fstab would not need to be changed. If the swap partition is deleted, then re-created as a new larger swap partition, the entry in etc/fstab for the UUID would need to be changed to reflect the new UUID.
Apologies for the confusion there.

EDIT  thanks oldfred.

---

### Post by djaunl on 2011-01-10
Hi all,

I followed the directions in this thread and it worked. I ended up merging my existing swap space, /dev/sda5, into my mounted /space partition, /dev/sda6. Here are the steps I followed:

1. sudo umount /space
2. sudo vi /etc/fstab, commented out line where /space mounted
3. sudo gparted
4. deleted /dev/sda6 (formerly mounted at /space)
5. swapoff /dev/sda5
6. resize/move /dev/sda5, resized it into the now unallocated memory where /dev/sda6 was
7. swapon /dev/sda6
8. reboot

The UUIDs did not change, as mentioned in this thread, since I merged sda5 into sda6. I did not need to change anything in /etc/fstab, except for that mentioned in step #2 above, and I did not need to change anything in /etc/initramfs-tools/conf.d/resume. 

Now, I have around 10GB of swap space to complement my 8GB RAM. I have 1.00MB of unallocated memory where sda6 was that I don't know how to get rid of, but whatever. Finally, I tested out hibernation and it works. 

Thanks a lot to everyone who replied.

---

### Post by oldfred on 2011-01-10
Do not worry about the 1MB of space. That has to do with the new rounding used to put partitions on 1MB boundaries rather than cylinders, which actually have not been used for years with LBA. Before the space was smaller and due to rounding you did not see it.

One user tried to move partition and damaged the partition somehow. So it is not something to worry about.

---

### Post by Quackers on 2011-01-10
Nice to see things went smoothly :-)

---

