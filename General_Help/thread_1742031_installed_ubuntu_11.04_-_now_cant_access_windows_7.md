---
title: "installed ubuntu 11.04 - now cant access windows 7 BOOTMGR IS MISSING Press Ctrl + Al"
date: 2011-04-28
forum: General Help
---

### Post by kaisar89 on 2011-04-28
Hi, since i installed ubuntu 11.04 last night i cant seem to access my Windows 7 OS. When i hold shift at start up to access grub menu i cant see windows 7 at all, ubuntu and ubuntu recovery show up but not windows 7. i tried disabling the hard drive with ubuntu on it through Bios menu but then i get the following message:
BOOTMGR IS MISSING
Press Ctrl + Alt + Del to restart

What do i have to do for Windows 7 to work again? I can access the my windows 7 folder and files. (screenshot attached showing files) Please help

The 2 following hard drive installed in pc:
Sata Maxtor 160GB HDD - windows 7
IDE? Fujitsu siemens 19.4GB HDD - Ubuntu 11.04

I have attached to screenshots along with this thread, ones is of the list of hard drive installed on my computer; the second is of my windows files which i able to access through ubuntu.

---

### Post by sikander3786 on 2011-04-28
From within Ubuntu, please download and run the bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would generated a Results.txt file at your desktop. Copy/paste all text from that file in your post. Click # icon in post menu to generate the [code] tags and paste your text in between them for readability purposes.

It would let us take a look at your boot setup and thus diagnose the problem.

---

### Post by sepo on 2011-04-28
It was a fresh install of 11.04 on a windows7 machine ? Did you use wubi?

Try here:
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions)
to recover windows (and possibly lose your Ubuntu partition; then maybe you can reinstall it)

---

### Post by kaisar89 on 2011-04-28
> **sikander3786 said:**
> From within Ubuntu, please download and run the bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would generated a Results.txt file at your desktop. Copy/paste all text from that file in your post. Click # icon in post menu to generate the [code] tags and paste your text in between them for readability purposes.

It would let us take a look at your boot setup and thus diagnose the problem.

Hi, Thanks for the reply, i tried to run the follow your instruction but i dont think it worked. i attached the screenshot of the codes i followed which i entered into terminal. please take a look. Thank You.

---

### Post by kaisar89 on 2011-04-28
> **sepo said:**
> It was a fresh install of 11.04 on a windows7 machine ? Did you use wubi?

Try here:
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions)
to recover windows (and possibly lose your Ubuntu partition; then maybe you can reinstall it)

previously i had windows 7 OS installed. 

[http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/) i download 32bit version of ubuntu from this link. i then placed it on a bootable usb stick and then installed the OS.

---

### Post by sikander3786 on 2011-04-28
Are you sure the downloaded file is there on your desktop? If it is in the downloads directory, drag it to your desktop and please re-run the command.

---

### Post by kaisar89 on 2011-04-28
> **sikander3786 said:**
> Are you sure the downloaded file is there on your desktop? If it is in the downloads directory, drag it to your desktop and please re-run the command.

i have attached the text file generated


    Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2d.
 => Syslinux is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdh
 => No boot loader is installed in the MBR of /dev/sdi

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdh1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdi1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdi1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdi1 starts at sector 2048. According to the info in 
                       the boot sector, sdi1 has -387940352 sectors.. But 
                       according to the info from the partition table , it 
                       has 3907026943 sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 19.4 GB, 19444562432 bytes
255 heads, 63 sectors/track, 2364 cylinders, total 37977661 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    34,850,815    34,848,768  83 Linux
/dev/sda2          34,852,862    37,976,063     3,123,202   5 Extended
/dev/sda5          34,852,864    37,976,063     3,123,200  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2    *        206,848   312,575,999   312,369,152   7 HPFS/NTFS


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 3965 MB, 3965190144 bytes
3 heads, 32 sectors/track, 80672 cylinders, total 7744512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdh1    *          2,048     7,743,487     7,741,440   7 HPFS/NTFS


Drive: sdi ___________________ _____________________________________________________

Disk /dev/sdi: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdi1    *          2,048 3,907,028,991 3,907,026,944   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        806e86ab-411b-48fc-a091-f4b556f7f86c   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        d17d6a58-1599-46f1-b9c2-a09e375d66b0   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C49C4F7F9C4F6ACE                       ntfs       System Reserved               
/dev/sdb2        08E8546FE8545CCE                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdh1        624604C60EE1F57F                       ntfs                                     
/dev/sdh: PTTYPE="dos" 
/dev/sdi1        E05D-3EA7                              vfat                                     
/dev/sdi: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdh1        /media/624604C60EE1F57F  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb2        /media/08E8546FE8545CCE  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdi1        /media/E05D-3EA7         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 806e86ab-411b-48fc-a091-f4b556f7f86c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 806e86ab-411b-48fc-a091-f4b556f7f86c
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
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
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 806e86ab-411b-48fc-a091-f4b556f7f86c
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=806e86ab-411b-48fc-a091-f4b556f7f86c ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 806e86ab-411b-48fc-a091-f4b556f7f86c
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=806e86ab-411b-48fc-a091-f4b556f7f86c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 806e86ab-411b-48fc-a091-f4b556f7f86c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 806e86ab-411b-48fc-a091-f4b556f7f86c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d17d6a58-1599-46f1-b9c2-a09e375d66b0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  15.1GB: boot/grub/core.img
    .2GB: boot/grub/grub.cfg
   5.5GB: boot/initrd.img-2.6.38-8-generic
  15.4GB: boot/vmlinuz-2.6.38-8-generic
   5.5GB: initrd.img
  15.4GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg #

---

### Post by sikander3786 on 2011-04-28
I am unsure about the text in red.

> => Grub 2 is installed in the MBR of /dev/sda and looks for [COLOR="Red"]b2d[/COLOR].

This is appearing for the first time with Natty I think. Might be some other member can shed some light on this.

And how was Syslinux bootloader installed in the MBR of your Windows HDD? Strange.

> => Syslinux is installed in the MBR of /dev/sdb

Anyways, the easiest fix for you is to disconnect your Ubuntu HDD (or even leave it connected) and boot a Windows 7 installation/recovery disc and perform startup repair 3 times at least. Then test Windows 7 boot independent of Grub by selecting your Windows HDD as the first boot device in Bios.

Once you are able to boot Windows successfully, boot Ubuntu and run this command in a Terminal.

```
sudo update-grub
```

If Windows is listed in the output, everything is good and you can dual-boot.

If you don't have the install/recovery disc, you can download legit ones here.

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

For repairing the Windows startup,

[http://windows.microsoft.com/en-US/windows7/What-are-the-system-recovery-options-in-Windows-7](http://windows.microsoft.com/en-US/windows7/What-are-the-system-recovery-options-in-Windows-7)

If that doesn't sort out the issue, try using command line.

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by oldfred on 2011-04-28
With grub2 1.99 the boot script version 55 has issues. Gert was working on a new version, but had to take a few weeks off. Last test version seemed to work well for me, but he has not released it yet.

Get last development version of Boot Info Script:
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'

Is the sda 19.4GB drive an old IDE and the 160GB drive a newer SATA? Your install in windows may have just been installed to hd0 or sda and then when you plugged in the new(old) drive it was promoted to sda, and now windows does not know where to boot from since it is hd1 or sdb in Linux. The repairs should fix it but I think you may have to have both drives installed. Or if you unplug the old drive you may have to fix it again. Or it may just work if old drive unplugged.

---

### Post by kaisar89 on 2011-04-28
> **oldfred said:**
> With grub2 1.99 the boot script version 55 has issues. Gert was working on a new version, but had to take a few weeks off. Last test version seemed to work well for me, but he has not released it yet.

Get last development version of Boot Info Script:
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'

Is the sda 19.4GB drive an old IDE and the 160GB drive a newer SATA? Your install in windows may have just been installed to hd0 or sda and then when you plugged in the new(old) drive it was promoted to sda, and now windows does not know where to boot from since it is hd1 or sdb in Linux. The repairs should fix it but I think you may have to have both drives installed. Or if you unplug the old drive you may have to fix it again. Or it may just work if old drive unplugged.

i installed ubuntu on 19.4GB IDE hard drive which i took out of old computer and decided i might as well put it to use by installing Ubuntu 11.04.

previously i had sata maxtor 160gb hard drive with windows 7 installed.

what do i need to install again, do i need to copy'n'paste the following into terminal.

wget -O boot_info_script.sh  'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'

---

### Post by Quackers on 2011-04-28
Yes, then a new version of the boot script will be put in your home folder. Just then run the command ```
sudo bash newbootscriptname
``` in the terminal. The results.txt file will then appear in your home folder.

---

### Post by kaisar89 on 2011-04-28
> **Quackers said:**
> Yes, then a new version of the boot script will be put in your home folder. Just then run the command ```
sudo bash newbootscriptname
``` in the terminal. The results.txt file will then appear in your home folder.

hi, i just entered the first code, and a file was created in home folder, but the code below has not worked, i have attached a screenshot with this post
sudo bash newbootscriptname

---

### Post by oldfred on 2011-04-28
It is not literally newbootscript. It actually is the same without the 055 at the end.

 sudo bash boot_info_script.sh

If you type sudo bash and boo then hit tab, it will autocomplete or complete as far as it is unique.

sudo bash boo{tab}

---

### Post by kaisar89 on 2011-04-28
> **oldfred said:**
> It is not literally newbootscript. It actually is the same without the 055 at the end.

 sudo bash boot_info_script.sh

If you type sudo bash and boo then hit tab, it will autocomplete or complete as far as it is unique.

sudo bash boo{tab}

i follwoed your instructions, i took a screenshot of the terminal once i entered the codes. i have attached both screenshot and the file created.

---

### Post by kaisar89 on 2011-04-28
bump plz help

---

### Post by oldfred on 2011-04-28
Have you tried the windows repairs?

Have you run from Ubuntu

```
sudo update-grub
```

New version of boot script is not a lot different. It does show grub in sda is ok. You should have a windows boot loader in sdb's MBR not syslinux. Which the windows repairs should fix.

With a 2TB external why are you messing with a 20GB drive? And why is the external FAT? You cannot store files over 4GB and if it develops issues a chkdsk will take days since it has no journal. Some do need it for Xbox or compatibility with a Mac, but I would not dedicate 2TB to that.

---

### Post by kaisar89 on 2011-04-28
> **oldfred said:**
> Have you tried the windows repairs?

Have you run from Ubuntu

```
sudo update-grub
```New version of boot script is not a lot different. It does show grub in sda is ok. You should have a windows boot loader in sdb's MBR not syslinux. Which the windows repairs should fix.

With a 2TB external why are you messing with a 20GB drive? And why is the external FAT? You cannot store files over 4GB and if it develops issues a chkdsk will take days since it has no journal. Some do need it for Xbox or compatibility with a Mac, but I would not dedicate 2TB to that.

I use the 2TB hard drive to store movies to watch on ps3 and xbox. if only other formats were compatiable with both the consoles. and regarding the small hard drive, i thought i might as well put it to use, i took the hdd from old computer which has been in the attic for about 4/5 yrs.

thanks anyways, the code sudo update-grub seems to have solved the problem.

cheerz thanks everyone.

---

