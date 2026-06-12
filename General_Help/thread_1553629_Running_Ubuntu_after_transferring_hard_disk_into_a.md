---
title: "Running Ubuntu after transferring hard disk into another computer?"
date: 2010-08-15
forum: General Help
---

### Post by FlameReaper on 2010-08-15
Just wondering, I had Ubuntu installed on my laptop using Wubi. Then  today I transferred the hard disk of the laptop into another laptop of  the same model - except that it uses an AMD Turion64 TL-56 x2 1.8GHz,  whereas the laptop I took it out from is using an AMD Turion64 TL-58 x2  1.9GHz.

What I would like to know is that is it possible for me  to select and run Ubuntu when I come across the OS selection menu? There's the OS selection menu and GRUB2 loads letting me do a selection of OSes to load... yet I  tried, but I can't load anything. The boot process seems to just stop there and does not show any sign of proceeding. The Plymouth splash screen does not show up, and the CPU light indicates it is not loading anything.

Do I have to reconfigure anything to make it work again as it should, now that I've put it in another laptop? Hardware specifications are pretty much the same except for the processor. I'm using an Acer Aspire 4520 by the way.

**EDIT:** The above problem was fixed somehow, with this error below unresolved but still being able to boot...

```
                                                 [    2.270262] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b0056341200]
[    6.370036] ata1: link is slow to respond, please be patient (ready=0)
[   11.350035] ata1: device not ready (errno=-16), forcing hardreset
[   16.550035] ata1: link is slow to respond, please be patient (ready=0)
[   21.410034] ata1: SRST failed (errno=-16)
[   26.610033] ata1: link is slow to respond, please be patient (ready=0)
[   31.470034] ata1: SRST failed (errno=-16)
[   36.670034] ata1: link is slow to respond, please be patient (ready=0)
[   66.490034] ata1: SRST failed (errno=-16)
[   71.510034] ata1: SRST failed (errno=-16)
[   71.510037] ata1: reset failed, giving up
[   71.510109] ata2: port disabled. ignoring.                      
```... but later I did an update via terminal, and after I rebooted I can't login to Ubuntu, and keep dropping to BusyBox. How do I get around this? It happened while I was working in the office.

---

### Post by ajgreeny on 2010-08-15
Have you replaced the original disk or just added to it, ie do you have one disk in the machine or two?  If there are two, the addition may have upset the whole system, and if just a single disk it may be named wrongly in grub.

Using a live CD, download and run boot-info-script from in my signature and report back here.

---

### Post by oldfred on 2010-08-15
When I put in a new motherboard, XP wanted to call BillG to make sure it was ok and not a duplicate install. But the call home screen was hidden behind the boot screens and it took me a while to figure out that windows would not do anything until it called home.

One advantage of having Ubuntu in its own partition as then it does not depend on windows boot loader or the NTFS file system.

---

### Post by FlameReaper on 2010-08-15
> **ajgreeny said:**
> Have you replaced the original disk or just added to it, ie do you have one disk in the machine or two?  If there are two, the addition may have upset the whole system, and if just a single disk it may be named wrongly in grub.

Using a live CD, download and run boot-info-script from in my signature and report back here.

Ah, my bad - I meant that I *swapped* the hard disk drives between the two laptops, actually. Anyhow...

It looks like it seems to be a driver problem, since I was using NVIDIA's proprietary driver. Now trying to reinstall it. Turns out I can actually boot in text mode, which got me a bit confused since I failed to even boot in text mode before.

I'm going to proceed to finish installing the driver and see if there's any success. By the way, I can't use any LiveCDs since this laptop's DVD drive seem to not work somehow, it's not even detected in the system...

---

### Post by FlameReaper on 2010-08-15
Guess I got to the root of the problem, and the graphics problem is just a side-problem I'm having - now that settled, on to the actual problem...

Turns out my bootup was taking a long time to finish, and when I booted in recovery mode (a.k.a text-only) I found these somehow intriguing lines... Now that I can already boot into Ubuntu without much problems (except for that somehow long time to load) I'd like to put this as [solved], but not before I know what's wrong when these lines came out during text-only boot...

> [    2.270262] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b0056341200]
[    6.370036] ata1: link is slow to respond, please be patient (ready=0)
[   11.350035] ata1: device not ready (errno=-16), forcing hardreset
[   16.550035] ata1: link is slow to respond, please be patient (ready=0)
[   21.410034] ata1: SRST failed (errno=-16)
[   26.610033] ata1: link is slow to respond, please be patient (ready=0)
[   31.470034] ata1: SRST failed (errno=-16)
[   36.670034] ata1: link is slow to respond, please be patient (ready=0)
[   66.490034] ata1: SRST failed (errno=-16)
[   71.510034] ata1: SRST failed (errno=-16)
[   71.510037] ata1: reset failed, giving up
[   71.510109] ata2: port disabled. ignoring.

It is only after the last two lines only boot process continued to load Ubuntu normally.

---

### Post by PRC09 on 2010-08-15
When you stated earlier that you swapped drives between laptops and you are running Wubi,does windows actually boot up and run?? I read that when Wubi is actually installed it does read the information in the windows registry in order to set up the drivers that are used during installation so that could be part of your problem......

> The installer may read data from the Windows registry to detect hardware, download the necessary drivers to C:\ubuntu, and add a section to config.txt that will instruct Ubuntu to install the drivers and set the hardware up on the first boot, in order to provide a better out-of-the-box experience for users. 

---

### Post by FlameReaper on 2010-08-15
> **PRC09 said:**
> When you stated earlier that you swapped drives between laptops and you are running Wubi,does windows actually boot up and run?? I read that when Wubi is actually installed it does read the information in the windows registry in order to set up the drivers that are used during installation so that could be part of your problem......

Yes, it does. In fact booting into Windows is the first thing I tried before trying to boot up Ubuntu. Now except for the bootlog entries I posted before, there's no problem now :D

---

### Post by PRC09 on 2010-08-15
Not being an expert at this and just thru reading other posts on that error you could try disabling in bios the IE1394 port(firewire or whatever and see what happens..I did have a similar problem with errors referencing my card reader and when I removed it the errors when away and the boot process went to normal.Dont know if this is any help but......

---

### Post by FlameReaper on 2010-08-16
> **PRC09 said:**
> Not being an expert at this and just thru reading other posts on that error you could try disabling in bios the IE1394 port(firewire or whatever and see what happens..I did have a similar problem with errors referencing my card reader and when I removed it the errors when away and the boot process went to normal.Dont know if this is any help but......

Thanks, but I can't disable the FireWire IEEE 1934 port. It seems that in my laptop's BIOS setup I can only change the boot order, the HDD mode (IDE or AHCI - in this case, IDE for me) and the amount of system memory the integrated graphics will use on my laptop.

I guess I should tag this as solved already, but if anyone can tell me what actually went wrong (although it seems to be nothing serious) on the boot log entries I posted there it'll be a great knowledge for me :D

---

### Post by FlameReaper on 2010-08-27
Uh, bumping this thread after an update via the terminal... Ubuntu worked fine until I rebooted and that's where a new problem surfaced.

I can't seem to load Ubuntu thanks to the root filesystem being unable to mount, and the OS dropped into the BusyBox shell. What do I do to get it running again as usual?

---

### Post by FlameReaper on 2010-08-27
By the way, I did a run of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") on my system, and here is the output of it:

```
                

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sda2          81,915,435   234,420,479   152,505,045   f W95 Ext d (LBA)
/dev/sda5          81,915,498   234,420,479   152,504,982   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2003 MB, 2003828736 bytes
16 heads, 32 sectors/track, 7644 cylinders, total 3913728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     3,913,727     3,913,696   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       d9ee831b-0ae2-4dd0-afbd-83d48ebc5609   ext4                                     
/dev/loop2       d9ee831b-0ae2-4dd0-afbd-83d48ebc5609   ext4                                     
/dev/sda1        BE88EBC988EB7DF1                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        D684124B84122F0D                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D4A3-57FD                              vfat       NANO                          
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/loop1       /media/disk              ext4       (rw)


======================== sda5/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
	insmod ntfs
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set D684124B84122F0D
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash nomodeset video=uvesafb:mode_option=640x400-24,mtrr=3,scroll=ywrap
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set D684124B84122F0D
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set be88ebc988eb7df1
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda5/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda5/Wubi: Location of files loaded by Grub: =================


   4.7GB: boot/grub/grub.cfg
   2.2GB: boot/initrd.img-2.6.32-24-generic
    .9GB: boot/initrd.img-2.6.32-24-generic.bak
   6.3GB: boot/vmlinuz-2.6.32-24-generic
   2.2GB: initrd.img
   6.3GB: vmlinuz
=============================== StdErr Messages: ===============================

umount: /media/D684124B84122F0D: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

```

3 hours prior to this bump is too quick, and I know that; but I really need urgent help because I'm trying to troubleshoot this from my workplace, since there's the only place I can have a dependable Internet connection. If there's a way to get this fixed once for all (perhaps) I'd like to know about it, because fixing this at the workplace is taking up my valuable work time I need to concentrate on.

---

