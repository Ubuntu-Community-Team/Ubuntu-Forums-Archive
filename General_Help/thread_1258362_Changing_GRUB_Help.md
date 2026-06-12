---
title: "Changing GRUB Help"
date: 2009-09-04
forum: General Help
---

### Post by DGortze380 on 2009-09-04
Hey All,

long story, but here's what I'm trying to do...

I have two drives, sda and sdb (or hd0 and hd1 for grub).
I have an Ubuntu Install on each drive (not for long, one's getting formatted)
I added an entry in menu.lst on hd0 for the install on hd1,0. It boots just no fine, no issues. 

My problem is this, GRUB is looking on hd0 for /boot ... I need it to read hd1 for /boot as hd0 is soon going to be formated out.

How can I change GRUB to look at hd1 for /boot info?

I tried 
>grub
>root (hd1,0)
>setup (hd1)

but that didn't help, I'm still getting the menu.lst from hd0 upon boot.

---

### Post by blueridgedog on 2009-09-04
I assume you set you bios to boot from hd1/sdb to get the install of grub to that drive?

Can you post the output of 
```

sudo fdisk -l 
```

It will help to understand the partitions in more detail.

---

### Post by DGortze380 on 2009-09-04
> **blueridgedog said:**
> I assume you set you bios to boot from hd1/sdb to get the install of grub to that drive?

Can you post the output of 
```

sudo fdisk -l 
```

It will help to understand the partitions in more detail.

haha. you know it may be that simple ... I pretty sure it's booting hd0 ... there's no way to make grub in the mbr of hd0 look at hd1,0 for menu.lst??

```

user@ubuntu-desktop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4341    34869051   83  Linux
/dev/sda2            4342        4863     4192965   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdbdef7ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2550    20482843+  83  Linux
/dev/sdb2            2551        9729    57665317+   7  HPFS/NTFS


```

---

### Post by DGortze380 on 2009-09-04
Changing the drives around in the BIOS took care of it.

This will work for now. More issues to come I'm sure when I try to get a windows install on the other drive.

Thanks for the tip.

---

### Post by blueridgedog on 2009-09-05
The reason I mentioned it was that you were setting up hd1, not hd0 based on your post, so you must have been booting off of hd1.  The key is to setup the drive that you boot from.

---

### Post by DGortze380 on 2009-09-05
> **blueridgedog said:**
> The reason I mentioned it was that you were setting up hd1, not hd0 based on your post, so you must have been booting off of hd1.  The key is to setup the drive that you boot from.

I've got it now .. I should have set root to hd1,0 and setup hd0 ... 

Now after I do the Windows install today, I should be able to fix grub by doing the same, right?

Install Windows to hd0 will overwrite the mbr on that drive. Get to a grub prompt, set root back to hd1,0 and setup hd0. Add windows to menu.lst and it will theoretically boot ...

---

### Post by blueridgedog on 2009-09-05
> **DGortze380 said:**
> Now after I do the Windows install today, I should be able to fix grub by doing the same, right?


I think you have it.

---

