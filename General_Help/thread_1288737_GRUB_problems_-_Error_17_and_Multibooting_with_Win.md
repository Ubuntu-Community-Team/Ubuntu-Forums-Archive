---
title: "GRUB problems - Error 17 and Multibooting with Windows"
date: 2009-10-11
forum: General Help
---

### Post by Apepa on 2009-10-11
Hi There. I recently installed Ubuntu 9.04 alongside my existing Windows Vista installation. I have a major problem, because whenever I try to boot I get GRUB error 17. I can get Vista up and running again by using the Vista disc's automatic repair tool to fix the Vista loader, but this obviously means that I can't get into Ubuntu.

Now previously, I've had no problems doing this - in the past I've had a multiboot between Windows XP, Vista and Ubuntu 8 set up automatically by the Ubuntu installer, but this time it just isn't working - even after I tried installing Ubuntu again twice.

I'm currently in my installed Ubuntu, by using a SuperGrubDisk CD, but this can only be a temporary solution as I need the CD in the drive every time I boot, and I still can't access my Windows install.

This is how my machine is set up:

SATA disc 1: 
FAT32 Partition*: 10GiB
NTFS Partition**: 40GiB
Vista Partition: 85GiB (NTFS)
Installed Applications Partition:100GiB (NTFS)

SATA disc 2:
Ubuntu Partition: 40GiB (ex3)
Ubuntu Swap: 8GiB
Unallocated: 420GiB***

SATA disc 3:
Music and Video Partition: 465GiB(NTFS)
Work Partition: 465GiB(NTFS)

*Earmarked for a future Win98 install
**Earmarked for a future XP install
***Will likely format as NTFS for future expansion.

If anyone can offer any insights I'd be very greatful

Thank You.

---

### Post by khughitt on 2009-10-11
Hello,

Which version of Ubuntu did you install, 9.04?

Do you have a Ubuntu Live! CD? If you can boot into Ubuntu using the live CD, and mount the partition you installed Ubuntu onto (use "sudo /sbin/fdisk -l" to find the correct partition, and then "mount -t ext3 /dev/sdxx", assuming you installed Ubuntu using ext3).

Once you do that, can you paste the contents of:

/boot/grub/menu.lst

and

/etc/fstab

If you can't boot into Ubuntu at all, does the grub menu at least show up? If it does, you should be able to hit "e" to edit a given line. What does it say when you edit the first grub line?

---

