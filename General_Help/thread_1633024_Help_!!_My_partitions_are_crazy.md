---
title: "Help !! My partitions are crazy"
date: 2010-11-28
forum: General Help
---

### Post by linguine89 on 2010-11-28
I recently installed 10.10 netbook remix on my Samsung N150 netbook alongside Windows 7 Starter. 

At the time of the first installation one of the forward buttons wasn't showing up so I was stuck and had to reboot and restart the installation. This happened after I had made the partition for Ubuntu so when I got back to that stage in installation there was already a partition made. I tried to delete the previous partition but it kept coming back so I made another partition for Ubuntu and installed it. 

It was working fine apart from a problem with the right-click and dragging icons. Then I updated the grub and after restarting the machine my grub disappeared and I was left with a black screen with a blinking cursor. 

I reinstalled Ubuntu again using my external HD with new partitions (the same thing happened where the partitions kept coming back after trying to delete). Now my Windows won't load up and just goes straight to recovery. After I restored it the grub disappeared again.

Any suggestions for how to solve the partition problem and the Windows problem ? How do I fix my MBR ?

Thanks,
Matilda x

---

### Post by sanderd17 on 2010-11-28
what is your current situation? A working windows starter and a broken ubuntu?

can you put in a live disk, don't install ubuntu and run
```

sudo parted -l

```
and post the output (you can copy-paste by selecting the text and middle clicking where it need to come, or with CTRL+SHIFT+C and CTRL+SHIFT+V) or, if you can't run the command, post a screenshot of the gparted program.

This way, we can see what your current partitions are.

---

### Post by johnmay on 2010-11-28
My suggestion: From your UBUNTU install DVD remove the ubuntu partition and see if windows loads, try safe mode first. 

After you get windows to load, repartition with ubuntu.

---

### Post by linguine89 on 2010-11-28
[IMG]http://i170.photobucket.com/albums/u273/sebmel/Screenshot.png[/IMG]

---

### Post by linguine89 on 2010-11-28
I am now running Ubuntu from a live USB and Windows isn't working
Thanks for the help

---

### Post by sanderd17 on 2010-11-28
ooooh damn, that's really a lot of work to repair it.

Do you have data to lose? Or can you just install a fresh windows and ubuntu?

In the last case, do a fresh install of windows, after the installation, boot windows a few times, and as the last step, install ubuntu. When you come to the last step, please ask help if you need any.

---

### Post by DogMatix on 2010-11-28
Have you got a Windows Recovery Disk?

---

### Post by sikander3786 on 2010-11-28
From your output above, I can see Windows partitions are there so you may be able to get it back.

But your partitioing setup looks pretty much messed up. 3 swap partitions, 2 Linux partitions and an NTFS partition in the Extended one. I don't know if that was meant to be there or not.

As **sanderd17** mentioned above, you may want to re-install Ubuntu as that is a fresh install and not a lot of configuration/settings involved.

Regarding a re-install for Windows, I hope that can be fixed. If you've got some data and settings on Windows, post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us exactly about your Windows boot files, if they are there and not and whether they can be repaired.

Please wrap your output using proper code tags # from the post menu. [/code] at the end and [code] at the beginning.

---

### Post by linguine89 on 2010-11-28
I backed up my files so that's ok, but I don't have any recovery disc and my netbook doesn't have a CD-ROM. The problem I have right now I can't boot any of my OS and my bootloader wont load, is there anyway around that ?

---

### Post by sikander3786 on 2010-11-28
Is there supposed to be a recovery partition on your Netbook?

---

### Post by linguine89 on 2010-11-28
Yes there is. I tried to restore Windows but the bootloader didn't load and I was back to square one. Here is the boot info.
Thanks

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #10 for (,msdos10)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 2048.
    Operating System:  
    Boot files/dirs:

---

### Post by sikander3786 on 2010-11-28
Google "Windows 7 recovery disc" and you'll find one. Download it, burn to a disc or USB and perform Startup repair 3 times. Yes thats right, 3 times.

And the output you posted is not complete. Please edit your post, add the remaining text and type [/code] at the end and [code] at the start of that text.

We need to see the boot flags necessary for booting Windows and the output for them is in the same file you partially posted ;-)

---

### Post by mikewhatever on 2010-11-28
> **linguine89 said:**
> I backed up my files so that's ok, but I don't have any recovery disc and my netbook doesn't have a CD-ROM. The problem I have right now I can't boot any of my OS and my bootloader wont load, is there anyway around that ?

It looks like the only way to fix it is deleting the redundant partitions and reinstalling Ubuntu.

Try launching Gparted with the following command:
**gksudo gparted**

Delete all ext4 and swap partitions, then close Gparted and reinstall Ubuntu.

---

### Post by linguine89 on 2010-11-28
Sorry, it would let me post it because it thought it was uploading pictures so I just posted the parts that looked important :P

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #10 for (,msdos10)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 2048.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    41,945,087    41,943,040  27 Hidden HPFS/NTFS
/dev/sda2    *     41,945,088    42,149,887       204,800   7 HPFS/NTFS
/dev/sda3          42,149,888   134,326,550    92,176,663   7 HPFS/NTFS
/dev/sda4         134,328,318   312,580,095   178,251,778   f W95 Ext d (LBA)
/dev/sda5         232,992,768   273,461,770    40,469,003   7 HPFS/NTFS
/dev/sda6         134,328,320   181,730,063    47,401,744  83 Linux
/dev/sda7         228,866,048   232,990,719     4,124,672  82 Linux swap / Solaris
/dev/sda8         181,731,328   226,815,999    45,084,672  83 Linux
/dev/sda9         226,818,048   228,861,951     2,043,904  82 Linux swap / Solaris
/dev/sda10        273,463,296   310,857,727    37,394,432  83 Linux
/dev/sda11        310,859,776   312,580,095     1,720,320  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   625,142,447   625,140,400   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       42b1c534-cf23-422b-9284-f6577b3d101e   ext4                                     
/dev/sda11       a7bdc894-78f1-4c5a-8e3d-55e3a4b02d9a   swap                                     
/dev/sda1        24602B5D602B3548                       ntfs       RECOVERY                      
/dev/sda2        226CE1B86CE186BF                       ntfs       SYSTEM                        
/dev/sda3        98202EA4202E8978                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        76D8DDCCD8DD8AAF                       ntfs                                     
/dev/sda6        0d202dfb-1930-4270-9c88-45104ff9aee9   ext4                                     
/dev/sda7        e354b567-9b67-41b8-aff4-5503834f25ca   swap                                     
/dev/sda8        f93ff378-c93b-474d-bcab-3d6dbe0cd42b   ext4                                     
/dev/sda9        4fc8ec4f-f1ba-4478-ba08-660832573738   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5D0B-0F0E                              vfat       New Volume                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=0d202dfb-1930-4270-9c88-45104ff9aee9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=e354b567-9b67-41b8-aff4-5503834f25ca none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  83.9GB: boot/vmlinuz-2.6.35-22-generic
  83.9GB: vmlinuz

=========================== sda8/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set f93ff378-c93b-474d-bcab-3d6dbe0cd42b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set f93ff378-c93b-474d-bcab-3d6dbe0cd42b
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set f93ff378-c93b-474d-bcab-3d6dbe0cd42b
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=f93ff378-c93b-474d-bcab-3d6dbe0cd42b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set f93ff378-c93b-474d-bcab-3d6dbe0cd42b
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=f93ff378-c93b-474d-bcab-3d6dbe0cd42b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set f93ff378-c93b-474d-bcab-3d6dbe0cd42b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f93ff378-c93b-474d-bcab-3d6dbe0cd42b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set f93ff378-c93b-474d-bcab-3d6dbe0cd42b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f93ff378-c93b-474d-bcab-3d6dbe0cd42b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set f93ff378-c93b-474d-bcab-3d6dbe0cd42b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set f93ff378-c93b-474d-bcab-3d6dbe0cd42b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 24602b5d602b3548
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 226ce1b86ce186bf
    chainloader +1
}
menuentry "Ubuntu 10.10 (10.10) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 0d202dfb-1930-4270-9c88-45104ff9aee9
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda6
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

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=f93ff378-c93b-474d-bcab-3d6dbe0cd42b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=4fc8ec4f-f1ba-4478-ba08-660832573738 none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 101.8GB: boot/grub/core.img
  99.8GB: boot/grub/grub.cfg
  94.0GB: boot/initrd.img-2.6.35-22-generic
  94.1GB: boot/initrd.img-2.6.35-23-generic
 101.8GB: boot/vmlinuz-2.6.35-22-generic
 101.9GB: boot/vmlinuz-2.6.35-23-generic
  94.1GB: initrd.img
  94.0GB: initrd.img.old
 101.9GB: vmlinuz
 101.8GB: vmlinuz.old

========================== sda10/boot/grub/grub.cfg: ==========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set 42b1c534-cf23-422b-9284-f6577b3d101e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos10)'
search --no-floppy --fs-uuid --set 42b1c534-cf23-422b-9284-f6577b3d101e
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 42b1c534-cf23-422b-9284-f6577b3d101e
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=42b1c534-cf23-422b-9284-f6577b3d101e ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 42b1c534-cf23-422b-9284-f6577b3d101e
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=42b1c534-cf23-422b-9284-f6577b3d101e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 42b1c534-cf23-422b-9284-f6577b3d101e
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=42b1c534-cf23-422b-9284-f6577b3d101e ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 42b1c534-cf23-422b-9284-f6577b3d101e
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=42b1c534-cf23-422b-9284-f6577b3d101e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 42b1c534-cf23-422b-9284-f6577b3d101e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 42b1c534-cf23-422b-9284-f6577b3d101e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 24602b5d602b3548
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 226ce1b86ce186bf
    chainloader +1
}
menuentry "Ubuntu 10.10 (10.10) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 0d202dfb-1930-4270-9c88-45104ff9aee9
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda6
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda8)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set f93ff378-c93b-474d-bcab-3d6dbe0cd42b
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=f93ff378-c93b-474d-bcab-3d6dbe0cd42b ro quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sda8)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set f93ff378-c93b-474d-bcab-3d6dbe0cd42b
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=f93ff378-c93b-474d-bcab-3d6dbe0cd42b ro single
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda8)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set f93ff378-c93b-474d-bcab-3d6dbe0cd42b
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=f93ff378-c93b-474d-bcab-3d6dbe0cd42b ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda8)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set f93ff378-c93b-474d-bcab-3d6dbe0cd42b
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=f93ff378-c93b-474d-bcab-3d6dbe0cd42b ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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

=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=42b1c534-cf23-422b-9284-f6577b3d101e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda11 during installation
UUID=a7bdc894-78f1-4c5a-8e3d-55e3a4b02d9a none            swap    sw              0       0

=================== sda10: Location of files loaded by Grub: ===================


 146.6GB: boot/grub/core.img
 142.4GB: boot/grub/grub.cfg
 140.9GB: boot/initrd.img-2.6.35-22-generic
 140.9GB: boot/initrd.img-2.6.35-23-generic
 146.6GB: boot/vmlinuz-2.6.35-22-generic
 146.7GB: boot/vmlinuz-2.6.35-23-generic
 140.9GB: initrd.img
 140.9GB: initrd.img.old
 146.7GB: vmlinuz
 146.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  a3 83 17 d7 e0 41 5c 95  f3 68 82 00 23 4e 3b 0f  |.....A\..h..#N;.|
00000010  e6 f4 10 15 75 cc 07 e3  82 c2 5b ff 0d 41 b9 5b  |....u.....[..A.[|
00000020  98 0f 56 39 b5 2f b6 eb  c4 aa 9d 7b d4 d0 57 e1  |..V9./.....{..W.|
00000030  b8 e8 64 dd ae b7 42 ec  75 3b 0f b3 ad 92 84 3f  |..d...B.u;.....?|
00000040  61 60 47 fb 70 c5 7c cd  27 9d cd 1c 3c ca 5a 64  |a`G.p.|.'...<.Zd|
00000050  7d 95 3c 50 fa 11 c6 ce  a2 da 90 79 41 7e 86 1f  |}.<P.......yA~..|
00000060  c8 94 1f 3f d9 f9 65 b1  f1 49 3e 31 55 41 f7 bc  |...?..e..I>1UA..|
00000070  cd 6c 8e 66 f6 03 01 bd  29 85 ef 3b 8d 79 0a 01  |.l.f....)..;.y..|
00000080  b5 71 2f ea 79 74 5f 75  53 b5 52 b8 71 67 ef cd  |.q/.yt_uS.R.qg..|
00000090  01 00 e5 9d 0d 75 80 cf  8d a4 c4 35 ba ac af 5b  |.....u.....5...[|
000000a0  87 64 57 7e a8 b8 a8 81  28 8d 41 c5 e8 3b 5c 00  |.dW~....(.A..;\.|
000000b0  a1 53 c2 8e d1 e2 91 0a  18 01 54 7b dd c1 78 47  |.S........T{..xG|
000000c0  51 2f 76 d6 28 23 9e 6b  c1 b9 bb b1 f7 db a0 56  |Q/v.(#.k.......V|
000000d0  65 ad c9 a8 18 2c 5a cc  96 df d3 2e cf 10 0d d6  |e....,Z.........|
000000e0  b3 bb ac 83 44 be 1d d8  3e 84 3e 2b 1b cb 53 f5  |....D...>.>+..S.|
000000f0  38 3b 09 de 1c 1b 5b 1a  e3 e4 7e be cd 12 43 44  |8;....[...~...CD|
00000100  8b 15 27 35 fd ab d9 fe  69 36 4d 9d fc c7 c0 8b  |..'5....i6M.....|
00000110  56 2f 5a 5c 7d f3 cf 25  78 e4 99 7d db de c9 ed  |V/Z\}..%x..}....|
00000120  fd 4a d4 22 71 06 83 6d  d5 07 36 af 91 74 56 75  |.J."q..m..6..tVu|
00000130  92 87 31 8a c7 9a 99 5c  8c 74 e0 86 af ce f4 96  |..1....\.t......|
00000140  76 61 8a bd 29 28 c7 54  8e f4 99 35 34 83 8e e2  |va..)(.T...54...|
00000150  50 8c 14 90 0f 76 26 21  76 18 9e 03 15 02 99 68  |P....v&!v......h|
00000160  18 bc 14 b4 7f e5 bf d6  c5 46 07 25 35 14 a8 13  |.........F.%5...|
00000170  fe c1 42 c0 e3 0c 7c d3  9e 91 30 6a 63 60 7e b9  |..B...|...0jc`~.|
00000180  79 9d 5b ee 9f 1b d7 61  b6 60 fe e2 07 83 8b fb  |y.[....a.`......|
00000190  87 c1 ed c7 6c 46 63 35  7a 98 98 5c e5 bd b1 4a  |....lFc5z..\...J|
000001a0  cc da f1 d9 6f f1 aa 10  4a 0f 8d de fa 38 05 1e  |....o...J....8..|
000001b0  59 47 39 76 c4 c7 e8 31  ba dd 4b 1e ee b8 00 fe  |YG9v...1..K.....|
000001c0  ff ff 07 fe ff ff 02 80  e1 05 0b 82 69 02 00 fe  |............i...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 11 4b d3 02 00 00  |...........K....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by sikander3786 on 2010-11-28
> **mikewhatever said:**
> It looks like the only way to fix it is deleting the redundant partitions and reinstalling Ubuntu.

Try launching Gparted with the following command:
**gksudo gparted**

Delete all ext4 and swap partitions, then close Gparted and reinstall Ubuntu.
Keeping in mind that Windows is not able to boot successfully, I don't think reinstalling just Ubuntu or Grub would fix the problem. Doesn't the OP first need to fix boot for Windows and then try installing Ubuntu again? What do you say?

All the boot files for Windows seem intact though. Can't say why that isn't booting properly.

---

### Post by mikewhatever on 2010-11-28
Presumably, Windows doesn't boot because nothing points to its bootloader at the moment. Given the situation that the OP can't boot from a cd to fix Windows (it's a netbook and there is no cd), Ubuntu live usb seems the only option.
Just hoping Gparted is included with 10.10 netbook edition.

---

### Post by sikander3786 on 2010-11-28
But when Grub was pointing to Windows, it wasn't able to boot properly either.

From the bootinfoscript Results:
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 24602b5d602b3548
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 226ce1b86ce186bf
    chainloader +1
}

```

To the OP: I still am not convinced if re-installing Ubuntu would fix your problem but as **mikewhatever** mentioned, if there is no other option, you can do nothing else rather than installing Ubuntu again.

---

### Post by linguine89 on 2010-11-28
Installing ubuntu again would mean creating another partition. Would deleting the current ubuntu partitions using gparted damage anything ? Yes 10.10 live usb includes gparted.
Thanks to everyone x

---

### Post by mikewhatever on 2010-11-28
> **linguine89 said:**
> Installing ubuntu again would mean creating another partition. Would deleting the current ubuntu partitions using gparted damage anything ? Yes 10.10 live usb includes gparted.
Thanks to everyone x

Well, just the files on the partitions you delete, and you'll also get rid of six redundant partitions. Be careful not to delete any Windows partitions.

Edit: At which screen does the installation stall? 
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) (click ShowMe for pictures).

---

### Post by DogMatix on 2010-11-28
If you are sure your netbook has a Windows recovery partition it my be worth doing a bit of research (ie. Google) to see if there is a key combo that boots into it. For example, Acer have a hold down Alt+F10 during startup to enter Windows recovery partition.

---

### Post by linguine89 on 2010-11-28
Also, I'm not sure why there is a partition for Vista. As far as I knew the netbook only came with Win7. When I try booting that up it also goes to recovery.

---

### Post by johnmay on 2010-11-28
Maybe try Hiren's Boot CD. Has quite a number of useful tools which might help you.

---

### Post by mikewhatever on 2010-11-28
> **linguine89 said:**
> Also, I'm not sure why there is a partition for Vista. As far as I knew the netbook only came with Win7. When I try booting that up it also goes to recovery.

Likely just a naming convention, but I've also heard W7 to be a big service pack for Vista. Perhaps it's true.

---

### Post by linguine89 on 2010-11-28
I think I'm going to leave it for now and have my more technically minded friend  have a look at it tomorrow. Thanks to all for the help

---

### Post by sanderd17 on 2010-11-29
If you have no way to boot into windows, Samsung should help you. Getting windows of the internet is possible, but you never know what you get.

---

