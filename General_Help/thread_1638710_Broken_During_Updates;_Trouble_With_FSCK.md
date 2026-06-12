---
title: "Broken During Updates; Trouble With FSCK"
date: 2010-12-06
forum: General Help
---

### Post by apocalypsemystic on 2010-12-06
Hi, I have a black 2007 MacBook running Ubuntu. Earlier today while  installing the system updates something broke and the install could not  finish. I then saw strange behavior such as messages about some sort of  file daemon that wasn't found and eventually the system ground to a  halt. On reboot it would not start up. It sounds a lot like the problem [here]("http://ca.ubuntuforums.org/showthread.php?t=1627742").

I tried following the solution to the thread but I'm getting stuck because my Ubuntu is actually on the same physical disk (I believe) as my Windows install and I don't know how to get fsck to work on the logical partitions (it complains about not recognizing GUID). My computer has a defunct Mac OSX snow leopard install on sda2 (the disk is messed up), and a Windows Vista and Ubuntu 10.04 install on sda3. Can anyone help me figure out how to get fsck to work? I'm on a slax live cd now as per the thread. Here's my parted -l. Thanks.

```
root@slax:~# parted -l
Warning: Unable to open /dev/hda read-write (Read-only file system).  /dev/hda has been opened read-only.
Error: /dev/hda: unrecognised disk label

Model: ATA WDC WD2500BEVS-0 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system  Name                  Flags
 1      20.5kB  210MB  210MB   fat32        EFI System Partition  boot
 2      210MB   103GB  103GB   hfs+         Untitled 1
 3      103GB   143GB  40.0GB  ntfs         BOOTCAMP
 4      143GB   145GB  2000MB  linux-swap
 5      145GB   155GB  10.0GB  ext3
 6      155GB   250GB  94.6GB  ext3


Error: /dev/md0: unrecognised disk label
```Edit: Here's the output for fsck:

```
root@slax:~# e2fsck /dev/sda3
e2fsck 1.41.3 (12-Oct-2008)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda3

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```And of course no luck with -b 8193

At some point fsck told me to use parted:

```
root@slax:~# parted /dev/sda
GNU Parted 1.8.8
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) check
Partition number? 5
Error: File system was not cleanly unmounted!  You should run e2fsck.  Modifying an unclean file system could
cause severe corruption.
Ignore/Cancel? cancel
```How do I use e2fsck on the logical partition 5?

EDIT: I might have been able to get the system back but I deleted the mac partition which is a bad call on a macbook. Ended up clean installing everything.

---

### Post by srs5694 on 2010-12-06
Why were you trying to use e2fsck on /dev/sda3? Your parted output clearly indicates that partition uses NTFS, and fsck is useless on NTFS.

You have no logical partitions; your disk uses the GUID Partition Table (GPT) system, which does not use logical partitions. You can use e2fsck on /dev/sda5 just as you tried it on /dev/sda3, but it's more appropriate for /dev/sda5, since parted identified it as having an ext3 filesystem.

---

### Post by apocalypsemystic on 2010-12-06
It could not find a device /dev/sda5

```

root@slax:~# e2fsck /dev/sda5
e2fsck 1.41.3 (12-Oct-2008)
e2fsck: No such file or directory while trying to open /dev/sda5

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


```

What is the difference between a logical partition and the 5+ non primary partitions? Still new to this.

---

### Post by srs5694 on 2010-12-07
Please post the output of:

```
ls /dev/?d*
```

That will show us what partitions Linux is detecting. It's possible that Linux isn't reading the GPT data for some reason. You could also try downloading [GPT fdisk,](http://sourceforge.net/projects/gptfdisk/files/) typing "sudo gdisk -l /dev/sda", and posting the results here. That'll give a view of the disk using another utility, which might provide some clues.

As I posted before, your disk (like most Intel-based Mac disks) uses the GPT partitioning system, which does not use extended or logical partitions. GPT provides the ability to store up to 128 partitions by default, which you can think of as 128 primary partitions (although the term "primary partition" really is an MBR-only concept). See the [Wikipedia article on GPT](http://en.wikipedia.org/wiki/GUID_Partition_Table) and the [Wikipedia article on MBR](http://en.wikipedia.org/wiki/Master_Boot_Record) for miore details about how these partitioning systems differ.

---

### Post by apocalypsemystic on 2010-12-09
Ah, thanks. Still getting adjusted to non mac. Here's the output from the slax live CD:

```
root@slax:~# ls /dev/?d*
/dev/adsp  /dev/cdr0@   /dev/cdrom0@  /dev/cdrw0@     /dev/cdwriter0@  /dev/hda  /dev/sda   /dev/sda3
/dev/cdr@  /dev/cdrom@  /dev/cdrw@    /dev/cdwriter@  /dev/fd@         /dev/md0  /dev/sda1  /dev/sda4
```

```
Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   3       202000384       280125383   37.3 GiB    0700  BOOTCAMP
   4       280125440       284030975   1.9 GiB     8200
   5       284030976       303562751   9.3 GiB     0700
   6       303562752       488396799   88.1 GiB    0700
```

Would ubuntu live cd output be useful? Thanks.

---

### Post by srs5694 on 2010-12-11
I'm not very familiar with Slax, and I didn't realize you were using it for maintenance. It appears that the Slax CD doesn't include GPT support, which means it's only reading the MBR partitions. I suggest you throw the Slax CD in the trash for this reason; anything that doesn't support GPT will be suboptimal at best, and useless at worst, on your system. Instead, use an Ubuntu Live CD, [Parted Magic,](http://partedmagic.com/) or [System Rescue CD](http://www.sysresccd.org/) for maintenance. These all include GPT support.

---

### Post by apocalypsemystic on 2010-12-11
Ah ok. I was going based on this post [here]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/668561?comments=all"). I'm on the system rescue disk. It correctly lists all the /dev/sda[1-6]. The gdisk output is the same though.

EDIT: Ok, I cleaned sda5 with e2fsck -p and it claims to have cleaned it. It must have done something because now the installation seems to progress fine. My only question now is should I proceed with installing a new ubuntu over the old sda5 or is there a chance the old one is now fine and I just have a problem with whatever is responsible for detecting my partitions and letting me boot into my various operating systems on start up? Right now I'm just getting a grey screen on start up with a flashing questionmark folder.

Ah ok. I was going based on this post [here]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/668561?comments=all"). I'm on the system rescue disk. It correctly lists all the /dev/sda[1-6]. The gdisk output is the same though.

EDIT: Ok, I cleaned sda5 with e2fsck -p and it claims to have cleaned it. It must have done something because now the installation seems to progress fine. My only question now is should I proceed with installing a new ubuntu over the old sda5 or is there a chance the old one is now fine and I just have a problem with whatever is responsible for detecting my partitions and letting me boot into my various operating systems on start up? Right now I'm just getting a grey screen on start up with a flashing questionmark folder.

EDIT2: Maybe when I deleted my first mac partition with the disk utility in ubuntu it contained the bootloader? Still working out how all this fits together lol.

---

### Post by srs5694 on 2010-12-11
Booting Ubuntu with OS X on a Mac requires jumping through extra hoops, since Ubuntu really assumes a BIOS-based PC. Apples can look like this to software, but there are complications because of the need for a hybrid MBR and other issues.

You can probably get your existing installation to boot by re-installing the boot loader, but I'm not positive of that, and you'll have to figure out the details yourself -- I don't happen to have them handy in my brain at the moment. OTOH, if you haven't invested a lot of time in customizing the installation, re-installing it from scratch may be easier than trying to recover it.

---

