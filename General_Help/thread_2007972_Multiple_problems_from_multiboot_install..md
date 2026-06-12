---
title: "Multiple problems from multiboot install."
date: 2012-06-21
forum: General Help
---

### Post by Quenepas on 2012-06-21
Posted this on Mac forum but here might help as well... 

Hello, Im new here and to Linux as well so I'll try to be as specific as I can. Any type of help is greatly appreciated .

Just followed [THIS]("http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required") guide to triple boot OSX, Win7 and Ubuntu. Since I already had Bootcam with Windows, the guide asked me to create 2 additional partitions, 1 for Linux and 1 for Linux Swap. During installation it seems like the swap file needed was just about 1.5GB HDD space. Ubuntu Disk Utility shows 5 partitions (in order),

EFI System Partition 210MB FAT32
OSX 254GB HFS+
"Linux" (as renamed during OSX format) 51GB FAT32 /dev/sda3 not mounted
Linux 51GB FAT32 ext4 v1.0 Mounted at L
Swap Space 1.6GB /dev/sda6
and finally...
BOOTCAMP 141GB

Ubuntu seems to work, OSX seems to work and Windows doesnt seem to boot thru rEFIt... boots back to Ubuntu :/ before booting it comes up with GNU menu (which I dont know). 

So afaik My problems are:

1) Windows 7 wont boot thru rEFIt.

When choosing Windows Vista (dunno why, I have Win7) Windows boot Manager gives error: File \boot\BCD Status:0xc0000225 Info An error ocurred while attempting to read the boot configuration data. Enter=continue ESC=Exit. I press continue and it does nothing. It asks for the installation disc and attempt a repair but I dont think this would be solved that easily.

Checking Disk Utility on OSX shows 8 partitions including osx... this doesnt look good :/

2) When Ubuntu start it rapidly tell about an internal error : "/usr/share/apport/apport-gpu-error-intel.py"

3) the graphic card seems to be unknown within Ubuntu.

I have a black Macbook... Thanks for your time!! ):P

---

### Post by Quenepas on 2012-06-22
alright, been working on this since last post and looks like the Ubuntu installer probably autodetected a recovery partition and set up GRUB (the bootloader) to boot to that instead of the proper Windows partition.

so I did a ```
sudo os-prober; sudo update-grub
```

Aaaaaand it didnt help... so I did a 

```
sudo fdisk -l
```

it presented me with the following info:

/dev/sda1 start: 1 End: 409639 Blocks: 204819+ Id: ee System: GPT
/dev/sda2 start: 409640 End: 496355775 Blocks: 247973068 Id: af System: HFS/HFS+
/dev/sda3 start: 496617920 End: 596472847 Blocks: 49927464 Id: b System: W95 FAT32
/dev/sda4 * start: 599539200 End: 698798991 Blocks: 49629896 Id: 83 System: Linux

And thats when the command ends... So after that I fireup Disk Utility again and it shows that the long lost BOOTCAMP is stored in /dev/sda5 not mentioned by the terminal command...

Disk Utility "Check Filesystem" doesnt fix it either so... 

If anyone wanna throw in their 2 cents that would be awesome! Thanks! :popcorn:

---

### Post by Quenepas on 2012-06-22
Partition inspector on oSX gives out this info:

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    496355775  Mac OS X HFS+
 3      496617920    596472847  Basic Data
 4      599539200    698798991  Basic Data
 5      701845504    976771071  Basic Data
 6      698798992    701843913  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    496355775  af  Mac OS X HFS+
 3      496617920    596472847  0b  FAT32 (CHS)
 4 *    599539200    698798991  83  Linux

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 496617920:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 0b  FAT32 (CHS)

Partition at LBA 599539200:
 Boot Code: GRUB
 File System: ext4
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux, active

Partition at LBA 701845504:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 5, type Basic Data

Partition at LBA 698798992:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 6, type Linux Swap

---

### Post by Quenepas on 2012-06-22
Followed [THIS]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation") guide here and rebooted to the rEFIt menu and selected the “partition tool”. rEFIt asked if you would like to sync your partition tables. I hit y.

Now it freezes in the rEFIt windows logo and windows wont boot :frown:

---

### Post by Quenepas on 2012-06-22
Hory Shet! Followed [THIS]("http://ubuntuforums.org/showthread.php?t=1908210") guide and look and behold... TRIPLE BOOTING DRESSAGE! :guitar:

Alright, now I have to fix one partition I believe is not being used... On the Lifehacker tutorial, it said to create 2 partitions... SO I did... 2 50GB partitions... So it seemed that you just needed a big chunk of FAT32 formated partition (in addition to you OSX and Win7 partitions) and let the Ubuntu installer apply whatever partitions it needed. 

Now I deleted the unneeded partition (Disk utility shows the Ubuntu partition as DISK0S4 and the swap as Linux Swap) and have an empty space I want to allocate to OSX. I boot to PSX and go to Disk Utility and drag the square to allocate the empty space and error occurs: Partition failed with the error: MediaKit reports no such partition \\:D/

What could possibly be?

---

### Post by Quenepas on 2012-06-22
Oh and the error about the GPU, [HERE]("https://launchpad.net/ubuntu/lucid/i386/xserver-xorg-video-intel/") are some files to fix it. I installed one suggested elsewhere and it didnt fix the issue. I installed the latest on top and the errors havent reappeared afaik.

After messing with the partition to get it merged I installed iPartition for Mac as suggested elsewhere but that app DOES NOT work. The other alternative is to boot from OSX SL cd to get it fixed. iPartition said the operation could not be done from the partition being currently in use.... I'll go to sleep now :-&

---

