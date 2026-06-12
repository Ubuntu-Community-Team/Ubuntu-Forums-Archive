---
title: "Dual-Booting Issues"
date: 2010-05-02
forum: General Help
---

### Post by Tramx on 2010-05-02
I wanted to try dual-booting Ubuntu with Windows. I installed windows first with 50% Ntfs and 50% empty. When I began installing Ubuntu I manually created sda? (0,1) Ntfs 50% / sda (0,2) Swap ~2% / sda (0,3) ext3 48%. When installation completed I was able to run Ubuntu on ext3, but the Windows partition (ntfs) does not seem to be recognized. I also expected a grub bootloader during startup but there was none and Ubuntu started right away.
What have I done wrong? Apologies, I'm new at this...

---

### Post by P4man on 2010-05-02
to show grub hold down the shift key right after the bios.

As for windows, try opening a terminal and run

```
sudo update-grub
```

copy/paste  the output here. If it doesnt detect windows, then show us the output of

```
sudo fdisk -l
```

as well

---

### Post by dino99 on 2010-05-02
> **Tramx said:**
> I wanted to try dual-booting Ubuntu with Windows. I installed windows first with 50% Ntfs and 50% empty. When I began installing Ubuntu I manually created sda? (0,1) Ntfs 50% / sda (0,2) Swap ~2% / sda (0,3) ext3 48%. When installation completed I was able to run Ubuntu on ext3, but the Windows partition (ntfs) does not seem to be recognized. I also expected a grub bootloader during startup but there was none and Ubuntu started right away.
What have I done wrong? Apologies, I'm new at this...

follow  [http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14

---

### Post by Tramx on 2010-05-02
Sorry for the late reply... I was updating Video drivers :P

Here is the output for the "sudo fdisk -l" command

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a0f5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       14592   117210208+   f  W95 Ext'd (LBA)
/dev/sda5           11533       14592    24579418+   7  HPFS/NTFS
/dev/sda6               1         307     2465883   82  Linux swap / Solaris
/dev/sda7             308       11532    90164781   83  Linux

Partition table entries are not in disk order

```

I'll also try dino99's method... Thank you so far

*edit

Since I can still access my Windows files let me try re-installing
Ubuntu first and then Windows last; I bet that might help...

---

