---
title: "HEEEELP!!! (Please?)"
date: 2010-07-13
forum: General Help
---

### Post by dfd001 on 2010-07-13
A little background:
I am NOT a computer guy; that is why I liked windows.  Plug n Play or hit the .exe and all is fine.  But Windows (lately 7) is problematic as well.  No need to list the problems I have had...my guess is most in here have experienced the same, or similar.  Point is that I decided to try something new...I have ubuntu because, well...I could not get fedora to run, no matter what I tried.  For whatever reason, I had no such problem with ubuntu.  So I tried it.  

I really like Ubuntu.  But there are a couple of problems I am experiencing:

1.  When I boot in Ubuntu mode, I get a boot disk (or is it drive) error, followed by a black screen that tells me to type 'help' for a list of commands.  This leads to a paragraph of words that I have absolutely no idea what they mean.  My solution: reboot.  Here is that problem part deux: when I do this, most times it works.  The last time I did it, I had to reboot 3 times before Ubuntu loaded.  Oh yeah...I should add that this does not happen every time.  If I had to make a judgment, I would say maybe 40% of the time.  It seems to be a 'floating' problem.  Any suggestions?

2.  I have a 2 hard drives.  (Don't ask me for a name..I built this machine on my own.  Its a hodgepodge.  More fun that way, not to mention being able to buy each component seperately as I could afford it).  Anyhow, my C drive has only my OS.  All programs other than OS I load on d drive.  Not knowing anything about ubuntu, it loaded on C drive.  All programs, downloads, etc also go to c.  But c has very limited space, and thus far, I have not figured out how to direct downloads to d.  Its most probably something really simple and silly, but I just don't see it.  (My d drive is recignized by ubuntu as "xxxgigabyte file system", but has no drive letter)  Is it possible to 'move' ubuntu to my d drive?

Thus far, I really like ubuntu, and would like to keep using it, even though I still have only just firured out how to open a terminal, and have no idea how to use Wine (any directions on that would be very appreciated as well.)  

Thanks

---

### Post by prodigy_ on 2010-07-13
First of all, Linux systems (including Ubuntu) do not assign letters (C:, D:, etc.) to partitions. So forget about them, they're Windows stuff.

In Linux, there's root partition that is mounted to **/** directory (aka the root of the file system). Any other partition (except swap) can be mounted to any other directory. For convenience in Ubuntu it's usually **/media/<partition_name>**.

---

To help you to fix your boot problem we need to understand what exactly is going on. Download [Boot Info Script](http://bootinfoscript.sourceforge.net) and run it. Post the output here.

---

### Post by Dustin2128 on 2010-07-13
> **dfd001 said:**
> A little background:
I am NOT a computer guy; that is why I liked windows.  Plug n Play or hit the .exe and all is fine.  But Windows (lately 7) is problematic as well.  No need to list the problems I have had...my guess is most in here have experienced the same, or similar.  Point is that I decided to try something new...I have ubuntu because, well...I could not get fedora to run, no matter what I tried.  For whatever reason, I had no such problem with ubuntu.  So I tried it.  

I really like Ubuntu.  But there are a couple of problems I am experiencing:

1.  When I boot in Ubuntu mode, I get a boot disk (or is it drive) error, followed by a black screen that tells me to type 'help' for a list of commands.  This leads to a paragraph of words that I have absolutely no idea what they mean.  My solution: reboot.  Here is that problem part deux: when I do this, most times it works.  The last time I did it, I had to reboot 3 times before Ubuntu loaded.  Oh yeah...I should add that this does not happen every time.  If I had to make a judgment, I would say maybe 40% of the time.  It seems to be a 'floating' problem.  Any suggestions?

2.  I have a 2 hard drives.  (Don't ask me for a name..I built this machine on my own.  Its a hodgepodge.  More fun that way, not to mention being able to buy each component seperately as I could afford it).  Anyhow, my C drive has only my OS.  All programs other than OS I load on d drive.  Not knowing anything about ubuntu, it loaded on C drive.  All programs, downloads, etc also go to c.  But c has very limited space, and thus far, I have not figured out how to direct downloads to d.  Its most probably something really simple and silly, but I just don't see it.  (My d drive is recignized by ubuntu as "xxxgigabyte file system", but has no drive letter)  Is it possible to 'move' ubuntu to my d drive?

Thus far, I really like ubuntu, and would like to keep using it, even though I still have only just firured out how to open a terminal, and have no idea how to use Wine (any directions on that would be very appreciated as well.)  

Thanks
Not sure about your first problem but as for your second, it depends on what you mean by move. Do you mean move the OS to the D drive? If you mean to do that I'd recommend breaking out gparted. If you mean move the storage there, you'd just have to mount it and move whatever you want there. The main difference is this: if you move the main ubuntu partition to the second drive, it'll be (if you want maximum speed) in the linux format (ext3/4), meaning that you can't acess it from your windows partition. As for the other, assuming it (the second drive) is in FAT or NTFS format, you'll get reduced performance on ubuntu. Post your gparted table? might give me some ideas.

---

### Post by dfd001 on 2010-07-14
> **prodigy_ said:**
> First of all, Linux systems (including Ubuntu) do not assign letters (C:, D:, etc.) to partitions. So forget about them, they're Windows stuff.

In Linux, there's root partition that is mounted to **/** directory (aka the root of the file system). Any other partition (except swap) can be mounted to any other directory. For convenience in Ubuntu it's usually **/media/<partition_name>**.

---

To help you to fix your boot problem we need to understand what exactly is going on. Download [Boot Info Script]("http://bootinfoscript.sourceforge.net") and run it. Post the output here.

Here is the file you asked about.  I certainly cannot decipher it...but if you don't mind my asking, how are yu going to get anything from it?  I am in ubuntu now.  Anyhow, thank you for your time.  Also, I realize that, at least in large part, some of my problems are due to my own inexperience and lack of knowledge about ubuntu.  So some, I learn more each day.  My next task is 'mounting' a drive, and figuring out 'permissions'.  Good luck to me!:p

```

```Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sdb1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       6ad12dd9-0c21-4cc2-be72-635d63acd338   ext4                                     
/dev/sda1        6A2A64A62A6470CD                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        84146D7D146D735A                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda1        /media/6A2A64A62A6470CD  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


======================== sdb1/Wubi/boot/grub/grub.cfg: ========================

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
menuentry "Ubuntu, Linux 2.6.32-23-generic" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 84146d7d146d735a
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-23-generic (recovery mode)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 84146d7d146d735a
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 84146d7d146d735a
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 84146d7d146d735a
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 84146d7d146d735a
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sdb1/Wubi/etc/fstab: =============================

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
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================= sdb1/Wubi: Location of files loaded by Grub: =================


  10.9GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.32-21-generic
   6.7GB: boot/initrd.img-2.6.32-23-generic
   6.5GB: boot/vmlinuz-2.6.32-21-generic
   6.7GB: boot/vmlinuz-2.6.32-23-generic
   6.7GB: initrd.img
    .8GB: initrd.img.old
   6.7GB: vmlinuz
   6.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc

---

### Post by prodigy_ on 2010-07-14
Since you apparently used Wubi, I can only say that Wubi isn't intended for permanent setups. In the long run perhaps the best option for you is to download LiveCD and install the real thing.

If you'll go this route, remember that you'll need some unpartitioned space on your hard drive because Linux can't be installed on a Windows (NTFS) partition without tricky tools like Wubi. If you don't need Windows anymore you can just remove your Windows partition and use the freed space.

Also don't forget to **backup your data** and uninstall Wubi first. Otherwise you can easily end up having even more boot problems.

---

### Post by jmszr on 2010-07-14
dfd001,

1) Wubi installs Ubuntu into a windows folder - usually a NTFS type of file system, this file system has a known reaction of being unstable in other operating systems like Ubuntu when a hard shutdown happens.

Just boot into windows, then shutdown correctly and then try to boot into ubuntu as normal, everything should work. (From LowSky)

If it doesn't:
                    Boot into Windows, Goto "My Computer", Right click the drive that you have installed Ubuntu in. Click Properties. Select the "Tools" tab and click "check now" under error checking (with Vista you might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After the checking is done, shut down  by using the start menu (Do Not hard reboot) and  try using Ubuntu now. ( From Ago)
                  
You can also accomplish the immediate previous tip by running chkdsk/r  in Windows and then shutting down properly.

2) I agree with prodigy_ that you should consider either a dual-boot ([https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)  and: [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)) or Ubuntu-only installation. I would suggest the dual-boot until/unless you want an Ubuntu-only install.

---

### Post by Jonners59 on 2010-07-15
I kicked off about a year ago moving from Windows - used like you OS in C, Apps in D and Docs in another, and back ups in another partition.

I also used Wubi - still tend to if something goes wrong with Grub....  BUT I suggest you send off for the Disc and load using that.  I suggest you install in its own space on , remember HOME is sort of like where you would store your docs, but you can still access your docs in your D drive.  This will be found under the PLACES, and once mounted from there will also appear in MEDIA.....

Yes, Ubuntu is better, though at times you will get frustrated.  But keep at it.

PS.  Wubi has vast limitations on memory.  At some point you will have loading errors due to this....  Just be warned.  Get the disc.

---

