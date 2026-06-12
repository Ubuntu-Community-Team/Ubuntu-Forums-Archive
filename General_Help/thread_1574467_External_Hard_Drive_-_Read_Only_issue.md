---
title: "External Hard Drive - Read Only issue"
date: 2010-09-14
forum: General Help
---

### Post by skathmandoo on 2010-09-14
I recently bought a new 500Gb Seagate external hard drive. At first  
i could use it ( copy files on to it) without any issue . But yesterday i tried to use it with my Mac Book and it didnt give me the option to copy files on to it but it still allowed me to view and copy files from the external hard drive to the Mac Book. I changed some settings on the hard drive which allowed me to copy files to it from my Mac but now this hard drive isnt allowing me to copy anything to it from my Ubuntu.

I did have a look around the forums but couldnt really get the answer. I want a solution where it would be compatible with both my MAC and Ubuntu OS. 

I tried    "sudo fdisk -l"

and got this...

rajiv@Rajiv:~$ sudo fdisk -l

Disk /dev/sda: 59.8 GB, 59814236160 bytes
255 heads, 63 sectors/track, 7272 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce18ce18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1188     9542578+   7  HPFS/NTFS
/dev/sda2            1189        7272    48869730    5  Extended
/dev/sda5            1189        7017    46821411   83  Linux
/dev/sda6            7018        7272     2048256   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table


any idea?

Thanks

---

### Post by coffeecat on 2010-09-14
> **skathmandoo said:**
> 

rajiv@Rajiv:~$ sudo fdisk -l

....

Disk /dev/sdb doesn't contain a valid partition table


any idea?

Plenty! :)

Your Mac has probably created a GUID partition table which fdisk doesn't support or understand (see edit below), but which Linux generally is quite happy with - which is why you can read your Mac-formatted drive in Ubuntu (if I read your post correct).

This is what I think has happened:

Your drive came pre-formatted NTFS, which is a Microsoft filesystem, and which Ubuntu can read and write to reliably. Mac Snow Leopard can read NTFS but not write to it out of the box. (It can be made to, but see below.) When you reformatted it in the Mac Disk Utility, you probably chose the default hfs+ journalled filesystem which Ubuntu can read but not write to. Seeing a pattern here? :wink: Also - Mac's Disk Utility defaults to the GUID partition table for hfs+ (if I remember correctly) and presumably replaced the original MBR partition table.

You have three choices:

Format the disc FAT32 using either Ubuntu Disk Utility or Disk Utility on the Mac. If you use the Mac, click the options button and choose mbr partition table. I think FAT32 is simply identified as 'MS-DOS' or something similar in the Mac Disk Utility. Disadvantage of FAT32 - prehistoric and fragile filesystem that has a 4GB filesize limit.

Format the disc in MacOS with the hfs+ non-journalled filesystem which Ubuntu can write to. Disadvantages: it's a non-journalled filesystem and inherently more fragile than a journalled one. Of more immediate importance, you will run into frustrating permissions problems. The Mac filesystem supports the same Unix permission as Linux, but your Mac UID will be 501 and your Ubuntu will be 1000.

Format the disc NTFS (with mbr, also called ms-dos, partition table) and install the Mac NTFS-3g driver. I'll give you a couple of links if that is what you want. Disadvantage: the MacOS ntfs-3g driver is s-l-o-o-o-w. Also, you **must** have Windows available. NTFS is a MS filesystem and you need Windows' chkdsk if it needs repairing.

**Edit:** Update.

I've plugged a hfs+ non-journalled SD card into my Lucid system and fdisk says:

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.
```... which is a bit different from the "doesn't contain a valid partition table" that you got. When you said "changed some settings on the hard drive" I presumed you meant you had reformatted it with Disk Utility, but perhaps not. What exactly did you do?

---

### Post by skathmandoo on 2010-09-15
I do remember using disk utility from my mac , but i  cant remember in detail what i did in it. is there anyway to find out? Also with the three options you gave which one do you recommend? i'm usually using my harddrive to transfer music & movies more than anything else.

Thank you so much for your help.

---

### Post by coffeecat on 2010-09-15
> **skathmandoo said:**
> I do remember using disk utility from my mac , but i  cant remember in detail what i did in it. is there anyway to find out?

Probably, but it's a bit theoretical if you are going to reformat anyway. Once you've made your choice, I'll help you with that if you wish.

> **skathmandoo said:**
>  Also with the three options you gave which one do you recommend?

Depends on your circumstances. If you have Windows available then perhaps NTFS, so long as you are patient. NTFS copies in MacOS are leisurely.

If you are comfortable with some judicious chown-ing and chmodding, the non-journalled MacOS HFS+ is a good bet, although it is non-journalled. How much do you know about Unix-style permissions (Linux and Mac use the same system even on different filesystems)?

Of course, the simplest option is FAT32, but don't use that if you can't back all your files onto another medium. It is an ancient filesystem which is almost impossible to repair if it goes wrong - no journal. And don't forget the 4GB filesize limit. Important if you are storing video files.

---

### Post by srs5694 on 2010-09-15
> **skathmandoo said:**
> I do remember using disk utility from my mac , but i  cant remember in detail what i did in it. is there anyway to find out?

It's possible that the disk uses the Apple Partition Map (APM), which Apple used on Macs prior to its release of Intel-based machines. Current Macs support creating such partition tables, so it's conceivable that you accidentally created one even if you're using an Intel-based Mac.

The GNU Parted, GParted, and other libparted-based tools support APM, so if you launch one of them on the disk, you should see the disk's partitions. If you select View -> Device information in GParted, a pane will open on the left that will identify the partition table type, among other things. APM reads as "mac" in GParted. Linux also supports APM, although I don't know offhand if the default kernel for x86 and x86-64 builds of Ubuntu includes APM support.

All that said, unless the drive was sold explicitly for Macs, I think it's unlikely that it uses APM. AFAIK, no standard OS X utility will convert another disk type to APM in a non-destructive way; you'd need to repartition the disk (wiping its data) to convert it to APM.

A more likely explanation is that the disk originally used a "raw" filesystem -- in other words, NTFS or FAT without a carrier partition. If this is so, it's possible that the disk wasn't cleanly unmounted and Linux is therefore unable to mount it. The fdisk utility will correctly report that it has no partitions. The solution in this case is to attach the drive to a Windows computer and schedule a disk check (or multiple disk checks), then cleanly unmount it. You should at least be able to test whether this is the case by using blkid on the whole disk, as in "sudo blkid /dev/sdb". If this command reports that the type is "ntfs", then this hypothesis is correct; if the command returns with no output, them this hypothesis is incorrect.

---

