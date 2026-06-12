---
title: "Having trouble with Win7 + Ubuntu"
date: 2010-03-01
forum: General Help
---

### Post by FatalIll on 2010-03-01
I have had Windows 7 installed for a while now, and when I originally installed it I left a sizeable partition for Ubuntu down the road.     I finally got around to installing Ubuntu and it installed onto the partition just fine, no errors or anything. I rebooted after installation like it asked and was expecting to see GRUB like I had when I had XP.    Much to my surprise it was not there, I rebooted, and it still wasnt there, I dont know what else to do right now for as I dont like playing around with BIOS and bootloaders.     Something I will NOT do, is uninstall windows, if thats what it comes down to I will find something else to put in ubuntu's spot.

---

### Post by Objekt on 2010-03-01
No, you definitely don't have to uninstall Windows 7 for Ubuntu to work correctly.  I have had two systems with both Windows 7 and some version of Ubuntu on them.

It sounds like your computer is skipping the part where you would normally see a GRUB menu, instead going straight to the Windows 7 bootloader.  Please give us a little more info about your setup:

-What version of Ubuntu did you install?
-Tell us about your computer.  How many hard drives?

Your problem could be something really simple, like GRUB not being installed on the hard drive that the BIOS considers "number one" at boot time.

---

### Post by oldfred on 2010-03-01
Just so we can see exactly what is where, download and run this script:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by FatalIll on 2010-03-01
I didnt even think about checking BIOS boot priority, I will do that next reboot which isnt for a while. I was thinking its maybe because I have a SATA Card that also has a little bootscreen, but the drive that is hooked up to that through raid has nothing but data, no OS on it.  EDIT: Checked boot priority, all seems to be in good order... When I get the time again, I will try the Boot Info thing posted above.

---

### Post by FatalIll on 2010-03-02
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=f72b7ae0-8f85-4b62-8c15-39af8cf43abb)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

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
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
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
/dev/sdb5        f72b7ae0-8f85-4b62-8c15-39af8cf43abb   ext4                                     
/dev/sdb6        c22e65fd-eeed-4809-b4a4-c4d45bf5ad51   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


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
insmod ext2
set root=(hd1,5)
search --no-floppy --fs-uuid --set f72b7ae0-8f85-4b62-8c15-39af8cf43abb
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
    search --no-floppy --fs-uuid --set f72b7ae0-8f85-4b62-8c15-39af8cf43abb
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f72b7ae0-8f85-4b62-8c15-39af8cf43abb ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set f72b7ae0-8f85-4b62-8c15-39af8cf43abb
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f72b7ae0-8f85-4b62-8c15-39af8cf43abb ro single 
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
UUID=f72b7ae0-8f85-4b62-8c15-39af8cf43abb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=c22e65fd-eeed-4809-b4a4-c4d45bf5ad51 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 120.4GB: boot/grub/core.img
 120.4GB: boot/grub/grub.cfg
 117.6GB: boot/initrd.img-2.6.31-14-generic
 117.6GB: boot/vmlinuz-2.6.31-14-generic
 117.6GB: initrd.img
 117.6GB: vmlinuz
```


sda drive is now just used for data, no booting on it. Windows XP/Server 2003 dont exist anymore, they arent set to boot ever.
GRUB appears to be installed but its not... working?

---

### Post by thematrixuum on 2010-03-02
same like me.. when I already done the boot_info_script, the output is this : 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe5ce044f

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   104,856,254   104,856,192  83 Linux
/dev/sda2    *    104,856,255   227,737,439   122,881,185   7 HPFS/NTFS
/dev/sda3         227,737,440   613,265,309   385,527,870   7 HPFS/NTFS
/dev/sda4         613,265,310   625,137,344    11,872,035   5 Extended
/dev/sda5         613,265,373   625,137,344    11,871,972  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        521b413b-5a2b-4dcf-9d59-8c6a3f539d31   ext4                                     
/dev/sda2        7D2155B33FB88A69                       ntfs                                     
/dev/sda3        34B60F4853498776                       ntfs                                     
/dev/sda5        3ea50c4b-c5a6-47ac-bccf-5170d1e62ee0   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /media/7D2155B33FB88A69  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda3        /media/34B60F4853498776  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 521b413b-5a2b-4dcf-9d59-8c6a3f539d31
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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 521b413b-5a2b-4dcf-9d59-8c6a3f539d31
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=521b413b-5a2b-4dcf-9d59-8c6a3f539d31 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 521b413b-5a2b-4dcf-9d59-8c6a3f539d31
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=521b413b-5a2b-4dcf-9d59-8c6a3f539d31 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 521b413b-5a2b-4dcf-9d59-8c6a3f539d31
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=521b413b-5a2b-4dcf-9d59-8c6a3f539d31 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 521b413b-5a2b-4dcf-9d59-8c6a3f539d31
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=521b413b-5a2b-4dcf-9d59-8c6a3f539d31 ro single 
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
if [ ${timeout} != -1 ]; then
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=521b413b-5a2b-4dcf-9d59-8c6a3f539d31 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3ea50c4b-c5a6-47ac-bccf-5170d1e62ee0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  13.6GB: boot/grub/core.img
  13.6GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
   1.5GB: boot/initrd.img-2.6.31-19-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
   1.5GB: boot/vmlinuz-2.6.31-19-generic
   1.5GB: initrd.img
    .5GB: initrd.img.old
   1.5GB: vmlinuz
    .5GB: vmlinuz.old

=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
```

It detects the Windows 7 but everytime I reboot, it goes directly into Ubuntu instead of list.

---

### Post by FatalIll on 2010-03-02
> **thematrixuum said:**
> It detects the Windows 7 but everytime I reboot, it goes directly into Ubuntu instead of list.  And mine is the exact opposite, what the hell goes on.

---

### Post by oldfred on 2010-03-03
Your windows still have some files in the boot directory sda2 that may confuse windows, a wubi loader and grub2 file.

Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                      [COLOR=DarkRed] /grldr /boot/grub/core.img[/COLOR]

I would delete these files unless you are still using wubi (/grldr). Then do a sudo update-grub and it should find your windows.

---

### Post by FatalIll on 2010-03-03
> **oldfred said:**
> Your windows still have some files in the boot directory sda2 that may confuse windows, a wubi loader and grub2 file.

Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                      [COLOR=DarkRed] /grldr /boot/grub/core.img[/COLOR]

I would delete these files unless you are still using wubi (/grldr). Then do a sudo update-grub and it should find your windows.

Possible for noob-proof instructions? :| I dont have much experience with boot managers let alone doing anythign with them in Ubuntu.

---

### Post by oldfred on 2010-03-03
From a boot, use places (Nautilus browser) and open your windows partition and delete the files like you would delete anything else.

---

### Post by FatalIll on 2010-03-03
> **oldfred said:**
> From a boot, use places (Nautilus browser) and open your windows partition and delete the files like you would delete anything else.

This can be done from Ubuntu LiveCD? Because, I cant boot into the installed Ubuntu, and that is the problem. Keep in mind I want to keep both Windows 7 and Ubuntu.

---

### Post by oldfred on 2010-03-03
From a liveCD or since the files are in Windows from windows.

---

### Post by FatalIll on 2010-03-03
> **oldfred said:**
> From a liveCD or since the files are in Windows from windows.

Im so confused.

---

### Post by deadlockedgamer on 2010-03-03
Hey for future reference, use the entire disk for windows. Then just make sure everything is def-ragged. The ubuntu installer on the live cd will then give the option to create a part-ion and dual boot. This should avoid your current problem. However for now I suggest getting someone on this forum who know how to manually install grub to help you install grub on the boot part-ion and add your ubuntu part-ion to the boot! This can be done with a live cd and so can the other suggestion. If I had experience with manual grub install I would help!  BTW grub is the boot loader that replaces the windows one. A boot loader is a program that tell your computer were to find the os. Grub allows you to boot both window and linux!

---

### Post by FatalIll on 2010-03-04
I would like a step-by-step if its possible, since I doubt myself with these things.

---

### Post by FatalIll on 2010-03-05
Someone?

---

### Post by oldfred on 2010-03-06
Are you not able to use the file browser to delete files?

---

