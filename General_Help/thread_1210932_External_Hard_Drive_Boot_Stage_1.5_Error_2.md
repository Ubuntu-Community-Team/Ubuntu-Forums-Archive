---
title: "External Hard Drive Boot Stage 1.5 Error 2"
date: 2009-07-12
forum: General Help
---

### Post by EkajArmstro on 2009-07-12
I'm trying to boot ubuntu 8.04 off of a usb external hard drive on my computer. I get an error that exactly reads, "
*GRUB loading stage1.5.*
 
*GRUB loading, please wait...*
*Error 2*
". I tested the external hard drive on another computer and it booted without a problem. My motherboard is an Asus P5L-MX.

---

### Post by merlinus on 2009-07-12
Here is a note on grub error 2:

The reason why is because Intrepid now formats its partitions to use a 256 byte inode file system size, whereas previous Ubuntu verions used 128 bytes. The older Grub versions choke on the newer ext3 partitions that use 256 byte inode sizes, and Grub returns an error 2

Don't know if this applies to your situation...

---

### Post by Frugoo Scape on 2009-07-12
> **EkajArmstro said:**
> I'm trying to boot ubuntu 8.04 off of a usb external hard drive on my computer. I get an error that exactly reads, "
*GRUB loading stage1.5.*
 
*GRUB loading, please wait...*
*Error 2*
". I tested the external hard drive on another computer and it booted without a problem. My motherboard is an Asus P5L-MX.

It can't find the partition or the disk to boot off of.

---

### Post by EkajArmstro on 2009-07-12
The weird thing is that the install works with other computers... and my motherboard can recognize the USB drive enough to try and boot off of it (before returning the error).  Would there be anything specific I could change about my computer that might be causing it not to work?

---

