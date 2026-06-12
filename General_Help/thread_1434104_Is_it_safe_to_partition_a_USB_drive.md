---
title: "Is it safe to partition a USB drive?"
date: 2010-03-19
forum: General Help
---

### Post by ZeldaFan on 2010-03-19
Is it safe to partition a USB drive? I heard somewhere that partitioning a flash drive is unsafe/unstable and could cause damage to it. Is this true? I have an 8 GB and was planning on having a linux distro partition and a FAT32 data partition.

---

### Post by wilee-nilee on 2010-03-19
> **ZeldaFan said:**
> Is it safe to partition a USB drive? I heard somewhere that partitioning a flash drive is unsafe/unstable and could cause damage to it. Is this true? I have an 8 GB and was planning on having a linux distro partition and a FAT32 data partition.


I have never heard this concern before, I have and do this all the time with 3 different thumbs and have had no problems.

Edit: I have seen a warning about partitioning to the cylinders size, but I have never worried about this.

---

### Post by 2hot6ft2 on 2010-03-19
This made me think of a change I wanted to make to my usb flash drive installed ubuntu so I got rid of the small swap partition on it and expanded the storage partition. I haven't had any problems with partitioning usb flash drives.

---

### Post by bumanie on 2010-03-19
Flash memory is a non-volatile memory system that uses NAND gates. As far as I know it is the same as is used in the newer ssd hard drives - there should not be any problem associated with partitioning a flash drive.

---

### Post by psusi on 2010-03-19
Where did you hear such nonsense?

---

### Post by Austin25 on 2010-03-19
It is most definitely safe to partition a flash drive; I have put my flash drive under some of the worst stresses you could think of(formatting, partitioning, huge file creation/deleting) and it has not died yet.

---

### Post by jskandhari on 2010-03-19
Well make the Image of The Flash USB before hand and if any error occurs restore it to its orignal state via Image...

Happy Installing :)
Cheers

---

### Post by jskandhari on 2010-03-19
Well make the Image of The Flash USB before hand and if any error occurs restore it to its orignal state via Image...

Happy Installing :)
Cheers

---

### Post by ZeldaFan on 2010-03-19
> **psusi said:**
> Where did you hear such nonsense?

[http://www.gearfire.net/6-fun-things-to-do-with-your-new-usb-drive/](http://www.gearfire.net/6-fun-things-to-do-with-your-new-usb-drive/)

Check out number 6. I never figured there would be a problem but this got me a little worried.

---

### Post by efflandt on 2010-03-19
For flash memory it depends upon the quality.  While flash memory should be able to take many write cycles, if the related circuitry is substandard, it can fail (and has failed for some).  I never had any CF, SD, microSD, or USB flash fail yet.  But I buy name brands and use tmpfs for /tmp (like USB Startup Disk Creator).  I even put a bootable Linux system on microSD (which can boot from USB card reader or internally USB connected memory slot).

I have accidentally tried to format a USB flash "drive" instead of "partition", but gparted can start over from scratch with partition table and partition(s).

So far no issues repartitioning portable USB hard drives either.  I shrunk the FAT32 partition on one with gparted to make room for regular bootable Ubuntu on ext3 with grub in the mbr of the USB drive.  And on another one I have an ntfs partition with separate regular bootable Ubuntu.

---

### Post by srs5694 on 2010-03-19
There's nothing magical about the data structures involved in partitioning; it's all just 1s and 0s. Furthermore, every USB flash drive, CF drive, etc., that I've ever seen has been partitioned at the factory. It's just that they're usually partitioned with *one* partition. They still have the MBR data structures, though. The only way I can think of that adding another partition or two to the MBR would have a detrimental effect would be if that first sector were defective in a very unusual way.

I suspect that the vague comments referenced by ZeldaFan are a progressive distortion, over several generations of retelling, of the fact that Windows can only use the first partition on removable media. That is, if you put two, or five, or fifty partitions on a USB flash drive, Zip disk, or other removable disk, Windows will only recognize the first partition. (I don't think this applies to external USB hard disks, but I'm not positive of that.) This is purely a Windows limitation, but of course many people don't understand the difference between a Windows limitation and a limitation of computers generally. Still, it's something you should keep in mind if you want to partition a removable disk of any sort; if Windows must access the disk, either don't partition it or ensure that Windows only needs to access one partition and make it the first one.

Also and FWIW, I'm the author of the [GPT fdisk](http://www.rodsbooks.com/gdisk/) partitioning software, and I do most of my GPT fdisk testing on USB flash drives. I've got several, ranging in size from 1GB to 16GB, and I can partition and repartition them without trashing my real hard disks if there's a bug in the version I just compiled. Thus, these drives have all been repartitioned dozens of times with no obvious ill effects.

---

### Post by psusi on 2010-03-19
"is sketchy at best"?  Sounds like he's repeating FUD.

---

