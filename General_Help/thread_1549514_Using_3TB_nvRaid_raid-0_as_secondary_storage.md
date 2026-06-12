---
title: "Using 3TB nvRaid raid-0 as secondary storage"
date: 2010-08-09
forum: General Help
---

### Post by TheGame67 on 2010-08-09
Alright, so ive used Ubuntu for a while(currently using 10.04 LTS x86_64) dual booted with Windows 7, but I recently got a second 1.5tb hard drive to set up in raid-0 with nvRaid(note: I have a third 300gb hard drive that I have partitioned for the Windows 7 and Ubuntu installs, and the raid is just for storage). It all went fine and smooth in W7, but I could never get Ubuntu to recognize the drive so I just forgot about it for a while and stayed on the Windows side.

However, now that I have all my necessary data backed up, Ive dove back in to try to set this up. The strange thing is, if establish the raid and boot to W7, create a NTFS partition and reboot over to Ubuntu, all I can find in /dev/mapper/ is the drive itself, not the partition. In addition, in disk utilities, it shows a 3.0tb hard drive under peripherals with no partitions, and when I try to partition it on Ubuntu, I get the following error

```
Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/mapper/nvidia_bcedeacd, start=0, size=3000603770880, type=EBD0A0A2-B9E5-4433-87C0-68B6B72699C7
Entering MS-DOS parser (offset=0, size=3000603770880)
MSDOS_MAGIC found
found partition type 0xee => protective MBR for GPT
Exiting MS-DOS parser
Entering EFI GPT parser
GPT magic found
partition_entry_lba=2
num_entries=128
size_of_entry=128
Leaving EFI GPT parser
EFI GPT partition table detected
containing partition table scheme = 3
got it
got disk
new partition
added partition start=17408 size=3000603736576
committed to disk
Error doing BLKPG ioctl with BLKPG_ADD_PARTITION for partition 1 of size 17408 at offset 3000603736576 on /dev/mapper/nvidia_bcedeacd: Invalid argument

```Now, this is where it gets truly strange. When I rebooted over to Windows side, it showed no partitions, so I figured I messed something up somewhere, so I reinitialized the raid, booted to windows, and formated it to NTFS again, with the partition functioning fine. I then rebooted to Ubuntu, checked to see if I could access it again, to still find only the drive and not the partition in mapper. So, without doing anything else, I rebooted back to Windows, and the partition was gone there too.

I consider my self a fairly advanced computer user, on both Windows and Linux, but I am at a complete loss here, and any help would be greatly appreciated.

Thank you

---

### Post by TheGame67 on 2010-08-10
Bump, anyone have any ideas?

---

### Post by TheGame67 on 2010-08-10
Another bump, now that everyone is awake. Any insights at all are greatly appreciated, Im completely at a loss here.

---

### Post by kaicrr77 on 2011-07-03
I ran into this today with my HTPC which is using NVRAID.
I originally had 2 drives mirrored which Ubuntu didn't have a problem with... during the install. Later I wanted to add secondary storage so I figured I would use the Disk Utility. Obviously I got the "error doing with BLKPG" i dropped and recreated the RAID collection many times which didn't work.

Then i decided to do the entire creation via command line and was able to pull it off. I basically used bits and pieces of this: [http://en.gentoo-wiki.com/wiki/RAID/NVRAID_with_dmraid]("http://en.gentoo-wiki.com/wiki/RAID/NVRAID_with_dmraid")

1. ```
sudo dmraid -rE
``` to remove the old raid metadata
2. ```
sudo reboot
```Reboot. After the BIOS recreate your Raid collection within the onboard RAID disk utility.
3. ```
sudo dmraid -r
``` to look at what drives are involved in the raid collection. Copy the part that says nvidia_xxxxxx" which correlates to your drives.
4.```
sudo fdisk /dev/mapper/nvidia_xxxxx
```create your partition 
5.```
sudo reboot
```Reboot
6.```
sudo mkfs.ext4 /dev/mapper/nvidia_xxxxx
``` create your file system...and your done. Now it appears within the Disk Utility like the others and you can mount it.

---

