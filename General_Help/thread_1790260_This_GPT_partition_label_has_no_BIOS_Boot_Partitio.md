---
title: "This GPT partition label has no BIOS Boot Partition"
date: 2011-06-24
forum: General Help
---

### Post by Freddie on 2011-06-24
Hello,

When I installed Ubuntu on my system (a year or so ago) I forgot to add a BIOS Boot Partition.  This is something of a problem considering that the partition type for my 2TB drive is GPT.  Hence, whenever grub is updated I get a warning:
```

/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
Installation finished. No error reported.

```

Clearly this is something that I need to address.  Looking at my partition table:
```

freddie@bromine:~$ sudo parted /dev/sda unit s print
Model: ATA WDC WD20EARS-00J (scsi)
Disk /dev/sda
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start     End          Size         File system     Name  Flags
 1      2048s     499711s      497664s      ext2                  boot
 2      499712s   2453503s     1953792s     linux-swap(v1)
 3      2453504s  3907028991s  3904575488s                        lvm

```

I notice that there is around ~1MiB of space at the start of the drive (unused due to potential alignment issues).  Hence, I am wondering if I can create a partition in this empty space at the start of the drive and use it for GRUBs stuff.

If so, what is the rough sequence of commands to create the partition (without disturbing what is already there) and then setting it as a BIOS boot partition.

Regards, Freddie.

---

### Post by oldfred on 2011-06-24
I do not see why with gpt you cannot create a partition starting at sector 40. I created my gpt on a small drive to test a while back before they were rounding to 8s so mine starts at sector 34.

srs5694's to show 8 sector alignment post #9
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
```
$ sudo parted /dev/sda unit s print
Model: ATA WDC WD10EARS-00Y (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start     End          Size         File system  Name                  Flags
 1      40s       439s         400s                      BIOS boot partition   bios_grub

```GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

see gdisk walk thru to create a new partition starting at sector 40 and ending at 2040 or whatever.

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
sudo parted /dev/sda set <partition_number> bios_grub on

---

### Post by srs5694 on 2011-06-25
There's no problem with putting a BIOS Boot Partition in that less-than-1MiB space at the start of your disk. Advanced Format performance issues aren't an problem for the BIOS Boot Partition, and you can start it at sector 40 (or 512 or 1024), if you want to eek out the extra few milliseconds you'll save in boot time over the course of the machine's life. The BIOS Boot Partition only needs to be about 30 KiB in size, so being just a hair under 1 MiB is plenty big enough.

Note that you should reboot *before* re-installing GRUB; if you don't reboot, the kernel might not yet be using the new partition table and so GRUB might not install correctly.

---

### Post by BlendMe on 2011-06-28
I had the same problem just now and I solved it by setting the flag *bios_grub* on the boot partition. No errors.

Now let's see if it worked :confused:

---

### Post by oldfred on 2011-06-28
If you had a separate /boot partition you may have erased all the boot data. It needs to be a separate partition but does not have to be very large. The bios_grub partition is an unformated area just for grub to put a boot file that in MBR(msdos) formated systems is just after the MBR.

If you have not reinstalled grub you may be able to recover the boot files.

---

