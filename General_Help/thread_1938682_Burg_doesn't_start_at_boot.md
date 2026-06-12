---
title: "Burg doesn't start at boot"
date: 2012-03-10
forum: General Help
---

### Post by Subidubi32 on 2012-03-10
Burg doesn't start at boot, always grub2 comes up with it list. I have installed the burg from this repository: "ppa:n-muench/burg" It workes fine when emulated in ubuntu, but does not run as real boot menu. I don't know, what did I wrong, I followed the installation guide, and it just doesn't work.

---

### Post by Subidubi32 on 2012-03-10
So do you Have any idea please? What could be the problem? :confused:

---

### Post by b0b138 on 2012-03-10
Could you show the output of sudo fdisk -l

---

### Post by Subidubi32 on 2012-03-17
That is it:


Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xba346776

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   300674990   150337464    7  HPFS/NTFS/exFAT
/dev/sda2       300675070   398295039    48809985    5  Extended
/dev/sda5       394106880   398295039     2094080   82  Linux swap / Solaris
/dev/sda6       389916672   394106879     2095104   82  Linux swap / Solaris
/dev/sda7       300675072   385724415    42524672   83  Linux
/dev/sda8       385726464   389914623     2094080   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by lolpenguin on 2012-03-17
You probably haven't written BURG to the MBR. This will overwrite GRUB and if things go wrong, you will be temporarily unable to boot.

---

### Post by Subidubi32 on 2012-03-17
How could I write the BURG to MBR? If something go wrong can I restore grub2 from the live CD?

---

### Post by Subidubi32 on 2012-03-18
It's solved

---

