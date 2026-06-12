---
title: "Dual Boot Help"
date: 2010-03-02
forum: General Help
---

### Post by Buntzilla on 2010-03-02
Ok here goes.

I'm new here, and to linux in general. I have a Dell Studio 1555 Laptop with Windows 7 installed.

I decided to dual boot with Ubuntu 9.10

I have a couple questions. 

1) I have 2 boot managers running. On start up the Windows Boot Manager comes up and gives me a choice between Windows 7 and Ubuntu.

If I pick Ubuntu, it brings me to the GNU Grub boot manager. 
Grub gives me 3 options, Linux 2.6.31-14-generic, Linux 2.6.31-14-generic (recovery), and some windows7 disk option.

I want to get rid of one of these managers. I prefer the Windows Manager b/c it gives me only the 2 options.

2) My second question. Can I modify one of these boot screens? I want a different background, rather then just black (I found a cool graphic with both the windows and Ubuntu logo).

Any help or suggestions are appreciated.

---

### Post by Buntzilla on 2010-03-02
I've been googling but cant really figure this out. I am pretty new to this whole linux thing.

I should say I really like the look of Unbuntu.

---

### Post by Buntzilla on 2010-03-03
Bumpity Bump

---

### Post by jsriz on 2010-03-03
> **Buntzilla said:**
> 

2) My second question. Can I modify one of these boot screens? I want a different background, rather then just black (I found a cool graphic with both the windows and Ubuntu logo).

with grub2 of ubuntu you can customize anything and everything you can even have only two entries as you mentioned.(though it needs a bit of scripting work to be done)
you jus need to google it
heres something to start with 
[HTML]http://ubuntuforums.org/showthread.php?t=1296225[/HTML]

About the first question try reinstalling grub2 package and running sudo update-grub2

this should replace the windows bootloader.
I dont think keeping windows boot loader is such a good idea ,coz it wont recognize the future distros (knowing windows i am even doubtful about it having any customizing options at all.)
For me grub2 was the most interesting addition to 9.10...........

---

### Post by oldfred on 2010-03-03
Do you have wubi installed inside windows? Or how is it that the windows boot loader comes up first?

---

### Post by Buntzilla on 2010-03-03
> **jsriz said:**
> with grub2 of ubuntu you can customize anything and everything you can even have only two entries as you mentioned.(though it needs a bit of scripting work to be done)
you jus need to google it
heres something to start with 
[HTML]http://ubuntuforums.org/showthread.php?t=1296225[/HTML]
 
**About the first question try reinstalling grub2 package and running sudo update-grub2**

this should replace the windows bootloader.
I dont think keeping windows boot loader is such a good idea ,coz it wont recognize the future distros (knowing windows i am even doubtful about it having any customizing options at all.)
For me grub2 was the most interesting addition to 9.10...........
 
Thank you sir. I will try this out when I get home from work tonight.
 
Yeah, I personally don't care witch loader I use. I just didn't like all the options the grub gave, so if i can remove a few that would be great. Not really something i'm worried about, but my wife would probably get all confused.
 
I want to set this as the background for my Grub loader page.
[IMG]http://i908.photobucket.com/albums/ac287/pegcitypro/dual-boot.jpg[/IMG]

---

### Post by Buntzilla on 2010-03-03
> **oldfred said:**
> Do you have wubi installed inside windows? Or how is it that the windows boot loader comes up first?
 
 
I'm not 100% clear on what you are asking.
 
When I turn my computer on (or restart) the regular Dell Bios screen splashes, then it goes right to the Windows Boot Manager.
 
If I select Windows, it loads straight into Windows 7 like normal.
 
If I select Ubuntu, it then brings up the GNU Grub Boot screen.
 
I would prefer to have a single boot screen. Don't really care which, although given **jsriz**'s response I think i'd prefer the grub menu (as I want to customize it).
 
I have Ubuntu installed on a seperate partition then Win 7 if that makes a difference.

---

### Post by oldfred on 2010-03-03
To fully understand the boot process, download this script:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by Buntzilla on 2010-03-03
Here's the Boot Info
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
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6f191570

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              80,325    16,120,260    16,039,936   7 HPFS/NTFS
/dev/sda3          16,121,856    30,799,871    14,678,016   f W95 Ext d (LBA)
/dev/sda5          16,123,904    30,799,871    14,675,968   7 HPFS/NTFS
/dev/sda4    *     30,800,325   488,395,119   457,594,795   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       5e9b6450-c1f1-45b9-90e0-dc61620099ae   ext4                                     
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        58B27D48B27D2C1E                       ntfs       RECOVERY                      
/dev/sda4        30667F93667F5914                       ntfs       OS                            
/dev/sda5        36841EE6841EA7FF                       ntfs       Ubuntu                        

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /host                    fuseblk    (rw)
/dev/sda4        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


======================== sda5/Wubi/boot/grub/grub.cfg: ========================

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
set default="0"
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
    insmod ntfs
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 36841ee6841ea7ff
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 36841ee6841ea7ff
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod ntfs
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 36841ee6841ea7ff
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 36841ee6841ea7ff
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda4)" {
    insmod ntfs
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 30667f93667f5914
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
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda5/Wubi: Location of files loaded by Grub: =================


   3.4GB: boot/grub/grub.cfg
   2.6GB: boot/initrd.img-2.6.31-14-generic
   3.4GB: boot/initrd.img-2.6.31-19-generic
   2.5GB: boot/vmlinuz-2.6.31-14-generic
   3.0GB: boot/vmlinuz-2.6.31-19-generic
   3.4GB: initrd.img
   2.6GB: initrd.img.old
   3.0GB: vmlinuz
   2.5GB: vmlinuz.old
```

---

### Post by oldfred on 2010-03-03
You have wubi. Do not install grub to the MBR as wubi boots thru windows. You have to boot into windows and it will give you a choice. You should be able to reset grub to directly boot into Ubuntu by changing some of its settings:

Have you updated your wubi per this site?
Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

settings for grub2:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Buntzilla on 2010-03-03
I updated that wubi file. Here's a new Boot Info Script

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
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6f191570

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              80,325    16,120,260    16,039,936   7 HPFS/NTFS
/dev/sda3          16,121,856    30,799,871    14,678,016   f W95 Ext d (LBA)
/dev/sda5          16,123,904    30,799,871    14,675,968   7 HPFS/NTFS
/dev/sda4    *     30,800,325   488,395,119   457,594,795   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       5e9b6450-c1f1-45b9-90e0-dc61620099ae   ext4                                     
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        58B27D48B27D2C1E                       ntfs       RECOVERY                      
/dev/sda4        30667F93667F5914                       ntfs       OS                            
/dev/sda5        36841EE6841EA7FF                       ntfs       Ubuntu                        

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /host                    fuseblk    (rw)


======================== sda5/Wubi/boot/grub/grub.cfg: ========================

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
set default="0"
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
    insmod ntfs
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 36841ee6841ea7ff
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 36841ee6841ea7ff
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod ntfs
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 36841ee6841ea7ff
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 36841ee6841ea7ff
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda4)" {
    insmod ntfs
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 30667f93667f5914
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
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda5/Wubi: Location of files loaded by Grub: =================


   3.4GB: boot/grub/grub.cfg
   2.6GB: boot/initrd.img-2.6.31-14-generic
   3.4GB: boot/initrd.img-2.6.31-19-generic
   2.5GB: boot/vmlinuz-2.6.31-14-generic
   3.0GB: boot/vmlinuz-2.6.31-19-generic
   3.4GB: initrd.img
   2.6GB: initrd.img.old
   3.0GB: vmlinuz
   2.5GB: vmlinuz.old
```

---

### Post by Buntzilla on 2010-03-03
Is there a way to disable the windows Boot manager?

---

### Post by Buntzilla on 2010-03-03
Maybe i'm just a noob, but no of this seems to be working.

I still have 2 boot menus.

When I turn my computer on (or restart) the regular Dell Bios screen  splashes, then it goes right to the Windows Boot Manager.
 
If I select Windows, it loads straight into Windows 7 like normal.
 
If I select Ubuntu, it then brings up the GNU Grub Boot screen.

If I select Windows on the Grub Boot Screen, it takes me back to the Windows Boot Manager
 
I would prefer to have a single boot screen. Don't really care which,  although given **jsriz**'s response I think i'd prefer the grub menu  (as I want to customize it).
 
I have Ubuntu installed on a seperate partition then Win 7 if that makes  a difference.

---

### Post by Miljet on 2010-03-03
Your computer is doing exactly what it is supposed to do! If you want to do away with one of the boot loaders, you need to install Ubuntu side-by-side with Windows, NOT inside Windows with Wubi.

---

### Post by Buntzilla on 2010-03-03
> **Miljet said:**
> Your computer is doing exactly what it is supposed to do! If you want to do away with one of the boot loaders, you need to install Ubuntu side-by-side with Windows, NOT inside Windows with Wubi.

I'm confused, isn't Ubuntu installed on a separate partition?

Also, do you mean I would have to fully uninstall Ubuntu? Then what, reinstall? How does that change things?

---

### Post by Sef on 2010-03-04
> I'm confused, isn't Ubuntu installed on a separate partition?

No. It is installed as a file on Windows.  

> Also, do you mean I would have to fully uninstall Ubuntu? Then what,  reinstall? How does that change things? 	

If you would want Ubuntu on a separate partition, you would have to uninstall Wubi and then install Ubuntu on a separate partition.

---

### Post by Buntzilla on 2010-03-04
> **Sef said:**
> No. It is installed as a file on Windows. 
 But it shows up in the partition I created. my E:\ drive
 
>  
If you would want Ubuntu on a separate partition, you would have to uninstall Wubi and then install Ubuntu on a separate partition
 
When I log into windows, I can see the WUBI uninstaller on my E:\ drive.
 
I just want to make sure I have this. If I uninstall that, i'm basically uninstalling Ubuntu.
 
Then I would reboot with the Ubuntu disk and re-install in that fashion?

---

### Post by oldfred on 2010-03-04
Ubuntu runs on its file system which is ext3 or ext4. It can use others. But wubi is intended as an easy install for windows users to try it out and see it they like it. It can be easily installed since it is like a program installed in windows. It avoids the issue of partitioning which most new users are afraid of since it runs inside root.disk. There are ways to put root.disk on a separate partition, create a grub only partition and directly boot the wubi partition. Not partiticularly easy and it would be better to do a full install with a root (/) partition and a swap partition.

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
See info on windows resizing, but do not agree with grub2 complaints
[http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes](http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes)

---

