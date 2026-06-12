---
title: "Can't instal bootloader"
date: 2012-05-06
forum: General Help
---

### Post by Dartmaul on 2012-05-06
Hello.

I have the following problem.

I've tried to install ubuntu 11.10 and 12.04 versions and have the same problem:

If I install it booting from ubuntu CD, everything is fine until I'm getting to the very end of installation and receive a message that the bootloader cannot be set to selected partition.
This message appears every time I select any other partition.
Then I choose to complete installation without bootloader and reboot.
However I skipped the grub installation, it replaces windows bootloader and has absolutely no settings (no ubuntu and no windows entries) so I have to use windows CD to restore the boot section.
 
If I begin the installation from windows via wubi, I get an error about wrong partition right after booting in ubuntu.

I have following file system configuration:

1st disk (OCZ Revodrive (it's a PCI-E SSD) configured as a RAID0 Massive
100mb system reserved partition and 120GB Disk C with Windows and bootloader

2nd disk is RAID0 made of 4 HDD's 500gb each
Only 1 partiton on it (Disk D with files)

and 3th disk is a single HDD 250gb
Disk E with files

All partitions are formatted in NTFS.

(I shrink 20gb from C or E before trying to install ubuntu)


I also have quad-core i7 CPU that causes kernel panic if I run the installation with all 4 cores enabled (but seems that its some kind of linux specific)

I also use EasyBCD to configure boot section from windows.
Can I add my OS's to grub from windows or something?

I also cant configure the size of swap partition that I actually don't need at all (have 12GB of RAM)

---

### Post by PremC on 2012-05-11
Beware the OCZ Revodrive...

The last OS that installed on my computer from a CD without a problem was Ubuntu 10.10

My computer is very simple:
mobo:      asus P6T deluxe
cpu:          i7 920
memory:   6 gig
disk:         OCZ revodrive (original - 50 gig)
graphics card:  nvidia GeForce 9600 GT
CD:          Asus DRW-2014L1T


I have no other drives except the Revodrive, and the only OS I had was already Ubuntu
The entire drive was ext4.
I have CDs with 11.04, 11.10, 12.04 and none of them would do a clean install.
Every one of them tries to install the bootloader in sda1 and fails no matter what partition I select.
It seems like Ubutnu forgot how to work with Revodrive between 10.10 and 11.04

The only way I could manage to get 12.04 was to:
1/ install 10.10 from a CD
2/ upgrade to 11.04 online
3/ upgrade to 11.10 online
4/ upgrade to 12.04 online

It was a long afternoon...

PS. In desparation I've tried Linux Mint, but it has the same problem.

---

### Post by shazzr on 2012-05-12
I have pretty much the same setup as PremC. Only difference is that I have a 110 GB SSD RevoDrive.

I had Ubuntu running on this machine. Think it might have been 11.04, not sure though.

I have been at it for a good two days now, installing, reinstalling, tearing my hair, and installing once more, just to check that I did not do anything wrong during the installation process.

Now the installation works flawless. It is when I try to reboot and start the new, wonderfull distro that I get an error message saying that it is not able to find something to boot.

I have tried the desktop version, the server version and even the alternate version. None of them works, although I got to do some RAID setup with tha latter one. I figured that had to be a positive thing.

I have a 1 GB fat32 partition containing the booting stuff as prescribed in a tutorial I saw. Still no dice.

Do I need to downgrade and upgrade the system vie the net? Please help!

---

### Post by sudodus on 2012-05-12
Maybe I don't understand, but I'm afraid that you try to install grub into a partition instead of the beginning of the drive. What would happen if you choose **/dev/sda** (instead of /dev/sda1)?

This the the selection at the bottom of the page when installing 'something else' alias editing/selecting partitions manually.

*Edit: Maybe the partition table is not what the installer expects. Please post the output of* ```
sudo fdisk -lu
```

---

### Post by oldfred on 2012-05-12
With all those drives, you have many MBRs. Why not use manual install and install grub2 to sde's MBR? Or are some of the drives gpt?

If using RAID you may need extra drivers to see the RAID that are not in the Desktop install. Alternate or server installs include RAID drivers so you can 'see' the RAID partitions.

Lets see what sudodus's suggestion on fdisk says.

You may want to install this on liveCD. It still would not be in your install.
sudo apt-get install mdadm

---

### Post by shazzr on 2012-05-12
**This is my result:**

ubuntu@ubuntu:~$ sudo fdisk -lu 

Disk /dev/sda: 16.2 GB, 16170196480 bytes
64 heads, 32 sectors/track, 15421 cylinders, total 31582415 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006a854

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          32    31582207    15791088    c  W95 FAT32 (LBA)

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   234458623   117229311+  ee  GPT

Disk /dev/sdc: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/mapper/sil_biafbiabffaf'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/mapper/sil_biafbiabffaf: 120.0 GB, 120042815488 bytes
255 heads, 63 sectors/track, 14594 cylinders, total 234458624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

                       Device Boot      Start         End      Blocks   Id  System
/dev/mapper/sil_biafbiabffaf1               1   234458623   117229311+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/mapper/sil_biafbiabffaf1: 15.0 GB, 15000000512 bytes
255 heads, 63 sectors/track, 1823 cylinders, total 29296876 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Alignment offset: 48128 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sil_biafbiabffaf1 doesn't contain a valid partition table

Disk /dev/mapper/sil_biafbiabffaf2: 101.0 GB, 101000000512 bytes
255 heads, 63 sectors/track, 12279 cylinders, total 197265626 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Alignment offset: 58368 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sil_biafbiabffaf2 doesn't contain a valid partition table

Disk /dev/mapper/sil_biafbiabffaf3: 3000 MB, 3000000512 bytes
255 heads, 63 sectors/track, 364 cylinders, total 5859376 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Alignment offset: 12288 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sil_biafbiabffaf3 doesn't contain a valid partition table

Disk /dev/mapper/sil_biafbiabffaf4: 1042 MB, 1042779648 bytes
255 heads, 63 sectors/track, 126 cylinders, total 2036679 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Alignment offset: 53248 bytes
Disk identifier: 0x00000000

                         Device Boot      Start         End      Blocks   Id  System

---

### Post by oldfred on 2012-05-12
Fdisk does not work with gpt drives. It seems your system promotes the USB flash to sda.

Which device did you want to install to. If not in the RAID and gpt and booting with BIOS you need a small bios_grub partition for grub to install correctly.

To see gpt partitions change sda to your drive(s):

sudo parted -l
or
sudo parted /dev/sda unit s print
or
sudo gdisk -l /dev/sda

Should look like this:

```
Model: ATA SSD G2 series 64 (scsi)
Disk /dev/sdd: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  316MB   315MB   fat32                 boot
 2      316MB   317MB   1049kB                        bios_grub
 3      317MB   30.2GB  29.9GB  ext4         04
 4      30.2GB  60.0GB  29.9GB  ext4         Quantal

fred@fred-Precise:~$ sudo gdisk -l /dev/sdd
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdd: 117231408 sectors, 55.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 85A657E7-D379-4592-B060-E8EA09953D80
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 117231374
Partitions will be aligned on 2048-sector boundaries
Total free space is 3821 sectors (1.9 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          616447   300.0 MiB   EF00  
   2          616448          618495   1024.0 KiB  EF02  
   3          618496        58925055   27.8 GiB    0700  04
   4        58925056       117229567   27.8 GiB    0700  Quantal
fred@fred-Precise:~$ 


```

---

### Post by shazzr on 2012-05-12
> **oldfred said:**
> Fdisk does not work with gpt drives. It seems your system promotes the USB flash to sda.

Yes, it does.

I wanted to install it to the SSD drive that I got. I have tried with bios_grub and boot flags on small partitions earlier today. No dice.

Downloading 11.04 now. Going to try to install that, and maybe do a upgrade from there. Not a perfect solution, but maybe a solution that works.

Just can't get my head around the SSD/GPT-thingy... :s

---

### Post by oldfred on 2012-05-12
I just used gparted to create the partitions I showed above, and used manual install so I could choose to put grub2's boot loader into the MBR of sdd or the SSD. Grub likes to default to sda.

I still have 11.10 (soon to be 12.10) in one partition and 12.04 from the alpha in the other.

Is your system new enough to also be UEFI?

---

### Post by shazzr on 2012-05-12
> **oldfred said:**
> Is your system new enough to also be UEFI?
Yes. And that might also have something to do with the troubles? I have a Asus P8P67 Deluxe motherboard.

---

### Post by oldfred on 2012-05-12
You have to decide if you want UEFI or the older BIOS. Many do not understand UEFI and each vendor has done it a bit different even though it is supposed to be a standard.

When you configure drive I normally suggest both an efi partition which must be first and 200 or 300MB formated FAT32 with boot flag (in gparted), and a bios_grub partition 1MB not formated and with bios_grub flag. Then whatever partitions you want for the system(s) you want to install. You actually do not need both but partitions are small and it gives the  options to install either way from a partition stand point.

In Ubuntu when you boot from UEFI, you should see two different boot options. One is UEFI and should install using UEFI and the efi partition. The other option is the older BIOS/MBR install which will use the bios_grub.

---

### Post by shazzr on 2012-05-13
Ok. So I'm on the last leg of the installation process now. I did what oldfred described, and so I have the following partitions now:

ubuntu@ubuntu:~$ sudo fdisk -ls

Disk /dev/sda: 16.2 GB, 16170196480 bytes
64 heads, 32 sectors/track, 15421 cylinders, total 31582415 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e8fda

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          32    31582207    15791088    c  W95 FAT32 (LBA)

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/mapper/sil_biafbiddeice: 120.0 GB, 120042815488 bytes
255 heads, 63 sectors/track, 14594 cylinders, total 234458624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x0007f66c

                       Device Boot      Start         End      Blocks   Id  System
/dev/mapper/sil_biafbiddeice1   *          63      610469      305203+   b  W95 FAT32
Partition 1 does not start on physical sector boundary.
/dev/mapper/sil_biafbiddeice2          612352      614399        1024   83  Linux
/dev/mapper/sil_biafbiddeice3          614400   234457087   116921344    5  Extended
/dev/mapper/sil_biafbiddeice5          616448    31336447    15360000   83  Linux
/dev/mapper/sil_biafbiddeice6        31338496   232409087   100535296   83  Linux
/dev/mapper/sil_biafbiddeice7       232411136   234457087     1022976   82  Linux swap / Solaris

Disk /dev/mapper/sil_biafbiddeice1: 312 MB, 312528384 bytes
255 heads, 63 sectors/track, 37 cylinders, total 610407 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Alignment offset: 33280 bytes
Disk identifier: 0x00000000

                         Device Boot      Start         End      Blocks   Id  System

Disk /dev/mapper/sil_biafbiddeice2: 1 MB, 1048576 bytes
255 heads, 63 sectors/track, 0 cylinders, total 2048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sil_biafbiddeice2 doesn't contain a valid partition table
fdisk: unable to seek on /dev/mapper/sil_biafbiddeice3: Invalid argument

-----------------

I told the installer to install the bootloader on the /dev/mapper/sil_biafbiddeice1 partition. Now I got the message saying it is time to reboot. Just crossing my fingers!

---

### Post by shazzr on 2012-05-13
Follow up: yet another fail to boot.

I get no errors during install (did the alternate-iso version this time, due to RAID), but when I reboot my computer says:

*Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key*

I have changed settings in the UEFI/BIOS to pretty much every option avaliable. Every time I get the message above.

Such a downer. Got this awesome computer, and I can no longer use Ubuntu on it. :(

---

### Post by ewoodlief on 2012-07-13
Wow, this isn't that hard guys...

> **shazzr said:**
> I told the installer to install the bootloader on the /dev/mapper/sil_biafbiddeice1

Almost, just take off the number. Pop in 12.04, do the install as normal, and set the bootloader to install at  /dev/mapper/sil_biafbiddeice. That's it.

---

