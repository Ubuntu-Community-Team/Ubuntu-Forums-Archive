---
title: "NTFS flagged as boot?..."
date: 2011-03-29
forum: General Help
---

### Post by adduds on 2011-03-29
just wondering why my windows partition it flagged as boot? thought it should be Linux...

my system works fine just wanted to make sure nothing was out of the ordinary

i recently screw something as nothing would boot windows nor linux so i booted from live and did a fsck tons of errors fixed all then did a
```

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```


```
toews@kidlapp:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000da660

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       62704   503665664   83  Linux
/dev/sda2   *       62705       76467   110551297+   7  HPFS/NTFS
/dev/sda3           76468       77826    10903553    5  Extended
/dev/sda5           76468       77826    10903552   82  Linux swap / Solaris
```

like i said a i get a grub menu at boot just bein' thorough :D

(win7, meerkat dual boot)

---

### Post by oldfred on 2011-03-30
Windows (and Lilo) boot loader uses the boot flag to know what primary partition to jump to as that partition's boot sector (PBR) has more boot code. 

Grub does not normally install any boot code to the PBR and to chainload windows just jumps to the windows partition just as the windows boot loader in the MBR did. Grub therefore does not use boot flag. 

There are a few BIOS that seem to be only for windows as the BIOS stops booting if no boot flag is on a primary partition. IF you reinstall the windows boot loader or use a windows  repair CD to fix the windows partition, then you have to have the flag on the windows partition. Windows can only find a partition to repair if it has the boot flag.

Lots of info but you can review pictures and get a good idea.:

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

This is all for MBR/msdos systems. New UEFI system will be somewhat different. Macs are already EFI (not quite UEFI) and new motherboards seem to have UEFI or MBR capabilities.

---

### Post by adduds on 2011-03-30
thanks very much oldfred! really appreciate it 

ya the newer asus boards have UEFI

---

