---
title: "Windows partition unmounted, stuck in grub rescue!"
date: 2012-10-07
forum: General Help
---

### Post by AndyOpie150 on 2012-10-07
I Accidentally unmounted Windows partition thinking I had only unmounted the Linux partitions inside of the Windows partition while trying to install a Linux distro( I managed to boot into my Windows OS from the linux). To make matters worse after doing some re-partitioning to even out the partition size's in my Windows OS I lost the boot.img and ended up in grub rescue on a reboot. I already knew I would loose the boot.img and was prepared with a boot repair CD which also has a live linux distro (which is how I'm able to start this thread).
I tried running the boot repair CD and It tells me there is no OS detected so it cannot repair the boot img, which is how I figured out my Windows partition is unmounted.

Is there a way to mount the Windows partition from the Live Linux distro and therefore, be able to fix the boot image?

2003 SONY VAIO PVC V200G Desktop with 120 GB hard drive with 1GB of RAM with a intel pentium 4 running at 2.80 GHz.
Inside the Windows partition I have a Windows OS partition at 30GB, a 27GB unallocated partition (this was fixing to have a Bohdi linux distro installed onto it), a 27GB linux Mint distro partition, a 30GB Kubuntu partition, and a 990MB swapp partition (was trying to figure out which distro I liked the best and had them all installed for comparission).

```
root@debian:/home/user# cat /proc/partitions
major minor  #blocks  name

   8        0  117220824 sda
   8        1   31744405 sda1
   8       16   15667200 sdb
   7        0     327416 loop0

root@debian:/home/user# ntfs-3g /dev/sda /mnt/windows
NTFS signature is missing.
Failed to mount '/dev/sda': Invalid argument
The device '/dev/sda' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


root@debian:/home/user# ntfs-3g /dev/sda1 /mnt/windows
Failed to read last sector (63502328): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
root@debian:/home/user# 



```

---

### Post by AndyOpie150 on 2012-10-08
```
user@debian:~$ sudo blkid
/dev/sda1: UUID="01CDA32221FB5DC00" TYPE="ntfs"
/dev/loop0: TYPE="squashfs"
```

Any suggestions on how to get my XP and Kubuntu up and running would be greatly appreciated.

---

### Post by critin on 2012-10-08
> Inside the Windows partition I have a Windows OS partition at 30GB, a  27GB unallocated partition (this was fixing to have a Bohdi linux distro  installed onto it), a 27GB linux Mint distro partition, a 30GB Kubuntu  partition, and a 990MB swapp partition

Are you using Wubi for all of these?

Run the boot repair again and run the report option, post the report url.
Also check the disk utility in the live cd to see if it sees it.  Gparted too.

---

### Post by AndyOpie150 on 2012-10-08
Don't have desktop hooked to router.  Had to transfer report to phone, then copy to clipboard. This is pretty long ```
 Boot Info Script 0.61.full + Boot-Repair extra info [Boot-Info August 2nd 2012]

============================= Boot Info Summary: ===============================

=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of the same hard drive for core.img. core.img is at this location and looks for (,msdos7)/boot/grub on this drive.

sda1: __________________________________________________________________________

File system: ntfs Boot sector type: Windows XP: NTFS Boot sector info: According to the info in the boot sector, sda1 has 63502328 sectors, but according to the info from fdisk, it has 63488809 sectors. Mounting failed: Failed to read last sector (63502328): Invalid argument HINTS: Either the volume is a RAID/LDM but it wasn't setup yet, or it cw Xx xwas not setup correctly (e.g. by not using mdadm --build ...), or a wrong device is tried to be mounted, or the partition table is corrupt (partition is smaller than NTFS), or the NTFS boot sector is corrupt (NTFS size is not valid). Failed to mount '/dev/sda1': Invalid argument The device '/dev/sda1' doesn't seem to have a valid NTFS. Maybe the wrong device is used? Or the whole disk instead of a partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around? Failed to read last sector (63502328): Invalid argument HINTS: Either the volume is a RAID/LDM but it wasn't setup yet, or it was not setup correctly (e.g. by not using mdadm --build ...), or a wrong device is tried to be mounted, or the partition table is corrupt (partition is smaller than NTFS), or the NTFS boot sector is corrupt (NTFS size is not valid). Failed to mount '/dev/sda1': Invalid argument The device '/dev/sda1' doesn't seem to have a valid NTFS. Maybe the wrong device is used? Or the whole disk instead of a partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

sdb: ___________________________________________________________________________

File system: vfat Boot sector type: SYSLINUX 4.04 2011-04-18 Boot sector info: Syslinux looks at sector 1062800 of /dev/sdb for its second stage. SYSLINUX is installed in the directory. No errors found in the Boot Parameter Block. Operating System: Boot files: /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes 255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sda1 * 70 63,488,879 63,488,810 7 NTFS / exFAT / HPFS

"blkid" output: ________________________________________________________________

Device UUID TYPE LABEL

/dev/loop0 squashfs /dev/sda1 01CDA3221FB5DC00 ntfs /dev/sdb D4F4-0F3C vfat MYLINUXLIVE

================================ Mount points: =================================

Device Mount_Point Type Options

/dev/sdb /media/MYLINUXLIVE vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush) /dev/sr0 /live/image iso9660 (ro,noatime)

========================== sdb/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------default vesamenu.c32 prompt 0 timeout 300

menu title Bodhi Linux menu background splash.png menu color title 1;37;44 #c0ffffff #00000000 std

label live menu label live - boot the Live System kernel /casper/vmlinuz append file=/cdrom/preseed/custom.seed boot=casper initrd=/casper/initrd.gz quiet splash --

label xforcevesa menu label xforcevesa - boot Live in Generic safe graphics mode kernel /casper/vmlinuz append file=/cdrom/preseed/custom.seed boot=casper xforcevesa initrd=/casper/initrd.gz quiet splash --

label nomodeset menu label nomodeset - boot Live in ATI safe graphics mode kernel /casper/vmlinuz append file=/cdrom/preseed/custom.seed boot=casper initrd=/casper/initrd.gz nomodeset quiet splash --

label ramboot menu label Boot into RAM kernel /casper/vmlinuz append file=/cdrom/preseed/custom.seed boot=casper initrd=/casper/initrd.gz quiet splash toram --

label hd menu label hd - boot the first hard disk localboot 0x80 append -

--------------------------------------------------------------------------------

================== sdb: Location of files loaded by Syslinux: ==================

GiB - GB File Fragment(s)

?? = ?? ldlinux.sys 1 ?? = ?? syslinux/syslinux.cfg 1 ?? = ?? syslinux/vesamenu.c32 1

=============== sdb: Version of COM32(R) files used by Syslinux: ===============

syslinux/vesamenu.c32 : COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

File descriptor 7 (pipe:[5830]) leaked on lvscan invocation. Parent PID 7731: bash File descriptor 8 (pipe:[5830]) leaked on lvscan invocation. Parent PID 7731: bash No volume groups found mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION : =================== log of boot-repair 2012-10-08__01h17 =================== boot-repair version : 3.18-0ppa52~lucid boot-sav version : 3.192-0ppa24~lucid glade2script-gtk2 version : 0.0.1-0ppa4~lucid boot-sav-nonfree version : 3.18-0ppa14~lucid Please connect internet. Then close this window. /usr/share/boot-sav/gui-update.sh: line 328: add-apt-repository: command not found /usr/share/boot-sav/gui-update.sh: line 328: add-apt-repository: command not found deb http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu lucid main /usr/share/boot-sav/gui-update.sh: line 328: add-apt-repository: command not found /usr/share/boot-sav/gui-update.sh: line 328: add-apt-repository: command not found deb http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu lucid main W: Failed to fetch http://cdn.debian.net/debian/dists/squeeze/Release.gpg Could not resolve 'cdn.debian.net'

W: Failed to fetch http://cdn.debian.net/debian/dists/squeeze/main/i18n/Translation-en.bz2 Could not resolve 'cdn.debian.net'

W: Failed to fetch http://cdn.debian.net/debian/dists/squeeze/main/i18n/Translation-en_US.bz2 Could not resolve 'cdn.debian.net'

W: Failed to fetch http://security.debian.org/dists/squeeze/updates/Release.gpg Could not resolve 'security.debian.org'

W: Failed to fetch http://security.debian.org/dists/squeeze/updates/main/i18n/Translation-en.bz2 Could not resolve 'security.debian.org'

W: Failed to fetch http://security.debian.org/dists/squeeze/updates/main/i18n/Translation-en_US.bz2 Could not resolve 'security.debian.org'

W: Failed to fetch http://cdn.debian.net/debian/dists/squeeze-updates/Release.gpg Could not resolve 'cdn.debian.net'

W: Failed to fetch http://cdn.debian.net/debian/dists/squeeze-updates/main/i18n/Translation-en.bz2 Could not resolve 'cdn.debian.net'

W: Failed to fetch http://cdn.debian.net/debian/dists/squeeze-updates/main/i18n/Translation-en_US.bz2 Could not resolve 'cdn.debian.net'

W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/Release.gpg Could not resolve 'ppa.launchpad.net'

W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/main/i18n/Translation-en.bz2 Could not resolve 'ppa.launchpad.net'

W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2 Could not resolve 'ppa.launchpad.net'

W: Failed to fetch http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/Release.gpg Could not resolve 'ppa.launchpad.net'

W: Failed to fetch http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/main/i18n/Translation-en.bz2 Could not resolve 'ppa.launchpad.net'

W: Failed to fetch http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2 Could not resolve 'ppa.launchpad.net'

W: Some index files failed to download, they have been ignored, or old ones used instead.

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 55 not upgraded. WARNING: The following packages cannot be authenticated! os-uninstaller Err http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/lucid/main os-uninstaller all 3.18-0ppa12~lucid Could not resolve 'ppa.launchpad.net' Failed to fetch http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/pool/main/o/os-uninstaller/os-uninstaller_3.18-0ppa12~lucid_all.deb Could not resolve 'ppa.launchpad.net' E: Some files failed to download

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 55 not upgraded. WARNING: The following packages cannot be authenticated! boot-repair Err http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ lucid/main boot-repair all 3.18-0ppa52~lucid Could not resolve 'ppa.launchpad.net' Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/pool/main/b/boot-repair/boot-repair_3.18-0ppa52~lucid_all.deb Could not resolve 'ppa.launchpad.net' E: Some files failed to download File descriptor 7 (pipe:[5830]) leaked on lvs invocation. Parent PID 3822: /bin/sh File descriptor 8 (pipe:[5830]) leaked on lvs invocation. Parent PID 3822: /bin/sh No volume groups found boot-repair is executed in live-session (Boot-Repair-Disk 18.07.2012, squeeze, Debian, i686) CPU op-mode(s): 32-bit sdb may have broken partition table. Failed to read last sector (63502328): Invalid argument HINTS: Either the volume is a RAID/LDM but it wasn't setup yet, or it was not setup correctly (e.g. by not using mdadm --build ...), or a wrong device is tried to be mounted, or the partition table is corrupt (partition is smaller than NTFS), or the NTFS boot sector is corrupt (NTFS size is not valid). Failed to mount '/dev/sda1': Invalid argument The device '/dev/sda1' doesn't seem to have a valid NTFS. Maybe the wrong device is used? Or the whole disk instead of a partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

=================== os-prober:

=================== blkid: /dev/sda1: UUID="01CDA3221FB5DC00" TYPE="ntfs" /dev/loop0: TYPE="squashfs" /dev/sdb: LABEL="MYLINUXLIVE" UUID="D4F4-0F3C" TYPE="vfat"

Failed to read last sector (63502328): Invalid argument HINTS: Either the volume is a RAID/LDM but it wasn't setup yet, or it was not setup correctly (e.g. by not using mdadm --build ...), or a wrong device is tried to be mounted, or the partition table is corrupt (partition is smaller than NTFS), or the NTFS boot sector is corrupt (NTFS size is not valid). Failed to mount '/dev/sda1': Invalid argument The device '/dev/sda1' doesn't seem to have a valid NTFS. Maybe the wrong device is used? Or the whole disk instead of a partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

=================== dmesg | grep EFI : This live-session is not EFI-compatible.

=================== PARTITIONS & DISKS: sda1 : sda, not-sepboot, no-grubenv nogrub, no-docgrub, no-update-grub, 32, no-boot, no-os, not--efi--part, part-has-no-fstab, part-has-no-fstab, no-nt, no-winload, no-recov-nor-hid, no-bmgr, no-grldr, no-b-bcd, nopakmgr, nogrubinstall, no---usr, part-has-no-fstab, not-sep-usr, standard, not-far, /mnt/boot-sav/sda1.

sda : MSDos, not-GPT, BIOSboot-not-needed, has-no-EFIpart, not-usb, 70 sectors * 512 bytes

=================== parted -l:

Model: ATA ST3120022A (scsi) Disk /dev/sda: 120GB Sector size (logical/physical): 512B/512B Partition Table: msdos

Number Start End Size Type File system Flags 1 35.8kB 32.5GB 32.5GB primary ntfs boot

Model: (scsi) Disk /dev/sdb: 16.0GB Sector size (logical/physical): 512B/512B Partition Table: loop

Number Start End Size File system Flags 1 0.00B 16.0GB 16.0GB fat32

Warning: Unable to open /dev/sr0 read-write (Read-only file system). /dev/sr0 has been opened read-only.

Error: /dev/sr0: unrecognised disk label

=================== mount: aufs on / type aufs (rw) tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755) proc on /proc type proc (rw,noexec,nosuid,nodev) sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) udev on /dev type tmpfs (rw,mode=0755) tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev) devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620) /dev/sr0 on /live/image type iso9660 (ro,noatime) tmpfs on /live/cow type tmpfs (rw,noatime,mode=755) tmpfs on /live type tmpfs (rw,relatime) tmpfs on /tmp type tmpfs (rw,nosuid,nodev) fusectl on /sys/fs/fuse/connections type fusectl (rw) /dev/sdb on /media/MYLINUXLIVE type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

=================== ls: /sys/block/sda (filtered): alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent /sys/block/sdb (filtered): alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent /sys/block/sr0 (filtered): alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent /dev (filtered): agpgart block bsg btrfs-control bus cdrom cdrw char console core cpu_dma_latency disk dvd dvdrw fd full fuse fw0 hidraw0 hidraw1 hidraw2 hidraw3 hidraw4 hpet initctl input kmsg log MAKEDEV md mem net network_latency network_throughput null port ppp psaux ptmx pts radio0 random rfkill rtc rtc0 scd0 sda sda1 sdb sg0 sg1 sg2 shm snapshot snd sndstat sr0 stderr stdin stdout urandom usb v4l vbi0 vga_arbiter video0 video24 video32 xconsole zero ls /dev/md:

=================== df -Th:

Filesystem Type Size Used Avail Use% Mounted on aufs aufs 490M 7.2M 483M 2% /tmpfs tmpfs 490M 0 490M 0% /lib/init/rw udev tmpfs 485M 200K 485M 1% /dev tmpfs tmpfs 490M 0 490M 0% /dev/shm /dev/sr0 iso9660 347M 347M 0 100% /live/image tmpfs tmpfs 490M 7.2M 483M 2% /live/cow tmpfs tmpfs 490M 0 490M 0% /live tmpfs tmpfs 490M 8.0K 490M 1% /tmp /dev/sdb vfat 15G 679M 15G 5% /media/MYLINUXLIVE

=================== fdisk -l:

Disk /dev/sda: 120.0 GB, 120034123776 bytes 255 heads, 63 sectors/track, 14593 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes /512 bytes Disk identifier: 0x7fd5b960

Device Boot Start End Blocks Id System /dev/sda1 * 1 3952 31744405 7 HPFS/NTFS

Disk /dev/sdb: 16.0 GB, 16043212800 bytes 64 heads, 32 sectors/track, 15300 cylinders Units = cylinders of 2048 * 512 = 1048576 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes /512 bytes Disk identifier: 0x20ac7dda

This doesn't look like a partition table Probably you selected the wrong device.

Device Boot Start End Blocks Id System /dev/sdb1 ? 1574463 1785826 216435558+ 7 HPFS/NTFS Partition 1 does not end on cylinder boundary. /dev/sdb2 ? 1597667 2551505 976730017 16 Hidden FAT16 Partition 2 does not end on cylinder boundary. /dev/sdb3 ? 1 1 0 6f Unknown Partition 3 does not end on cylinder boundary. /dev/sdb4 24513 475848 462167897 0 Empty Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

=================== Repair blockers No OS has been found on this computer. Please report this message to yannubuntu@gmail.com

=================== Default settings Recommended-Repair This setting would restore the [(generic mbr)] MBR in sda, and make it boot on sda1. Additional repair would be performed: unhide-bootmenu-10s

=================== Settings chosen by the user Boot-Info This setting will not act on the MBR.

No change has been performed on your computer. See you soon! 
```

---

### Post by AndyOpie150 on 2012-10-08
Installed a system rescue cd which has gparted, but partitioning doesn't seem to be my strong point. I tried and reformated a partition and then install Ubuntu from a CD, but it couldn't install the grub to /dev/sda and failed.

---

### Post by critin on 2012-10-08
> **AndyOpie150 said:**
> Installed a system rescue cd which has gparted, but partitioning doesn't seem to be my strong point. I tried and reformated a partition and then install Ubuntu from a CD, but it couldn't install the grub to /dev/sda and failed.

So you were finally able to install another ubuntu?  I wish I had a screenshot of gparted to see how the disk was setup.  I see only sda1, no linux partitions.

**Again I ask, are all of these installed through Wubi?  **I didn't think that was possible, and it probably isn't.  I wonder though, where are the ext4  partitions & why is ntfs the only format shown?  The disk is (a mess)    :(  (sorry)  and in danger of becoming corrupted enough to lose Windows.
> 
after doing some re-partitioning to even out the partition size's in my Windows OS

It's dangerous to mess with windows partition.  Especially more than once.  If you must do something with it, it's best to use Windows disk management to do it.  Windows is very picky with its space, linux is very forgiving.   A big difference.

Someone else will have to help you retrieve the mbr.   I'm sure it can be fixed but only by those who know more than I do about windows.

---

### Post by critin on 2012-10-09
> **AndyOpie150 said:**
> Installed a system rescue cd which has gparted, but partitioning doesn't seem to be my strong point. I tried and reformated a partition and then install Ubuntu from a CD, but it couldn't install the grub to /dev/sda and failed.

Did you get an error message?  Can you see the disk from the rescue cd?  Can you post a screenshot?

---

### Post by critin on 2012-10-09
> **AndyOpie150 said:**
> 
============================= Boot Info Summary: 

Drive: sda _____________________________________________________________________

Partition table entries are not in disk order

=================== Repair blockers No OS has been found on this computer. Please report this message to [email]yannubuntu@gmail.com[/email]

===================**[COLOR=Red] Default settings Recommended-Repair This setting would restore the [(generic mbr)] MBR in sda, and make it boot on sda1. Additional repair would be performed: unhide-bootmenu-10s[/COLOR]**

=================== Settings chosen by the user Boot-Info This setting will not act on the MBR.

No change has been performed on your computer. See you soon! [/CODE]

This may not work at all, but run Boot Repair again and this time choose Recommended Repair instead of Boot Info.  It will attempt to restore the MBR as stated in red.

---

### Post by AndyOpie150 on 2012-10-09
I tried the repair option to no avail.
The MBR suggestion caused me to look in the advanced options. I found the MBR in the 88GB partiton that I formatted to ext.4 to install the failed Ubuntu attempt (Was unallocated by Mini Tool by error as I had three partitions other than the 33GB windows). 
Chose to have the boot repair install generic MBR to sda1. Closed out boot repair. On startup I had my boot selection screen with Windowa and Plop Boot Manager options, but would not boot windows.
Reinstalled boot repair and selected default repair. When done I closed out boot repair and on reboot it booted into the Ubuntu distro that supposedly failed.

Went into disk manager and saw that my 33GB Windows partition was unmounted. Tried to mount but it failed.

I'm now running a self test. Will post results when done.

---

### Post by critin on 2012-10-09
> 
Went into disk manager and saw that my 33GB Windows partition was unmounted. Tried to mount but it failed.What was the error message?  Did you have a box with 'details' to check the error? 

If you can get to the disk, make sure the Windows partition still has the Boot flag.  If it doesn't, put it there.

Can you open gparted and see if there's a red mark (maybe an exclamation point?)  next to any partitions?  Click on them to see the error.

I always install grub to sda from the first install, (the disk itself) not to a partition.  Some do install to partitions, but they seem to have more issues or the experience to know why they chose that option.  Each time I add another OS partition, I let the installer default grub to the disk (sda).

---

### Post by offgridguy on 2012-10-09
I may be getting away from the context of this thread,  but i have avoided so many of the problems
i read about here by installing ubuntu on an older restored computer as the only OS.  I did try a dual
boot on a second computer and ran into a lot of complications, eventually uninstalled ubuntu .  I realize the single system is not an option for everyone but it works well for me.

---

### Post by AndyOpie150 on 2012-10-09
I have to have a Windows partition because of the specialized applications that won't install on a Linux distro.

critin: I will check and do what you mentioned in 6 hours from now.
PS: Thanks for all advice and direction.

---

### Post by critin on 2012-10-09
Originally stated:  >  (was trying to figure out which distro I liked the best and had them all installed for comparission).

Virtual machines or live flash drives are the safest way to do this and keep Windows safe.  Or, one Wubi at a time.  I believe at the end you're going to have to reinstall Windows, deleting all the others.  If that happens, size the disk first in the size you want for Windows,  and make the remaining space unallocated.   Install Windows, and make the unallocated an extended partition.  You can then  size the extended into separate smaller logical partitions for any amount of OS's that there is room for. 

Install grub into the disk (not partitions).   

Starting fresh is the safest, easiest way to get to where you want to get, and you never need to touch the windows partition again.

---

### Post by critin on 2012-10-09
> **offgridguy said:**
>  i have avoided so many of the problems
i read about here by installing ubuntu on an older restored computer as the only OS.  I did try a dual
boot on a second computer and ran into a lot of complications, eventually uninstalled ubuntu .  I realize the single system is not an option for everyone but it works well for me.

I agree, offgridguy.  Those lucky enough to have a choice of having a machine dedicated to linux can learn it easier and faster.  Even a separate disk is a plus.

---

### Post by AndyOpie150 on 2012-10-10
Last night I finally snapped to what is going on. I had the System Rescue CD installed and was checking out a program called Test Disk (thought it was just for analysis of the disk). Found out it was for fixing and recovering the disk.
 It let me know that the /dev/sda1 partition ( where the Windows OS is) is too small (33GB)? Scratch head.
I was in Gparted next (didn't want to mess around with Test Disk until I had more knowledge or help), and that is when I snapped to what was going on.
The /dev/sda1 is only 33GB instead of 117.? GB. 
dev/sda2 is way bigger at over 87GB. This has the other linux partitions and the swap partition in it.
 I'm to much off a visual person and it took how Gparted showed the partitioning table for me to finally snap!

When I choose to split my Windows partition (wanted to just take a little off the end and put onto the partition next to it) I was not thinking at all. I thought it would be like messing with the other partitions, just cleaning up and organizing my space. What I managed to do is to create and run  /dev/sda2 (with the linux partitions and the swap partition in side it) next to the Windows OS  /dev/sda1 partition, instead of keeping the linux partitions inside of /dev/sda1

This is why the Windows OS is not booting. 
I need to figure out how to wipe the /dev/sda2 partition format it to NTFS and merge it back with the /dev/sda1 partition (without messing with the info inside  /dev/sda1), then Windows will boot (after a little more work with the Boot Repair CD).

I really need to keep the /dev/sda1 from getting wiped or corrupted as I will lose a folder that I should have put on the USB drive after creating a live install for another distro.  This folder has the culmination of all my programs and info for Development  of ROM's for my Android device, programs to unbrick the phone and programs for my Windows OS as well as pictures and other info that's important. How much of it I would be able to chase  down and re-download is a big guess (might take a month, and some things can't be found any more).

I had a double helping of stupidity on this  deal.

After I get the /dev/sda2 merged into /dev/sda1 then I can install the Ubuntu CD again and the rest is all down hill from there (Will use the sliding scale partition manager in the Ubuntu install to correctly size the Windows OS this time)

---

### Post by oldfred on 2012-10-10
You cannot merge formated partitions. But can delete a partition and then expand an adjacent partition into the unallocated space.

Testdisk usually does not say a partition is too small, but shows all the history including its original size and possibly other sizes you may have made over time. The more changes you do the more confusing testdisk can be as you have to know or at least have some idea of your partitions and sizes to really use testdisk to make repairs. With many changes you can have overlapping partitions and can only restore the ones that do not overlap.

Windows NTFS partitions have in the PBR - partition boot sector information on the size of the NTFS partition. That has to match partition table or else you will have issues. Usually chkdsk fixes that. Also NTFS partitions really like 30% free space to run well. Most partition tools will not let you shrink it too much but maybe not leave as much space as you really  should have.

Post screenshot from gparted. You can attach to a post with the paperclip icon in the edit panel above your message.

If folder is that critical and you still have not backed it up, do that before any more changes. If you cannot see it from a liveCD, testdisk may show it with deeper search. But if still not seen you need to stop making changes, make a full image of drive and see if photorec can find your files. Photorec can recover deleted info, but only finds extensions not file names and is a long slow process. Then it a lot of work to attempt to restore files names if name is not inside file. After my experience with photorec, I went back and added file names to all my text files, scripts, & python programs.

---

### Post by AndyOpie150 on 2012-10-11
Finally was able to force mount the Windows partiton, using PartedMagic 
 
oldfred: You where right about the actuall size issue of the partition. There was less than 2GB of space left. Once I deleted about 9GB of saved .iso's and a few other useless items (using Space FM in the System Rescue live CD), I was able to boot right into the Windows partition.
 
Now I really feel stupid. It wasn't Mini Tool's fault, it was my own (out of ignorance).
 
 
Cleaned everything up and wiped and formated the /dev/sda2 partition. Merged it with the /dev/sda1 partiton. Then ran the boot repair CD one more time.
Installed the Ubuntu 12.04, as I can download the Gnome classic and KDE desktop environments so I can switch environments if I get bored with the look of one (don't like the unity at all).
Made sure I gave the Windows partition 10 GB's of free space.
 
Will use the KDE once everything is updated (doing this without a connection initially).
 
Then I will split the Ubuntu partition and make another ext.4 to allow me to try different distro's out (I have to try something new at least once a week). This time I will allow everything plenty of free space. Instead of 3 distro's I will go down to my Daily Driver (Ubuntu with the KDE, or Gnome Classic desktop), and one new distro every week or so.
 
 
Thank's for all the advice and help critin.
 
Oldfred: I would have had a very hard time trying to figure it out without that one little piece of info (turned out to be huge). 
 
I hate being an Old Newb. Seems like I don't pickup on things near as fast as I used to when I was in my 20's and 30's. Lack of experience really makes a fellow feel humble amongst all the knowledgeable members here.
 
Will mark this solved.
Thanks again critin (who stuck with me thru this whole brain dead session of mine), and oldfred, who saved my bacon yet again.

---

### Post by oldfred on 2012-10-11
Glad you got it worked out.

I had(have) XP but essentially stopped using it and have many installs of Ubuntu. I I originally had two drives one with XP and the other Ubuntu. But I created a shared FAT32 (Do not use FAT32, now),  so I could have my Firefox & Thunderbird profiles in the shared data partition. Then while learning Ubuntu and my wife wanted to check email or Internet I did not have to reboot back into Windows. 

Then a new larger drive and I started installing Ubuntu in 25GB / partitions. I still have those old installs, some test installs and a NTFS shared and ext3  data partition for almost all my data.   

So if doing multiple installs you may want a shared partition or two.

---

### Post by AndyOpie150 on 2012-10-11
oldfred: Making a shared partition is deffinetly something I would be interested in doing. Could you link me to the best guide for accomplishing this?
I don't want to mess up my Windows partition again.

---

### Post by oldfred on 2012-10-11
You just have to use gparted to create space assuming you have some space. And format as NTFS. Windows should automatically see it as d: drive. But in Ubuntu you have to create a mount point and mount it. You need to add mount to fstab to make a permanent mount.

Some links to cover most of the details. If you have specific questions post back.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Mount NTFS partition:
[http://ubuntuforums.org/showthread.php?t=1927504](http://ubuntuforums.org/showthread.php?t=1927504)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates for fstab mounting instead. Post #6

[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)

---

### Post by AndyOpie150 on 2012-10-11
Thank you very much.

---

### Post by critin on 2012-10-12
Hey, Andy--I'm just glad you got it fixed without losing your work.  It had me worried til oldfred stepped in, then I relaxed.  lol

---

### Post by AndyOpie150 on 2012-10-12
I was stressing pretty hard too. I can't believe it was something that simple! Learn as I go, I do.

 I didn't lose anything at all, but I did make the partition 48GB to make sure I had room (the most I have ever had on it was 37GB).

I'm know rocking Ubuntu 12.04 and using the Kubuntu desktop environment with Gnome Classic as an option as well as a few others.

The other partition is Bodhi for now, then maybe Backtrack next, followed by OS4, then maybe CrunchBang or Slackware.

---

### Post by critin on 2012-10-12
and then & then & then...lol  I do the same thing.  I need larger disks.

---

