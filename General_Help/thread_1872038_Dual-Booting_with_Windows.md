---
title: "Dual-Booting with Windows"
date: 2011-10-29
forum: General Help
---

### Post by theoretical on 2011-10-29
It's been a very long time since I first started fixing this problem. I want to dual boot Ubuntu and Windows using GRUB. I've tried a lot of things on Google, but none of them work. The farthest I've gone was adding a new line in the menu of GRUB, but that menu entry only gives me an error and doesn't allow me to boot. My Windows partition is on sda2. It's a FAT32 partition. I'm very close to giving up on this. Help!

---

### Post by oldtimer7777 on 2011-10-29
> **theoretical said:**
> It's been a very long time since I first started fixing this problem. I want to dual boot Ubuntu and Windows using GRUB. I've tried a lot of things on Google, but none of them work. The farthest I've gone was adding a new line in the menu of GRUB, but that menu entry only gives me an error and doesn't allow me to boot. My Windows partition is on sda2. It's a FAT32 partition. I'm very close to giving up on this. Help!

Did you try this:

[https://debianhelp.wordpress.com/2011/07/05/how-to-fix-grub-grub2-windows-mbr-and-lost-systems/](https://debianhelp.wordpress.com/2011/07/05/how-to-fix-grub-grub2-windows-mbr-and-lost-systems/)

---

### Post by theoretical on 2011-10-29
It looks like it'll help. SuperGrub would be a nice temporary solution. I'll try it sometime, thanks!

---

### Post by oldtimer7777 on 2011-10-29
> **theoretical said:**
> It looks like it'll help. SuperGrub would be a nice temporary solution. I'll try it sometime, thanks!

And this:

[https://debianhelp.wordpress.com/2011/07/05/how-to-recover-grub2-after-windows-installation/](https://debianhelp.wordpress.com/2011/07/05/how-to-recover-grub2-after-windows-installation/)

---

### Post by theoretical on 2011-10-30
> **oldtimer7777 said:**
> And this:

[https://debianhelp.wordpress.com/2011/07/05/how-to-recover-grub2-after-windows-installation/](https://debianhelp.wordpress.com/2011/07/05/how-to-recover-grub2-after-windows-installation/)
Thanks oldtimer! I just tried Super Grub, but it couldn't detect any Windows OS, even though I have one installed. Is this something I need to worry about?

---

### Post by Blaqksheep on 2011-10-30
Would you mind providing us with a little more information?

If you're comfortable, open your terminal in Ubuntu and type
```
sudo fdisk -l
```

Then post the partition tree of your HDD it displays so I can have a better look.

Also, what version of Windows is it?  Who is the manufacturer of your machine and what type of machine is it (desktop, laptop, netbook)?

  I'm an A+ Certified Tech with Windows OS expertise so I can solve problems related to the OS better than most people here at UF.  (On the contrary, they can solve your Ubuntu problems better than me :P)

The reason I need that information is because of how most consumer machines are set up.  If you were to go out tonight and buy a new laptop, out-of-the-box the partition tree would look very similar this:
```
/dev/sda1 ... UNKNOWN ... System Recovery ... 8 GB free of 13 GB
/dev/sda2 ... FAT16 ... SYSTEM RESERVED ... 17 MB free of 100 MB
/dev/sda3 ... NTFS ... Windows 7 ... 288 GB free of 307 GB
```

Most OEMs will place a hidden partition that cannot be assigned a drive letter in the sda1 slot.  Windows Vista and 7 for sure will use the first available slot, sda2 in this case, to store their bootloader.  The actual OS files and your personal files will be stored on the remainder of the HDD which is partitioned into sda3.  If you were to use gParted, or when you run fdisk -l, you should see that the 100MB partition is flagged as "boot".  This means that when Grub searches for Windows, it's not looking for the Windows partition, it's looking for the stuff contained in the FAT16 partition that holds the boot instructions.  With Windows XP, this may or may not be the case.

I'll be able to give you further information or guidance once I see your partition tree.  =)

---

### Post by theoretical on 2011-10-30
> **Blaqksheep said:**
> Would you mind providing us with a little more information?

If you're comfortable, open your terminal in Ubuntu and type
```
sudo fdisk -l
```Then post the partition tree of your HDD it displays so I can have a better look.

Also, what version of Windows is it?  Who is the manufacturer of your machine and what type of machine is it (desktop, laptop, netbook)?

  I'm an A+ Certified Tech with Windows OS expertise so I can solve problems related to the OS better than most people here at UF.  (On the contrary, they can solve your Ubuntu problems better than me :P)

The reason I need that information is because of how most consumer machines are set up.  If you were to go out tonight and buy a new laptop, out-of-the-box the partition tree would look very similar this:
```
/dev/sda1 ... UNKNOWN ... System Recovery ... 8 GB free of 13 GB
/dev/sda2 ... FAT16 ... SYSTEM RESERVED ... 17 MB free of 100 MB
/dev/sda3 ... NTFS ... Windows 7 ... 288 GB free of 307 GB
```Most OEMs will place a hidden partition that cannot be assigned a drive letter in the sda1 slot.  Windows Vista and 7 for sure will use the first available slot, sda2 in this case, to store their bootloader.  The actual OS files and your personal files will be stored on the remainder of the HDD which is partitioned into sda3.  If you were to use gParted, or when you run fdisk -l, you should see that the 100MB partition is flagged as "boot".  This means that when Grub searches for Windows, it's not looking for the Windows partition, it's looking for the stuff contained in the FAT16 partition that holds the boot instructions.  With Windows XP, this may or may not be the case.

I'll be able to give you further information or guidance once I see your partition tree.  =)
Thanks Blaqksheep. Here's the partition tree you wanted to see: 
```
theoretical@ETinspiron:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0f850f85

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT

Disk /dev/sde: 491 MB, 491782144 bytes
32 heads, 32 sectors/track, 938 cylinders, total 960512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *         489      959487      479499+   6  FAT16

```Weird...I could've sworn I had more partitions than that. sde1 must be the SD card I have plugged in. My computer is a Dell Inspiron 530. The Windows I'm running is Windows 7 Ultimate.

---

### Post by Blaqksheep on 2011-10-30
Aha!  There's your problem.

Your Dell Inspiron is a BIOS PC.  That means that no matter what version of Windows you install, Windows cannot and will not boot from a GUID Partition Table (GPT) which your HDD is set up for.  If your computer uses an EFI (will be obvious, should have a pretty boot screen instead of the texty BIOS), then 64 bit versions of Vista, XP, and 7 should boot, but a 32 bit version will never boot, and even 64 bit wont boot from BIOS PCs.

Give me a bit and I'll post some suggested solutions.

---

### Post by theoretical on 2011-10-31
> **Blaqksheep said:**
> Aha!  There's your problem.

Your Dell Inspiron is a BIOS PC.  That means that no matter what version of Windows you install, Windows cannot and will not boot from a GUID Partition Table (GPT) which your HDD is set up for.  If your computer uses an EFI (will be obvious, should have a pretty boot screen instead of the texty BIOS), then 64 bit versions of Vista, XP, and 7 should boot, but a 32 bit version will never boot, and even 64 bit wont boot from BIOS PCs.

Give me a bit and I'll post some suggested solutions.
My boot screens have always been BIOS though, and it still is. There aren't any pretty and colorful screens. I think that EFI partition has been in my computer for a while, back when I was experimenting with Hackintosh.

---

