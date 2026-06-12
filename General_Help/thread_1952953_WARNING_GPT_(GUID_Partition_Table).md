---
title: "WARNING: GPT (GUID Partition Table)"
date: 2012-04-05
forum: General Help
---

### Post by golia on 2012-04-05
Hi all,

I have installed Ubuntu on my desktop pc.
The disk has 2TB of space. However I have created one partition of 60 GB with mount type / and 32 GB for swap  (I have 16 gb of ram).The rest I left it as unpartitioned space
I have also encrypted the home folder

Everything is working perfectly but when I am trying to run fdisk -l I get the following output:

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xec8f0bfb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  3907029167  1953514583+  ee  GPT

Disk /dev/mapper/cryptswap1: 38.0 GB, 38000000512 bytes

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

ANd also when I run 

root@hiram:~# parted -l
Model: ATA SAMSUNG HD204UI (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      17.4kB  60.0GB  60.0GB  ext4
 2      60.0GB  98.0GB  38.0GB


Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 38.0GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  38.0GB  38.0GB  linux-swap(v1)

Everything works fine but I would like to understand why I get :

1/ WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.
2/Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

Can It be that there is an hidden partition for the system recovery used by medion (pc manufacter) ?

Any help to learn is really appreciated!

//golia

---

### Post by grahammechanical on 2012-04-05
You can read about GPT here:

[http://en.wikipedia.org/wiki/GUID_Partition_Table]("http://en.wikipedia.org/wiki/GUID_Partition_Table")

You are getting that error message because

1) fdisk cannot work with Guid Partition Tables - I guess
2) You have this


> Model: ATA SAMSUNG HD204UI (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
**Partition Table: gpt**


If you go on that link to the heading; Unix Class Operating Systems you will see something interesting.
Regards

---

### Post by ratcheer on 2012-04-05
Install package gdisk.

Then run "sudo gdisk /dev/sda" (or, whatever device your drive is). Use ? to learn the commands - they are not exactly the same as fdisk.

Tim

---

### Post by oldfred on 2012-04-05
gpt is the newer partitioning scheme than MBR which has been the partition layout since PC hard drives in mid 1980's.

gpt is required if drive is over 2TiB or about 2TB and is recommended for any drive that does not have Windows as Windows only boots with gpt partitioning if using UEFI  not BIOS.

You should also have a bios_grub partition. The installer seems to automatically use gpt when drives are somewhat over 1TB.

Parted tools also work with gpt. I used gparted to format my gpt drives in advance.

gdisk is in repository, or you can download the newest version.
GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)


sudo parted /dev/sda unit s print
sudo sfdisk -l -uS
sudo gdisk -l /dev/sda

---

### Post by ratcheer on 2012-04-05
Thanks for the tip about the most recent version, @oldfred.

Tim

---

### Post by ratcheer on 2012-04-05
Oops. I am unable to install gptfdisk. It depends on libicu44, but that library has no installation candidate.

What else do I need to know?

Thanks,
Tim

PS - It was supposed to exist in January: [http://www.linuxsecurity.com/content/view/156649?rdf](http://www.linuxsecurity.com/content/view/156649?rdf)

---

### Post by oldfred on 2012-04-05
I thought I had installed the more current version, a while ago, but see that I just have the version from synaptic. That must have been in my previous install. 

There are notes on the gdisk install page about the changes to allow unicode make it a lot different for every system.

---

### Post by golia on 2012-04-07
Thanks a lot for the help!
If I wish to have dual boot with windows and Linux ..do I need first to partition the disk using GPT using UEFI, then install windows and then Linux?

/Golia/

---

### Post by golia on 2012-04-07
Hi,  also...how do I install gdisk in ubuntu?  cheers,

---

### Post by oldfred on 2012-04-07
If your system can boot with UEFI you should partition first. I boot with BIOS but have used gpt on my last 2 drives and just used gparted. Under device, create partition table, advanced, change from msdos(MBR) to gpt(GUID).

From Ubuntu you can download a version of gdisk from synaptic.

There was (is?) a bug in grub that it reformated the efi partition from FAT32 to FAT16. So which ever you install first, be sure to back up the files in the efi partition and reformat to FAT32 for Windows. Or if installing Windows first back up the Windows files and after Ubuntu check if it still reformats to FAT16, and save those files also and reformat back to FAT32.

Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

If you're using EFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning. You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS.


In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!


Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

---

