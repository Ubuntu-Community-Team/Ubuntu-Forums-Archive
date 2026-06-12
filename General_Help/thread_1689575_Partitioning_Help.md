---
title: "Partitioning Help"
date: 2011-02-17
forum: General Help
---

### Post by ZMan84 on 2011-02-17
**Long story short:** the partition I created to dual boot Win7 and Ubuntu was set to 20GB. I need to increase it, but it doesn't appear in Gparted. What gives?

I'm brand new to the GNU/Linux world and Ubuntu. Been running it for about 2 weeks or so now, and I need to increase my partition size. I originally set it to 20GB but would like to increase it to 40. I look in Gparted and it doesn't list my 20GB Ubuntu partition so I don't really know what to do other than shrink the 240-something NFTS partition of my 250GB harddrive.

I've searched but to haven't been able to find anything related to partitions not showing up in Gparted. I apologise if this topic has been covered and I simply missed it.

Zach

---

### Post by Rubi1200 on 2011-02-17
Hi and welcome to the forums :-)

What do the following commands show?

```
sudo parted -l

sudo fdisk -lu
```

Can you see all the partitions?

---

### Post by ZMan84 on 2011-02-17
> Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  165MB  164MB   primary   fat16        diag
 2      165MB   951MB  786MB   primary   ntfs         boot
 3      951MB   248GB  247GB   primary   ntfs
 4      248GB   250GB  2150MB  extended               lba
 5      248GB   250GB  2149MB  logical   ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

zach@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x90000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      321299      160618+  de  Dell Utility
/dev/sda2   *      321536     1857535      768000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3         1857536   484196351   241169408    7  HPFS/NTFS
/dev/sda4       484196352   488394751     2099200    f  W95 Ext'd (LBA)
/dev/sda5       484198400   488394751     2098176    7  HPFS/NTFS
Honestly, I don't exactly know how to interpret this information, other than I have 5 partitions on my HD. One (sda5) is the main bulk of my HD with sda4 an 'extended' part of sda5. Other than that, I'm lost.

---

### Post by Rubi1200 on 2011-02-17
Did you install Ubuntu using Wubi (which creates a virtual disk inside Windows)?

If not, then I don't see the Ubuntu installation from these results.

---

### Post by ZMan84 on 2011-02-17
Not to my knowledge. I was given a disk of Ubuntu 10.10 and I installed it from that.

Thanks for your help thus far!

---

### Post by Rubi1200 on 2011-02-17
Do you still have the Ubuntu CD? EDIT: you can also do this from within Ubuntu (which I assume you can boot).

If yes, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Hopefully, the results will tell us what is going on and then we can help you further.

---

### Post by ZMan84 on 2011-02-17
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       321,299       321,237  de Dell Utility
/dev/sda2    *        321,536     1,857,535     1,536,000   7 HPFS/NTFS
/dev/sda3           1,857,536   484,196,351   482,338,816   7 HPFS/NTFS
/dev/sda4         484,196,352   488,394,751     4,198,400   f W95 Ext d (LBA)
/dev/sda5         484,198,400   488,394,751     4,196,352   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       48dd1145-f686-448b-9f44-427cbbbaa1c6   ext4                                     
/dev/sda1        07DA-0B16                              vfat       DellUtility                   
/dev/sda2        2AC4CC2FC4CBFAD9                       ntfs       RECOVERY                      
/dev/sda3        9E84CF7584CF4F09                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        C042D31E42D317CC                       ntfs       READER                        
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


======================== sda3/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
}

if [ "${recordfail}" = 1 ]; then
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
menuentry "Ubuntu, Linux 2.6.35-25-generic-pae" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 9e84cf7584cf4f09
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-25-generic-pae root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry "Ubuntu, Linux 2.6.35-25-generic-pae (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 9e84cf7584cf4f09
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-25-generic-pae root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 2ac4cc2fc4cbfad9
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

============================= sda3/Wubi/etc/fstab: =============================

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

================= sda3/Wubi: Location of files loaded by Grub: =================


  15.2GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.35-25-generic-pae
   4.5GB: boot/vmlinuz-2.6.35-25-generic-pae
    .6GB: initrd.img
   4.5GB: vmlinuz
```
I'm considering reinstalling Ubuntu and make sure I know I'm doing it the right way. Should I?

---

### Post by Rubi1200 on 2011-02-17
Hi and thanks for the results.

Okay, well you did install using the Windows installer (Wubi).

Look at sda3 and you will see the files etc.

There is a way to resize the virtual disk, but as far as I know it can only go to a maximum of 30GB.

See here for more information as well as how to create some more virtual space:

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?")
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20create%20a%20virtual%20disk%20in%20Ubuntu?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20create%20a%20virtual%20disk%20in%20Ubuntu?)

If you want to do a proper dual-boot install with Ubuntu on its own dedicated partition that is another story.

It is also possible to migrate the current Wubi install to the hard-drive though you would need to prepare the partition beforehand.

Let us know please so we can advise you further.

---

### Post by ZMan84 on 2011-02-17
I tried a write-up on how to move a wubi installation to a partition but of course, nothing I try to do within Linux works... I booted from the Ubuntu CD (10.10) so I could re-size the Windows partition but Gparted only threw up an error and prevented me from doing anything to the size of that partition. 

I really don't understand how this can be so daunting. Anyone have any idea why I can't resize my Windows partition?

---

### Post by sikander3786 on 2011-02-17
So, what I get from all the conversation above is that you want to increase the size of your sda5 from 20 GB to 40 GB and still want to continue dual-booting your existing Windows and Ubuntu installs. But 30GB is the limit for Wubi installs as Rubi said above.

First of all, using gparted or any other Linux tools with NTFS partitions is not recommended as they can easily cause data loss. Windows 7 comes with a nice partitioning tool and you can use that for shrinking your Windows 7 partition. Defrag your windows partition, run chkdsk multiple times then resize it and leave some space unallocated that you want to add to sda5.

And apart from that, Windows doesn't like much changes to its partitions without it being notified so if you use gparted, chances are that Windows refuses to boot or simply, starts acting weird.

So, resize your Windows partition and reboot multiple times to test that everything is working fine. Then to add the freed space to your extended/logical sda4,sda5, you can either use Windows partitioning tool or gparted.

If you want to do a proper dual boot with Ubuntu i.e, Ubuntu on its own separate partitions, see here.

[http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html)

For gparted resizing,

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by Quackers on 2011-02-17
The best way to resize a Windows partition is usually with a Windows tool.
What I would do, personally, is this.
Backup whatever is in sda5 (about 2GB it looks like), btw what's in that partition?
I would then delete sda5, and sda4 using Windows Disk Management console.
I would then delete everything to do with wubi from the Windows system.
I would then defragment the C: partition (probably sda3), probably twice.
Then, back in Disk Management I would look to see how much of the C: partition is free space.
If there is lots of unused space you can then right-click on the C: partition and select "shrink", enter the amount of shrinkage you want and click OK.
Obviously, if there is not much unused space in C:, you will not be allowed to shrink it.
If all of the above goes ok, you will have 3 primary partitions and some unallocated space in a block at the end of the disc. 
Then, either in gparted or in the Ubuntu installation process, you can create an extended partition in that unallocated space, which can have as many logical partitions in it as you wish. Ubuntu partitions (root and swap) can be 2 of those logical partitions. You could also make a replacement partition for whatever was in sda5 (that you backed up) and restore that, if you want to.

---

