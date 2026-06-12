---
title: "Using Gparted Partitioning Editor to clone USB sticks"
date: 2010-12-13
forum: General Help
---

### Post by gb210461 on 2010-12-13
Hi all

I now have an install of Ubuntu 10.10 on a USB drive and would like to clone the result onto another USB drive of the same size. Both USB drives are 4Gb.

I've used Gparted Partitioning Editor and have copied from the master USB stick to another USB stick. Looking from within the editor they look the same in terms of configuration after the copying process e.g same filesystem boot flag set.

When I try to boot off the copied USB stick it comes up with a 'no operating system' message at boot.

Any ideas?

Is this the right tool to use to clone USB sticks or is there another option?

Regards, Gary

---

### Post by lrgmmc on 2010-12-13
i would use the dd command. it copys bit for bit. but you need to make sure the drive you are coping to is indeed the same size. ```
sudo fdisk -l
```

---

### Post by gb210461 on 2010-12-13
Hi 
 
Came across this command snippet. Would this work if the sourse and tragets are sdc and sdd respectively?
 
dd if=/dev/sdc of=/dev/sdd conv=notrunc &while killall -USR1 dd; do sleep 5; done
 
I would be checking with fdisk -l first.
 
Regards, Gary

---

### Post by ragtag on 2010-12-13
dd works great for this, but you can get away with a much simpler variant.

```

dd if=/dev/sdc of=/dev/sdd bs=16M conv=notrunc

```

The "killall -USR1 dd" loop, is just to show the progress of the copy every 5 seconds, as dd normally gives no indication on how far along it is. bs=16M will considerably speed up the process. 

Be warned though that dd is a powerful command, so tripple check that you've got the if (input file) and of (output file) correct. It's actually possible to overwrite your boot sector, partition tables and more, with...which is not something you normally want to do. :)

There is no need for gparted or fdisk, as dd basically clones the whole disk, partition, disk labeling, format an all.

As far as I know, gparted and fdisk are just for partitioning disks, and not making complete copies of them.

---

### Post by C.S.Cameron on 2010-12-13
When cloning flash drives I just use:

> dd if=/dev/sdc of=/dev/sdd

with none of the fancy stuff on the end and it always seems to work perfect.

For your original question concerning gparted, did you set the boot flag on the second flash drive?

Edit:
dd may take a while, it seems like it is not doing anything, there is no speedometer or anything.
Have patients and do not disturb it and it should work.

---

### Post by dcstar on 2010-12-13
> **C.S.Cameron said:**
> 
........
dd may take a while, it seems like it is not doing anything, there is no speedometer or anything.
Have patients and do not disturb it and it should work.

If you want something with a real-time counter use ddrescue, then you won't lose your **patience**.

---

### Post by dcstar on 2010-12-13
> **gb210461 said:**
> 
.........
When I try to boot off the copied USB stick it comes up with a 'no operating system' message at boot.
........

Using gparted to copy individual partitions does **not** copy the MBR which holds the Grub boot code. As recommended in other posts, copy the **whole** device.

---

