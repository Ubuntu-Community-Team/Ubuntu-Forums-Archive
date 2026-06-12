---
title: "GParted?"
date: 2010-11-11
forum: General Help
---

### Post by Yezinki on 2010-11-11
1. What is the command to install GParted using Terminal?

2. Which version Live CD should one download?

Thanks.

---

### Post by shadow120 on 2010-11-11
```
sudo apt-get install gparted
```

i would download 10.10.  and the live cd has gparted on it

---

### Post by Bitrate on 2010-11-11
SystemRescueCD ([http://www.sysresccd.org](http://www.sysresccd.org)) has GParted as well as other important system utilities such as Testdisk/PhotoRec.

---

### Post by Yezinki on 2010-11-12
Can the bootable CD perform a low level format & convert a all ext4 drive to NTFS?

Thanks.

---

### Post by mister_playboy on 2010-11-12
> **Yezinki said:**
> Can the bootable CD perform a low level format & convert a all ext4 drive to NTFS?

Thanks.

Yes... that's the only way to do such a task, really. :)

---

### Post by Ancanus on 2010-11-12
> **mister_playboy said:**
> That's the only way to do such a task, really. :)

I'm pretty sure that if you [boot to RAM]("https://wiki.ubuntu.com/BootToRAM"), you can unmount the hard drives and gpart them. Just elaborating on the 'only way' remark. =)

---

### Post by mister_playboy on 2010-11-12
> **Ancanus said:**
> I'm pretty sure that if you boot to RAM, you can unmount the hard drives and gpart them. Just elaborating on the 'only way' remark. =)

Did not know that. :popcorn:

---

### Post by srs5694 on 2010-11-12
> **Yezinki said:**
> Can the bootable CD perform a low level format & convert a all ext4 drive to NTFS?

Chances are the answer to the question you meant to ask is as others have stated; however, a true [low-level format](http://en.wikipedia.org/wiki/Disk_formatting#Low-level_formatting_.28LLF.29_of_hard_disks) of a disk involves re-initializing the sector definitions on the disk. This is possible with floppy disks and very old hard disks, but modern hard disks are low-level formatted at the factory and it's usually difficult or impossible for users to do so.

It's unclear precisely what you want to accomplish; however, it's probably one of these things:


[list]
[*]Completely wipe all data so that it's not recoverable -- You can do this with the dd utility, as in "dd if=/dev/zero of=/dev/sdb", which writes 0 values to all sectors on /dev/sdb. This operation will often take hours to complete. You can then create new partitions and filesystems (as described next).
[*]Create new partitions -- You can use partitioning tools such as GParted, GNU Parted, fdisk, gdisk, or various other tools to erase data on the partitions contained on the disk and create new partitions. Some of these tools will also create new filesystems (described next). This action will not destroy most data on the disk, but it will make it difficult to recover the data (the disk will appear to be empty to most disk utilities).
[*]Create new filesystems in existing partitions -- You can turn an ext4fs partition into an NTFS partition with the help of text-mode tools such as mkfs or GUI tools like GParted. If you use mkfs on a disk that uses the common Master Boot Record (MBR) partitioning system, you'll also have to use fdisk to change the partition type code of the partition, or Windows will ignore it. This action makes it very difficult to recover existing files, but not absolutely impossible, since only a tiny fraction of the sectors on the disk are actually overwritten. The disk will appear to be empty to most disk utilities and OSes, though, and as you write new files on the disk, they'll gradually obscure old data.
[/list]


If you just want to re-use the disk and aren't concerned with illicit data recovery, using partitioning and/or filesystem creation tools will be sufficient. If you want to wipe all data so there's no chance of recovery (say, before selling a computer or hard disk), wiping it with dd or a similar tool is in order. If the disk is misbehaving (which might prompt a desire to do a true low-level format), chances are you should just back up your data and discard the disk.

---

