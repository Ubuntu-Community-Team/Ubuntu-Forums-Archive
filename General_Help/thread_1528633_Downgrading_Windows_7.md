---
title: "Downgrading Windows 7"
date: 2010-07-11
forum: General Help
---

### Post by Yoshi65 on 2010-07-11
Hi everybody!
I recently dual booted Ubuntu with Windows 7 and I want to downgrade to XP and still be able to into Ubuntu. Can I just reformat the Windows 7 partition and install XP?

Thanks.

---

### Post by cj.surrusco on 2010-07-11
Yes, you will be able to do that. You will have to reinstall grub after the installation of XP, because the XP bootloader will be written to the mbr. 

There are many topics on how to reinstall grub from a live CD. [_This_]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD") is one of them.

---

### Post by Yoshi65 on 2010-07-11
Cool! Thanks! I was hating Windows 7! So is there a chance I will loose any of my Ubuntu Settings or programs? Or can I just re-install Grub and everything will be the same?

---

### Post by cj.surrusco on 2010-07-11
Everything in Ubuntu will be exactly the same. Just make sure you don't accidentally format the Ubuntu partition during the XP install!

---

### Post by Yoshi65 on 2010-07-11
XD Ok! That would be bad!! Ok I will do it tomorrow (later today I guess in my time-zone) and let you know how it goes!
Thanks for your help!!

---

### Post by Yoshi65 on 2010-07-11
Ok so I read the re-installation of Grub and since I have a dual boot does that mean that I auto matically have a boot partition? and when I mount my Ubuntu partition it mounts it as NTFS and it only shows a couple files not the "dev", "proc", or "sys". I am totally lost.

---

### Post by cj.surrusco on 2010-07-11
That definitely doesn't sound like the Ubuntu partition that you are mounting. Please show the output of:
```
sudo fdisk -l /dev/sda
```

---

### Post by Yoshi65 on 2010-07-11
Here it be! On GParted It said my Ubuntu was sda3 and the files that showed up are what shows up when I open the Ubuntu partition in Windows Explorer.

```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x74b860c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         191     1534176    7  HPFS/NTFS
/dev/sda2             192       19097   151862445    7  HPFS/NTFS
/dev/sda3           25860       38913   104856255    7  HPFS/NTFS
/dev/sda4           19098       25859    54315765    b  W95 FAT32

Partition table entries are not in disk order

```

---

### Post by cj.surrusco on 2010-07-12
Uh oh. Looks like you made a mistake during the install of XP, because I don't see the ext3 or ext4 partition there. You accidentally formatted your Ubuntu partition. :-|

If you want to use Ubuntu again, then you'll have to reinstall it. Good part is at least you don't have to worry about reinstalling grub, because it will automatically be installed and detect Windows when you install Ubuntu. This time be EXTRA careful that you choose the right partitions.

---

### Post by Yoshi65 on 2010-07-12
No. I didn't install XP yet and I am using Ubuntu right now.

---

### Post by cj.surrusco on 2010-07-12
Hmmm, I don't understand how your partition table looks like that, then. Can I see a screenshot of your Gparted?
In a terminal:
```
gksudo gparted
```

---

### Post by Dustin2128 on 2010-07-12
well I'd recommend if you're already ditching your current windows partition, you just swap to a full ubuntu install. I mean, if you're formatting, there's no risk of data loss right? Just give it whatever size partition you want, set aside the rest as free space, and install XP to the free space. Just make sure you back everything up first.

---

### Post by Yoshi65 on 2010-07-12
Ok here is my screenshot of GParted.

---

### Post by bcbc on 2010-07-12
Yes you can keep the wubi install - in fact all you need is the root.disk file (under the d:\ubuntu\disks directory or whatever 'drive' letter it is). Back it up somewhere safe (outside of the directory). This file is a virtual disk that contains the whole ubuntu os, plus your data stored under ubuntu.

Then after reinstalling XP, you have to reinstall wubi as well. Then just replace the new root.disk with the backup you made.

---

### Post by cj.surrusco on 2010-07-12
You never mentioned you had a wubi install... This make so much more sense now.

---

### Post by Yoshi65 on 2010-07-16
Ok so I installed XP and then I installed Ubuntu again replaced the root.disk but that was 64-bit and the installation was 32 (because of xp being 32) so then I installed Windows 7 back because Toshiba doesn't support xp so stuff didn't work right so then I had install Ubuntu again and the root.disk got over-written and then I installed Ubuntu like a full install but only on that partition and then Windows didn't boot of course so then I got it to boot to Windows 7 and then I ran the AutoSuperGrubDisk to get the partition back but then that didn't work it came up with some error on the screen so then I tried to install Ubuntu using Wubi but now when I go to boot off of Ubuntu to finish the installation it gave me the same error as when I tried to boot off of AutoSuperGrubDisk that I installed... I think it might be that the MBR needs to be cleaned or what? What do I do?
 
Thanks.

---

