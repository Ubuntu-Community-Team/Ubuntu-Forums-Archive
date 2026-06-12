---
title: "Grub rescue!? how to remove? Pleas help!"
date: 2012-03-14
forum: General Help
---

### Post by linktopower on 2012-03-14
Hello...

I had ubuntu 11.04 installed on another complete hard drive thats not even connected with my main hard drive. see I Just unhooked my Windows vista hard drive. and put another drive to run ubuntu. where I could run with out messing up my windows.
But it seems After taking the ubuntu hard drive out and put the windows hard drive back in I hit this problem..

Grub rescue>

Now his confuses me My windows drive wasn't even hooked up when I had ubuntu in my computer...

The question is how do I fix it where my Computer will stop doing this and boot my windows drive up normally?
Please anyone help :(

---

### Post by linktopower on 2012-03-14
ok I'm sorry about this double post but I need help now :( please...

---

### Post by Spewed on 2012-03-14
> **linktopower said:**
> Hello...

I had ubuntu 11.04 installed on another complete hard drive thats not even connected with my main hard drive. see I Just unhooked my Windows vista hard drive. and put another drive to run ubuntu. where I could run with out messing up my windows.
But it seems After taking the ubuntu hard drive out and put the windows hard drive back in I hit this problem..

Grub rescue>

Now his confuses me My windows drive wasn't even hooked up when I had ubuntu in my computer...

The question is how do I fix it where my Computer will stop doing this and boot my windows drive up normally?
Please anyone help :(

Hey man, sorry no one has responded to you sooner. I just got home from a date with my fiancee. So anyway, I've had this issue each time I've installed Ubuntu on my system. The Grub Rescue situation should be relatively easy to fix.


First things first, you need a Ubuntu LIVE CD for this fix that I'm recommending. 
Go ahead and insert that or your USB, whatever you have it installed on. Boot into your bios and select either your CD Drive or your USB Stick. 

If you have a Ubuntu Live CD, or USB stick go ahead and boot into that. If you don't know what that is it's the CD you used to install Ubuntu, there should be an option on it that says "Try Ubuntu" Select that option.

Once you're in there open up your terminal using Ctrl\alt\T. From there type in the following commands in the exact order. 

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair-ubuntu

Just copy and paste each command individually to ensure accuracy and lessen any chance of error. 

Hope this helps, if not get back to me and let know why not.

---

### Post by YannBuntu on 2012-03-14
Spewed's suggestion to use Boot-repair is good. Just few additional details:
- the package name is now "boot-repair", not "boot-repair-ubuntu" (see: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) )
- your problem arose because GRUB has been installed in your Windows disk's MBR, this means you have updated Ubuntu without disconnecting your Windows disk.
- if you want to be able to use Windows without connecting the Ubuntu disk, please follow these steps:
1) Disconnect the Ubuntu disk, and connect the Windows disk
2) Run Boot-Repair from live-CD or live-USB (see [https://help.ubuntu.com/community/Boot-Repair#A1st_option_:_get_a_CD_including_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#A1st_option_:_get_a_CD_including_Boot-Repair) ), then click the "Recommended repair" button. This will remove GRUB from Windows disk's MBR. **Note the URL that will appear, and indicate it to me.** 
Reboot the PC (without any CD nor live-USB) and check that it boots directly to Windows. 
3) Connect the Ubuntu disk
4) Reboot and check if you have access to Ubuntu. **If no**, run Boot-Repair again, but this time click on "Advanced options", go to the "GRUB location" tab, tick the "sdx is a removable disk" option (x may be a or b), apply, and **indicate the new URL that will appear.**

Regards

---

### Post by linktopower on 2012-03-14
> **Spewed said:**
> Hey man, sorry no one has responded to you sooner. I just got home from a date with my fiancee. So anyway, I've had this issue each time I've installed Ubuntu on my system. The Grub Rescue situation should be relatively easy to fix.


First things first, you need a Ubuntu LIVE CD for this fix that I'm recommending. 
Go ahead and insert that or your USB, whatever you have it installed on. Boot into your bios and select either your CD Drive or your USB Stick. 

If you have a Ubuntu Live CD, or USB stick go ahead and boot into that. If you don't know what that is it's the CD you used to install Ubuntu, there should be an option on it that says "Try Ubuntu" Select that option.

Once you're in there open up your terminal using Ctrl\alt\T. From there type in the following commands in the exact order. 

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair-ubuntu

Just copy and paste each command individually to ensure accuracy and lessen any chance of error. 

Hope this helps, if not get back to me and let know why not.
Nope No dice. its still 
saying Error invalided filesystem 
Grub rescue>
> **YannBuntu said:**
> Spewed's suggestion to use Boot-repair is good. Just few additional details:
- the package name is now "boot-repair", not "boot-repair-ubuntu" (see: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) )
- **your problem arose because GRUB has been installed in your Windows disk's MBR, this means you have updated Ubuntu without disconnecting your Windows disk.**
- if you want to be able to use Windows without connecting the Ubuntu disk, please follow these steps:
1) Disconnect the Ubuntu disk, and connect the Windows disk
2) Run Boot-Repair from live-CD or live-USB (see [https://help.ubuntu.com/community/Boot-Repair#A1st_option_:_get_a_CD_including_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#A1st_option_:_get_a_CD_including_Boot-Repair) ), then click the "Recommended repair" button. This will remove GRUB from Windows disk's MBR. **Note the URL that will appear, and indicate it to me.** 
Reboot the PC (without any CD nor live-USB) and check that it boots directly to Windows. 
3) Connect the Ubuntu disk
4) Reboot and check if you have access to Ubuntu. **If no**, run Boot-Repair again, but this time click on "Advanced options", go to the "GRUB location" tab, tick the "sdx is a removable disk" option (x may be a or b), apply, and **indicate the new URL that will appear.**

Regards
But thats the thing...I didn't even have my windows hard drive in my computer...
Is it possable that grub is in my bios??

---

### Post by YannBuntu on 2012-03-14
I think it's not possible, even with new EFI bios.

---

### Post by linktopower on 2012-03-14
Okay any sugestion on what to do?

And on another note I can still boot my windows by pressing F12 on the bios then selecting boot off hard drive.

EDIT: Hm...Maybe its still in the ram memory? Just guessing at this point...

>                  Boot Info Script 0.60-git      [23 Feb 2012]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   156,296,384   156,296,322   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   156,301,311   156,299,264   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        01CCF0F2A78EB080                       ntfs       Western Digital Master
/dev/sdb1        92A4BC10A4BBF537                       ntfs       Western Digital Slave
/dev/sdc         F658-405E                              vfat       CRUZER 15GB

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc         /media/CRUZER 15GB       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

ADDITIONAL INFORMATION :
**************** log of boot-repair 2012-03-14__09h21 ****************
boot-repair version : 3.16-0ppa10~natty
boot-sav version : 3.17-0ppa20~natty
/usr/share/boot-sav/gui-update.sh: line 31: hash: glade2script: not found
glade2script-gtk2 version : 0.0.1-0ppa4~natty
internet: no-internet
LIVESESSION is : yes (Ubuntu 11.04 , natty , Ubuntu , i686  )
sdc has unknown type. Please report this message to [email]yannubuntu@gmail.com[/email]
BYTES_BEFORE_PART[1] (sda) = 63 sectors * 512 bytes = 32256 bytes.
BYTES_BEFORE_PART[2] (sdb) = 2048 sectors * 512 bytes = 1048576 bytes.

OSPROBER:
/dev/sda1:Windows Vista (loader):Windows:chain

BLKID:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="Western Digital Master" UUID="01CCF0F2A78EB080" TYPE="ntfs"
/dev/sdb1: LABEL="Western Digital Slave" UUID="92A4BC10A4BBF537" TYPE="ntfs"
/dev/sdc: LABEL="CRUZER 15GB" UUID="F658-405E" TYPE="vfat"

1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.
Total of 1 OS detected on sda disk.
TABLE_TYPE of sda is MSDos
TABLE_TYPE of sdb is MSDos
sda1 : sda, not-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda1, with-os, no-gpt, notEFItable, no-fstab.
sdb1 : sdb, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sdb1, no-os, no-gpt, notEFItable, no-fstab.
sdc : sda, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /media/CRUZER 15GB, no-os, no-gpt, notEFItable, no-fstab.

PARTED:

Model: ATA WDC WD800BB-22JH (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  80.0GB  80.0GB  primary  ntfs         boot


Model: ATA WDC WD800BB-00CA (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  80.0GB  80.0GB  primary  ntfs


Model: SanDisk Cruzer (scsi)
Disk /dev/sdc: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
1      0.00B  16.0GB  16.0GB  fat32



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


MOUNT:
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc on /media/CRUZER 15GB type vfat (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


/sys/block/sda:  alignment_offset bdi capability dev device discard_alignment ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device discard_alignment ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdd:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdg:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev:  agpgart autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency dgcdcp0 dgcdcp1 dgcdcp2 dgcdcp3 dgcdcp4 dgcdcp5 dgcdcp6 dgcdcp7 dgcdiag0 dgcdiag1 dgcdiag2 dgcdiag3 dgcdiag4 dgcdiag5 dgcdiag6 dgcdiag7 dgcdiagdmp disk dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hpet input kmsg log lp0 mapper mcelog mem modem net network_latency network_throughput null oldmem parport0 pktcdvd port ppp psaux ptmx pts random rfkill rtc rtc0 scd0 sda sda1 sdb sdb1 sdc sdd sde sdf sdg serial sg0 sg1 sg2 sg3 sg4 sg5 sg6 sg7 shm snapshot snd sr0 stderr stdin stdout uinput urandom usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 vga_arbiter zero
/dev/mapper:  control

DF:

Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    501M  129M  372M  26% /
none      devtmpfs    494M  736K  493M   1% /dev
/dev/sr0   iso9660    686M  686M     0 100% /cdrom
/dev/loop0
squashfs    658M  658M     0 100% /rofs
none         tmpfs    501M  284K  500M   1% /dev/shm
tmpfs        tmpfs    501M   40K  501M   1% /tmp
none         tmpfs    501M  112K  500M   1% /var/run
none         tmpfs    501M  8.0K  501M   1% /var/lock
/dev/sdc      vfat     15G  416M   15G   3% /media/CRUZER 15GB
/dev/sda1  fuseblk     75G   15G   60G  20% /mnt/boot-sav/sda1
/dev/sdb1  fuseblk     75G   21G   54G  29% /mnt/boot-sav/sdb1

FDISK:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3b011949

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156296384    78148161    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005f1a3

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   156301311    78149632    7  HPFS/NTFS

Disk /dev/sdc: 16.0 GB, 16008609792 bytes
64 heads, 32 sectors/track, 15267 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?   778135908  1919645538   570754815+  72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?   168689522  2104717761   968014120   65  Novell Netware 386
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?  1869881465  3805909656   968014096   79  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?  2885681152  2885736650       27749+   d  Unknown
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order



************************Before mainwindow
FSCK_ACTION no PASTEBIN_ACTION yes
recommendedrepair, restore, REINSTALL_POSSIBLE no PURGE_POSSIBLE
UNHIDEBOOT_ACTION yes (10s), noflag (sda1)
PART_TO_REINSTALL_GRUB , PART_TO_REINSTALL_GRUB_PURGE , FORCE_GRUB  () REMOVABLEDISK
USE_SEPARATEBOOTPART  ()  ()
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) ( )
internet: no-internet

************************Actions
FSCK_ACTION no PASTEBIN_ACTION yes
customrepair, restore, REINSTALL_POSSIBLE no PURGE_POSSIBLE
UNHIDEBOOT_ACTION yes (10s), noflag (sda1)
PART_TO_REINSTALL_GRUB , PART_TO_REINSTALL_GRUB_PURGE , FORCE_GRUB  () REMOVABLEDISK
USE_SEPARATEBOOTPART  ()  ()
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) (sda 1)
Will restore the MBR_TO_RESTORE : sda (mbr) into sda
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 records in
0+1 records out
bootflag_action sda1 (=sda1)
parted /dev/sda set 2 boot off

                                                                          
Error: Partition doesn't exist.
parted /dev/sda set 3 boot off

                                                                          
Error: Partition doesn't exist.
parted /dev/sda set 4 boot off

                                                                          
Error: Partition doesn't exist.
parted /dev/sda set 1 boot on

                                                                          
Information: You may need to update /etc/fstab.

internet: connected
pastebinit  packages needed
internet: connected
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Package 'pastebinit' has no installation candidate
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Package 'pastebinit' has no installation candidate
Could not install pastebinit

theres a boot info txt that boot repair made... will this help any one?
And from what I gather my windows hard drive is /dev/sda.
Hope this will shed some light.

---

### Post by YannBuntu on 2012-03-14
You have 2 disks:
- sda is 80Go and contains Windows
- sdb is also 80Go and contains no OS

Is guess you see GRUB because your BIOS tries to boot on sdb.
Please setup your BIOS so that it boots on sda. Then reboot, and check if you can access Windows.

---

### Post by linktopower on 2012-03-14
Oh!! I got it now!. It was something so simple...god I'm dumb I cannot believe i forgot to set the boot priority D:
Thanks guys for all the help :)

at least I fixed it now :) Thanks so much Thank you thank you thank you!

---

