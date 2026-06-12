---
title: "Problem booting ubuntu after removing windows 7 trial"
date: 2010-06-12
forum: General Help
---

### Post by kernowkoi on 2010-06-12
Hi All,

I have a problem booting ubuntu 9.10 after removing a disk drive that had windows 7 on it from my PC.  Below is a run down of what happened.

My system is MSI based MB with 3 IDE drives and DVD-writer on Primary and Secondary IDE channels.

The MB also has a FASTTRACK SATA/IDE controller that I occasionally use to attach another disk for trial/backup purposes. (main backup is to external USB storage)

For some time I have DUAL booted with grub2 with ubuntu 9.10 and windows XP all fine and no problems. Use ubuntu as its quick and easy on my old PC. XP for some legacy apps.

As I had a spare IDE drive I thought I'd give a Windows 7 a trial. The Drive is attached to the FASTTRACK IDE controller and windows 7 installed with NO OTHER drives attached.  All OK so far!

Reattached my other drives and could boot into ubuntu/XP as required.  Ran sudo update-grub which found new windows 7 Ok! :)

So for the last month I was happily play/using all 3 OS booting from grub2 loader as required.

Windows 7 30 day trail has now expired so no longer of any use to me. So I decided to remove windows 7

Here's what I did:..........

1st:  Just unplugged the disk drive with windows 7 on it!  XP boots OK but ubuntu fails to boot! 

2nd: Re-attached the windows 7 drive and wiped with ubuntu disk utility. Re-ran sudo update-grub windows 7 no-longer on grub2 menu!  Reboot OK windows 7 no-longer on grub2 menu ubuntu and XP  boot ok.  Remove (empty)windows 7 drive again and ubuntu fails to boot!  :(

So I am left with the situation that I have to leave this 'empty' disk drive attached if I want to boot into ubuntu.  

What have I missed? help please!

Rgs
Steve

---

### Post by konqueror7 on 2010-06-12
just a wild suggestion here, have you tried updating grub, without the harddrive, via live cd?

---

### Post by kernowkoi on 2010-06-12
[HI konqueror7]("http://ubuntuforums.org/member.php?u=633585")

Thanks for the reply and suggestion.

> **konqueror7 said:**
> just a wild suggestion here, have you tried updating grub, without the harddrive, via live cd?

Ok by the live CD I assume you mean the CD I made when I downloaded ubuntu 9.10 in the 1st place?  what do I have to do with it to update grub?  Am I in fact removing and re-installing grub by this method?

Rgs
Steve

---

### Post by rodh on 2010-06-12
no,  update grub tells grub to refresh the menu and look for new OS

---

### Post by kernowkoi on 2010-06-12
Hi All,

I'm wondering if this is a grub issue or a ubuntu O/S issue?

It's like the O/S expects to see the disk drive in question empty or not!

Is it a mounting issue? fstab etc..... Do I need to tell the O/S that this drive no-longer exists in some way?

Rgs
Steve

---

### Post by oldfred on 2010-06-12
If you unplug drive and run this we can see if it is looking for something that is missing. Or run it with drive and see what it finds in the old win7 drive that might cause problems.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and click on # in edit panel(code tags) to make it easier to read when you post the results.txt.

---

### Post by kernowkoi on 2010-06-12
Hi oldfred

Ok run that script results pasted below.  The drive I'm trying to get rid of is the 1st one listed in the Drive/Partition Info section 82.0GB
Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


rgs
steve

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks for 
    (UUID=d3fa80c6-d4ba-4027-a0fa-283d203c6fbd)/boot/grub.
 => Windows is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sde

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /wubildr.mbr /wubildr

sdd1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x61fb61fb

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    80,276,804    80,276,742   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x623b623b

Partition  Boot         Start           End          Size  Id System

/dev/sdc1              16,065   234,436,544   234,420,480   f W95 Ext d (LBA)
/dev/sdc5              16,128   234,436,544   234,420,417   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005beea

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   230,259,644   230,259,582  83 Linux
/dev/sdd2         230,259,645   240,107,489     9,847,845   5 Extended
/dev/sdd5         230,259,708   240,107,489     9,847,782  82 Linux swap / Solaris


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x35cb00d5

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   781,417,664   781,417,602   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sdb1        0800780F007805CA                       ntfs       Windows XP                    
/dev/sdc5        46084A1E084A0D7D                       ntfs       Apps & Data                   
/dev/sdd1        d3fa80c6-d4ba-4027-a0fa-283d203c6fbd   ext4                                     
/dev/sdd5        2881db68-acff-4ac0-bb22-47f6f2ed6400   swap                                     
/dev/sde1        5838B97338B9512C                       ntfs       Rock 400GB                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdd1        /                        ext4       (rw,errors=remount-ro)
/dev/sde1        /media/Rock 400GB        fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc5        /media/Apps & Data       fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptOut 
 

=========================== sdd1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="7"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-22-generic root=/dev/sdd1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-22-generic root=/dev/sdd1 ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-21-generic root=/dev/sdd1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-21-generic root=/dev/sdd1 ro single 
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-20-generic root=/dev/sdd1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-20-generic root=/dev/sdd1 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 0800780f007805ca
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=d3fa80c6-d4ba-4027-a0fa-283d203c6fbd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=2881db68-acff-4ac0-bb22-47f6f2ed6400 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdd1: Location of files loaded by Grub: ===================


   8.0GB: boot/grub/core.img
   7.3GB: boot/grub/grub.cfg
    .3GB: boot/initrd.img-2.6.31-20-generic
    .4GB: boot/initrd.img-2.6.31-21-generic
    .6GB: boot/initrd.img-2.6.31-22-generic
    .2GB: boot/vmlinuz-2.6.31-20-generic
    .4GB: boot/vmlinuz-2.6.31-21-generic
    .4GB: boot/vmlinuz-2.6.31-22-generic
    .6GB: initrd.img
    .4GB: initrd.img.old
    .4GB: vmlinuz
    .4GB: vmlinuz.old
```

---

### Post by oldfred on 2010-06-12
I am currently in Karmic and my entries all use UUIDs which do not change.

Your entry is 
 root=/dev/sdd1

But then you delete sda and your sdd drive probably becomes sdc?

I think you have to remove drive and from liveCD reinstall grub2 so it finds the new drive location.

Install from LiveCD:
Find linux partition change sdc1 if not correct or even sdc wanted:
I assume it will find sdc1 but change if not.
sudo fdisk -l
sudo mkdir /mnt/sdc1
sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdc
sudo grub-install --recheck --root-directory=/mnt /dev/sdc

In BIOS make sure you are booting sdc or the 122.9GB drive (current sdd in results.txt).
After booting run
sudo update-grub

and you may want to do this, which does some of the same 
sudo dpkg-reconfigure grub-pc

---

### Post by kernowkoi on 2010-06-14
Hi Oldfred,

I have give your suggestion a go. but has made no difference!:(

> **oldfred said:**
> I am currently in Karmic and my entries all use UUIDs which do not change.

Your entry is 
 root=/dev/sdd1

But then you delete sda and your sdd drive probably becomes sdc?

I think you have to remove drive and from liveCD reinstall grub2 so it finds the new drive location.

Install from LiveCD:
Find linux partition change sdc1 if not correct or even sdc wanted:
I assume it will find sdc1 but change if not.
sudo fdisk -l
sudo mkdir /mnt/sdc1
sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdc
sudo grub-install --recheck --root-directory=/mnt /dev/sdc

In BIOS make sure you are booting sdc or the 122.9GB drive (current sdd in results.txt).
After booting run
sudo update-grub

and you may want to do this, which does some of the same 
sudo dpkg-reconfigure grub-pc


Can I check a couple of things pls.

The lines:
[I]"Find linux partition change sdc1 if not correct or even sdc wanted:
I assume it will find sdc1 but change if not."[/I]

Not quite sure what you mean by this can you expand please?

sudo fdisk -l 

Does not return anything!  if it did what am I looking for?

Rgs
Steve

---

### Post by oldfred on 2010-06-14
Did you use el not num 1 or cap i. You can copy this:

```
sudo fdisk -l
```

---

### Post by kernowkoi on 2010-06-16
Hi Oldfred,

Success!

OK sudo fdisk -l my bad must have been a typo.

That said I still could not get things to work I eventualy realised the bit I was missing doing was the

sudo update-grub

I assumed I need to do this once I had booted without the old win 7 drive attached. Which I could not! :(

I think the clue was when I ran the grub-install it reported back to be the contents of

/boot/grub/device.map 

Booted from the LIVEcd with the old win 7 drive remove created a 'correct' device.map

I then had to re-connect the old win 7 drive to allow grub to boot and then run 

sudo update-grub

To apply the changes made to device.map to the grub.cfg

I have not needed to use the 

sudo dpkg-reconfigure grub-pc

But useful to know about for the future

Thanks for your help

Rgs
Steve

---

### Post by oldfred on 2010-06-16
Success! is always good. Glad you got it working.

---

