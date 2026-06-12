---
title: "Grub and boot all messed up"
date: 2010-05-18
forum: General Help
---

### Post by FatalIll on 2010-05-18
I have had Windows 7 and Ubuntu 9.10 side by side on one of my hard drives, and I decided to update Ubuntu to 10.40 LTS and after that I quickly regreted it. I booted the LiveCD, used GParted on Ubuntu 9.10 LiveCD and formatted the Ubuntu 10.40 partition, and installed 9.10 on that space. Install went fine but upon restarting:
[B]"grub_getcharwidth" not found
grub rescue>[/B]

I tried to "insmod normal" and some other commands but it would keep saying **"grub_getcharwidth" not found**

I really would like to be able to use Grub again, or atleast for the time being; be able to get to my Windows part.

> **"Boot info script"]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=d75ecc39-aac6-467a-8f39-e57208bb67ba)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 228991867 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc506c506

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   209,728,574   209,728,512   7 HPFS/NTFS
/dev/sda2         251,674,290   976,768,064   725,093,775   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7d067d06

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   228,691,967   228,485,120   7 HPFS/NTFS
/dev/sdb3         228,701,340   312,576,704    83,875,365   5 Extended
/dev/sdb5         228,701,403   309,042,404    80,341,002  83 Linux
/dev/sdb6         309,042,468   312,576,704     3,534,237  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        04402B96402B8D8C                       ntfs                                     
/dev/sda2        AA34B0EA34B0BAA1                       ntfs                                     
/dev/sdb1        B4F0EC4BF0EC1580                       ntfs       System Reserved               
/dev/sdb2        FE40F12F40F0EF71                       ntfs                                     
/dev/sdb5        d75ecc39-aac6-467a-8f39-e57208bb67ba   ext4                                     
/dev/sdb6        8fa546e2-9648-44c6-bc23-ca79ae215f66   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb5        /media/d75ecc39-aac6-467a-8f39-e57208bb67ba ext4       (rw,nosuid,nodev,uhelper=devkit)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows Server 2003, Standard" /noexecute=alwaysoff /fastdetect /usepmtimer 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows Server 2003, Safe Mode" /noexecute=alwaysoff /fastdetect /usepmtimer /safeboot:minimal 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows Server 2003, Safe Mode Net" /noexecute=alwaysoff /fastdetect /usepmtimer /safeboot:network
=========================== sdb5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ] said:**
> ; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,5)
search --no-floppy --fs-uuid --set d75ecc39-aac6-467a-8f39-e57208bb67ba
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set d75ecc39-aac6-467a-8f39-e57208bb67ba
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=d75ecc39-aac6-467a-8f39-e57208bb67ba ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set d75ecc39-aac6-467a-8f39-e57208bb67ba
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=d75ecc39-aac6-467a-8f39-e57208bb67ba ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
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
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 04402b96402b8d8c
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set b4f0ec4bf0ec1580
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=d75ecc39-aac6-467a-8f39-e57208bb67ba /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=8fa546e2-9648-44c6-bc23-ca79ae215f66 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd2       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 117.6GB: boot/grub/core.img
 117.6GB: boot/grub/grub.cfg
 117.6GB: boot/initrd.img-2.6.31-14-generic
 117.6GB: boot/vmlinuz-2.6.31-14-generic
 117.6GB: initrd.img
 117.6GB: vmlinuz

---

### Post by FatalIll on 2010-05-19
I still need help :(

---

### Post by john newbuntu on 2010-05-19
Follow step # 13 from this post by drs305: 
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
In your case sdXY=sbd5 and sdX=sdb.  Make sure you boot from sdb in BIOS.  Hope this helps.

---

### Post by FatalIll on 2010-05-19
That worked! Thank god :P But where were you last night? Aw man, Made my day.

---

