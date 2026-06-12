---
title: "Bug in grub update script"
date: 2010-12-17
forum: General Help
---

### Post by dan_blm on 2010-12-17
I have two questions.

1. My update manager is completely locked up. When I try to add a new package, I get an error message. When I run sudo apt-get install xyz I get a notice to run sudo dpkg --configure -a. When I run that, the program dies with the following message: 

GRUB upgrade scripts have detected a GRUB Legacy setup in /boot/grub.     &#8593; 
 &#9474;                                                                           &#9646; 
 &#9474; In order to replace the Legacy version of GRUB in your system, it is      &#9618; 
 &#9474; recommended that /boot/grub/menu.lst is adjusted to chainload GRUB 2      &#9618; 
 &#9474; from your existing GRUB Legacy setup.  This step may be automaticaly      &#9618; 
 &#9474; performed now.                                                            &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; It's recommended that you accept chainloading GRUB 2 from menu.lst, and   &#9618; 
 &#9474; verify that your new GRUB 2 setup is functional for you, before you       &#9618; 
 &#9474; install it directly to your MBR (Master Boot Record).                     &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; In either case, whenever you want GRUB 2 to be loaded directly from MBR,  &#9618; 
 &#9474; you can do so by issuing (as root) the following command:                 &#9618; 
 &#9474;                                                                           &#8595; 
 &#9474;                                <ok>

I do not even use grub. I launch ubuntu from another partition. I do not know of a way to delete grub.
Is there a way out of this?

2. How do you boot into terminal mode?

Thanks

---

### Post by wilee-nilee on 2010-12-17
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

You can run this script from a Ubuntu install as well. It sounds like you gave a grub2 upgrade and you haven't done the accept is as a final command.

Frankly you don't mention what you have running on the computer the bootscript will tell us what is were.

---

### Post by dan_blm on 2010-12-18
Below is the info asked.
As I was saying, I am booting from another partition, sda9. There should never be this error that I got. How do I get out of this? I do not think I was doing anything wrong.

  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #9 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Grub
    Boot sector info:  Grub Dstx89fsemba9dyc3[ is installed in the boot 
                       sector of sda8 and looks at sector 86943844 of the 
                       same hard drive for the stage2 file. A stage2 file is 
                       at this location on /dev/sda. Stage2 looks on 
                       partition #1 for .

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:   This is .()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325    67,103,504    67,023,180   7 HPFS/NTFS
/dev/sda3          67,103,505    67,312,349       208,845  83 Linux
/dev/sda4          67,312,411   156,248,189    88,935,779   f W95 Ext d (LBA)
/dev/sda5         149,741,928   156,248,189     6,506,262   b W95 FAT32
/dev/sda6          67,312,413    67,392,674        80,262  83 Linux
/dev/sda7          67,392,738    86,943,779    19,551,042  83 Linux
/dev/sda8          86,943,843    99,602,999    12,659,157  82 Linux swap / Solaris
/dev/sda9          99,603,063   149,741,864    50,138,802  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        07D4-0506                              vfat       DellUtility                   
/dev/sda2        72741A217419E91D                       ntfs                                     
/dev/sda3        a2b3465c-a7db-459e-9cc5-16873ebaabf6   ext3       /boot                         
/dev/sda4: PTTYPE="dos" 
/dev/sda5        98AE-C051                              vfat       NEW VOLUME                    
/dev/sda6        792a6ea4-9c0d-4e53-9752-eae83499d1d0   ext3       /                             
/dev/sda7        ea4e12b7-5cd9-4ed3-8279-33acfb276dd4   ext3                                     
/dev/sda8        2d2fd5a6-428f-4402-891c-19ba9d79c35b   swap                                     
/dev/sda9        4af06232-12d1-427d-bcee-76e9b5b12a61   ext3                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect 

============================= sda3/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,2)
#          kernel /vmlinuz-version ro root=/dev/hda6
#          initrd /initrd-version.img
#boot=/dev/hda
default=0
timeout=10
splashimage=(hd0,2)/grub/splash.xpm.gz
title Fedora Core (2.6.9-1.667)
    root (hd0,2)
    kernel /vmlinuz-2.6.9-1.667 ro root=LABEL=/  rhgb
    initrd /initrd-2.6.9-1.667.img
title Windows
    rootnoverify (hd0,1)
    chainloader +1
title Red Hat Linux (2.4.20-8)
    root (hd0,8)
    kernel /boot/vmlinuz-2.4.20-8 ro root=LABEL=/1 hdc=ide-scsi
    initrd /boot/initrd-2.4.20-8.img
title Linux suse?
    kernel (hd0,8)/boot/vmlinuz root=/dev/hda9 vga=0x305 selinux=0 splash=silent resume=/dev/hda7 elevator=cfq showopts
    initrd (hd0,8)/boot/initrd

title Failsafe
    kernel (hd0,8)/boot/vmlinuz root=/dev/hda9 showopts ide=nodma apm=off acpi=off vga=normal noresume selinux=0 barrier=off nosmp noapic maxcpus=0  3
    initrd (hd0,8)/boot/initrd
=================== sda3: Location of files loaded by Grub: ===================


  34.3GB: grub/grub.conf
  34.3GB: grub/menu.lst
  34.3GB: grub/stage2
  34.3GB: initrd-2.6.9-1.667.img
  34.3GB: vmlinuz
  34.3GB: vmlinuz-2.6.13.4
  34.3GB: vmlinuz-2.6.9-1.667

========================== sda7/boot/grub/grub.conf: ==========================

# This is a sample grub.conf for use with Genkernel, per the Gentoo handbook
# [http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10#doc_chap2](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10#doc_chap2)
# If you are not using Genkernel and you need help creating this file, you
# should consult the handbook. Alternatively, consult the grub.conf.sample that
# is included with the Grub documentation.

default 0
timeout 10
splashimage=(hd0,6)/boot/grub/splash.xpm.gz

title Gentoo
root (hd0,6)
kernel /boot/kernel root=/dev/sda7
#ram0 real_root=/dev/sda3
#initrd /boot/initramfs-genkernel-x86-2.6.24-gentoo-r5

title Latest Gentoo Linux 2.6.32-r7
root (hd0,8)
kernel /boot/kernel-2.6.32-r7 root=/dev/sda9

title SUSE Linux 10.1
root (hd0,9)
kernel /boot/vmlinuz root=/dev/hda10 vga=0x303
initrd /boot/initrd

title Windows
    chainloader (hd0,1)+1


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=ea4e12b7-5cd9-4ed3-8279-33acfb276dd4 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=2d2fd5a6-428f-4402-891c-19ba9d79c35b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  43.2GB: boot/grub/grub.conf
  43.2GB: boot/grub/menu.lst
  43.3GB: boot/grub/stage2
  43.3GB: boot/initrd.img-2.6.32-24-generic
  43.3GB: boot/initrd.img-2.6.32-25-generic
  43.2GB: boot/vmlinuz-2.6.32-24-generic
  44.3GB: boot/vmlinuz-2.6.32-25-generic
  43.5GB: boot/vmlinuz-2.6.32-26-generic
  43.3GB: initrd.img
  43.3GB: initrd.img.old
  44.3GB: vmlinuz
  43.2GB: vmlinuz.old

========================== sda9/boot/grub/grub.conf: ==========================

# This is a sample grub.conf for use with Genkernel, per the Gentoo handbook
# [http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10#doc_chap2](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10#doc_chap2)
# If you are not using Genkernel and you need help creating this file, you
# should consult the handbook. Alternatively, consult the grub.conf.sample that
# is included with the Grub documentation.

default 0
timeout 10
splashimage=(hd0,/boot/grub/splash.xpm.gz

title Ann
root (hd0,6)
kernel /boot/vmlinuz-2.6.32-24-generic root=/dev/sda7
#ram0 real_root=/dev/sda3
initrd /boot/initrd.img-2.6.32-24-generic

title Latest Gentoo Linux 2.6.32-r7
root (hd0,
kernel /boot/kernel-2.6.32-r7 root=/dev/sda9



title Windows
    chainloader (hd0,1)+1


=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# noatime turns off atimes for increased performance (atimes normally aren't 
# needed; notail increases performance of ReiserFS (at the expense of storage 
# efficiency).  It's safe to drop the noatime options if you want and to 
# switch between notail / tail freely.
#
# The root filesystem should have a pass number of either 0 or 1.
# All other filesystems should have a pass number of 0 or greater than 1.
#
# See the manpage fstab(5) for more information.
#

# <fs>            <mountpoint>    <type>        <opts>        <dump/pass>

# NOTE: If your BOOT partition is ReiserFS, add the notail option to opts.
#/dev/BOOT        /boot        ext2        noauto,noatime    1 2
/dev/sda9        /        ext3        noatime        0 1
/dev/sda8        none        swap        sw        0 0
/dev/sda7        /mnt/7        ext3        noatime        0 1
/dev/cdrom        /mnt/cdrom    auto        noauto,rw    0 0
#/dev/fd0        /mnt/floppy    auto        noauto        0 0

# glibc 2.2 and above expects tmpfs to be mounted at /dev/shm for 
# POSIX shared memory (shm_open, shm_unlink).
# (tmpfs is a dynamically expandable/shrinkable ramdisk, and will
#  use almost no memory if not populated with files)
shm            /dev/shm    tmpfs        nodev,nosuid,noexec    0 0

=================== sda9: Location of files loaded by Grub: ===================


  68.0GB: boot/grub/grub.conf
  68.0GB: boot/grub/menu.lst
  68.1GB: boot/grub/stage2
=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by Krytarik on 2010-12-18
Sorry wilee-nilee for interfering.

According to the output you posted it's imo ***pletely safe to

1.) confirm the dialog posted
2.) remove grub altogether or leave it as it is, you may do it via Synaptic, search for "grub" (Name)

Greetings.

---

### Post by dan_blm on 2010-12-19
Thanks for the 2 responses. What specifically (step by step) needs to be done to get around this? My own idea was that grub could be removed but did not know how. Where do I find the script that is causing this? I think that this needs to be fixed.

Dan_blm

---

### Post by Krytarik on 2010-12-19
Like wilee-nilee said, your update-manager has obviously done an upgrade from the old GRUB to the new GRUB2 (did you a dist-upgrade?), and you did not confirm to migrate the old grub-config. The package-manager is therefore "locked". Then just confirm this by doing again
```
sudo dpkg --configure -a
```
After you've done this the package-manager is unlocked.

Now you can decide wether you want to remove grub from your system.
If you decide to do so, go to "System -> Administration -> Synaptic", search for "grub" (Name), and remove (completely) everything that shows up as installed.

---

### Post by dan_blm on 2010-12-21
Thanks Krytarik,

The command you indicate is what I originally tried, please see my original note; so my computer is quite sick. I tried the command again with the same result. At least now I know where to find system programs. When I went there, I got another error message.

Seems like the only the only way out would be re-install the upgrade

---

### Post by Krytarik on 2010-12-22
In your opening post I see an <ok>-button, isn't this click-/confirmable?

---

### Post by dan_blm on 2010-12-22
No.

---

### Post by Krytarik on 2010-12-23
Try this:

```
 sudo dpkg --configure --force-confnew grub-pc
```
[http://manpages.ubuntu.com/manpages/lucid/man1/dpkg.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/dpkg.1.html)

---

### Post by dan_blm on 2010-12-23
Thanks, but the result is the same.

---

### Post by Krytarik on 2010-12-25
Just a try: delete "/boot/grub/menu.lst" before issuing the command again.

---

### Post by dan_blm on 2010-12-27
Krytarik,

I deleted the file you indicated +/etc/default/grub, and that brought me to a new window:

The installation could have failed because of an error in the corresponding software package or it was canceled in an unfriendly way. You have to repair this before you can install or remove any further software.

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474; The following Linux command line was extracted from /etc/default/grub or  &#9474; 
 &#9474; the `kopt' parameter in GRUB Legacy's menu.lst.  Please verify that it    &#9474; 
 &#9474; is correct, and modify it if necessary.                                   &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Linux command line:                                                       &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; _________________________________________________________________________ &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;                                  <Ok>                                     &#9474; 
 &#9474;                                           

While nervously pressing keys to move forward, I inadvertently pressed the down arrow and that highlighted the Ok above and I was able to move forward The OK may have been accessible in the original window, but I never pressed the down or right keys. Next came the below screen: 

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474; A new version of configuration file /etc/default/grub is available, but   &#9474; 
 &#9474; the version installed currently has been locally modified.                &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; What do you want to do about modified configuration file grub?            &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;        install the package maintainer's version                           &#9474; 
 &#9474;        keep the local version currently installed                         &#9474; 
 &#9474;        show the differences between the versions                          &#9474; 
 &#9474;        show a side-by-side difference between the versions                &#9474; 
 &#9474;        show a 3-way difference between available versions                 &#9474; 
 &#9474;        do a 3-way merge between available versions (experimental)         &#9474; 
 &#9474;        start a new shell to examine the situation                         &#9474; 
 &#9474;                                                                

&#8206;           &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;                                  <Ok>                         


 keep the local version currently installed is what I highlighted and was able to highlight the OK by using the right arrow.

Next came the following screen:


                &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
                &#9474; GRUB install devices:                        &#9474; 
                &#9474;                                              &#9474; 
                &#9474;    [ ] /dev/sda (80000 MB, Maxtor_6Y080L0)   &#9474; 
                &#9474;    [ ] - /dev/sda7 (10010 MB, /)             &#9474; 
                &#9474;                                              &#9474; 
                &#9474;                                              &#9474; 
                &#9474;                    <Ok>                      &#9474; 
                &#9474;                                              &#9474; 
                &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
                                                                 
Was not able to highlight the OK in this window. Ctrl-C or Ctrl-Z did not work.
But, enter worked and brought me to next window:
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; You chose not to install GRUB to any devices.  If you continue, the boot  &#9474; 
 &#9474; loader may not be properly configured, and when your computer next        &#9474; 
 &#9474; starts up it will use whatever was previously in the boot sector.  If     &#9474; 
 &#9474; there is an earlier version of GRUB 2 in the boot sector, it may be       &#9474; 
 &#9474; unable to load modules or handle the current configuration file.          &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; If you are already running a different boot loader and want to carry on   &#9474; 
 &#9474; doing so, or if this is a special environment where you do not need a     &#9474; 
 &#9474; boot loader, then you should continue anyway.  Otherwise, you should      &#9474; 
 &#9474; install GRUB somewhere.                                                   &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Continue without installing GRUB?                                         &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;                    <Yes>                       <No>          
Yes or no was always highlighted and I was able to scroll between the 2 using the left/right arrows; I selected yes. And it seems that everything is working now.

Unrelated note: xorg still crashes if there is too much action on the screen (I have version 1.76). 

I was able to perform an update, and everything worked fine.

Who will we fix the cause for all the above?

---

### Post by dcstar on 2010-12-27
```
sudo dpkg-reconfigure debconf
```
Select **Gnome**.

This will make future things much easier.

---

### Post by dan_blm on 2011-01-04
These area all workarounds and thanks for the help. Is anyone going to fix this?

---

