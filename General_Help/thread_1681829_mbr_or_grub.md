---
title: "mbr or grub"
date: 2011-02-04
forum: General Help
---

### Post by kaykav on 2011-02-04
Hi
         Im not sure I understand the booting process.  Does a 'master boot record' (MBR) have to be installed if I only have Linux systems?  Do I need Mbr and Grub to boot into Linux?
     I only have Linux on my hard drives. Where can I find info on this subject ,without the explanation being too 'geeky'?..........Thank you

---

### Post by DiSTORT3D on 2011-02-04
Grub modifies your MBR, You can`t have 2 things in the MBR

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by Rhizoid on 2011-02-04
Simplistically, the MBR is where the code required to boot the operating system and tell it how the disk is partitioned gets installed.

All partitioned disks have an MBR - whether there's any bootable code in it is a different matter.

Suffice to say, if you have a single disk and your disk is partitioned (even a big single partition) and you have grub installed - then grub will be installed into the MBR of your disk.

If you overwrite or remove the code in the MBR chances are good you'll stop your computer from starting properly.

---

### Post by kaykav on 2011-02-04
Thank you for that. Sometimes basics review is necessary...

---

### Post by oldfred on 2011-02-05
While this discusses Vista primarily, it applies to all MBR (msdos) systems.

Lots of detail but pictures do easily explain it.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

BIOS starts process of booting and with MBR partitioning jumps to the primary master drive's MBR to continue booting. With SATA, BIOS have been updated to let you select with BIOS which drive to boot, where in the early days it was just jumpers on the hard drive to determine master or slave and which cable was primary or secondary.

Big changes coming soon with UEFI in place of BIOS and gpt in place of MBR. Apple already uses EFI and gpt.
[http://en.wikipedia.org/wiki/UEFI](http://en.wikipedia.org/wiki/UEFI)

---

### Post by srs5694 on 2011-02-05
> **Rhizoid said:**
> Simplistically, the MBR is where the code required to boot the operating system and tell it how the disk is partitioned gets installed.

This is succinct but not "simplistic," except for one caveat....

> All partitioned disks have an MBR - whether there's any bootable code in it is a different matter.

In the sense of "MBR = first sector of the hard disk", this is correct; however, in the sense in which you defined it earlier, there are other partitioning and boot-loader systems. In terms of partitioning, there's the Apple Partition Map (APM), which was used on 680x0- and PowerPC-based Macs, which doesn't use an MBR. (I'm not sure if there's any boot code in the APM's first sector.) The GUID Partition Table (GPT) has a "protective MBR," which exists just to keep GPT-unaware utilities from messing with the disk; GPT partitions are defined elsewhere. On an EFI-based computer, there will be no boot loader code in the GPT's protective MBR; the EFI has its own boot loader, which relies on files in a specific partition on the disk to help it along. GPT can be used on BIOS-based computers, in which case there will be a boot loader in the protective MBR, at least if it's a boot disk.

---

### Post by glene77is on 2011-02-07
SRS, 
Good info. :)
I was reading that some Microsoft Applications write a smidgen of code in MBR 
in order to control version/upgrade.  
I read that a user installed a new MS_Windows  application, and his MBR failed.
Can't find the reference right now.  But the idea certainly appears plausible.

---

