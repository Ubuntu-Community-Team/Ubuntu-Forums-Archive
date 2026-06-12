---
title: "Recovering back to xp so I can duel boot (grub error)"
date: 2010-11-29
forum: General Help
---

### Post by rjcube on 2010-11-29
I installed the Ubuntu netbook variation on my Asus 1005HA. Decided I rather have a duel boot with windows xp but im having some trouble. My recovery partition is still intact. so on the boot loader I select the windows option and it takes me to the recovery of the computer. Does its thing then reboots, at this point it gives me a grub error and says operating system not found. (I forget the exact error and I reinstalled ubuntu at this point) I assume it needs to be restored to the windows MBR, Being a netbook I don't have a windows CD, or an optical drive for that matter. Searching around I found people that would search for boot files on the different partition but nothing came up on any of mine. (Can't remember the exact errors and what I searched for exactly but another person had a similar problem and searched hd0,hd1,etc for boot files).

I am thinking the problem is it is trying to reinstall windows but once it reboots it is not sure where to go. Restoring a windows MBR might fix it somehow but I cant find how to do that without a windows cd. 

My ultimate goal is to reinstall XP and likely duel boot with ubuntu. (which I should have done in the first place)

Any help is appreciated.

---

### Post by rjcube on 2010-12-01
bump

---

### Post by rjcube on 2010-12-01
accidental double post, my bad

---

### Post by Rubi1200 on 2010-12-01
Hi,
please use a LiveCD to boot the computer and choose to try not install Ubuntu.

Then, click on the link for the boot info script at the bottom of my post (instructions included).

Post the results back here so we can get a better overview of your setup.

Thanks.

---

### Post by rjcube on 2010-12-01
I currently have ubuntu installed, here is the summary with ubuntu insalled. If you want me to try to recover and recreate the error and get the info from the livecd I can do hat no problem. 

```

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
```

---

### Post by Rubi1200 on 2010-12-01
Can I assume Windows XP was on sda4?

If so, something has gone wrong.
> mount: unknown filesystem typeDo you have the installation CD for Windows?

You could try using Testdisk to recover the partition as well:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Also, are you sure you copied/pasted everything from the script? Usually, there is more information.

---

### Post by rjcube on 2010-12-01
Well the recovery partition is probably sda3, no idea what sda4 could be. I don't have a windows CD because my computer didn't come with one, it has no cd drive. It just has the recovery partition. And no, it wasn't all he info, wasn't sure if you needed more than the summary. Heres the whole thing.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,046    39,061,503    39,059,458   5 Extended
/dev/sda5               2,048    39,061,503    39,059,456  82 Linux swap / Solaris
/dev/sda2          39,061,504   302,229,503   263,168,000  83 Linux
/dev/sda3    *    302,230,845   312,480,314    10,249,470   c W95 FAT32 (LBA)
/dev/sda4         312,480,315   312,576,704        96,390  ef EFI (FAT-12/16/32)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda2        653687f6-8ab7-49a5-9088-70e5eeaf8368   ext4                                     
/dev/sda3        CCED-990E                              vfat       PE                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        3b494b31-4386-4867-bbf0-859903b9e32d   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=600)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 653687f6-8ab7-49a5-9088-70e5eeaf8368
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 653687f6-8ab7-49a5-9088-70e5eeaf8368
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 653687f6-8ab7-49a5-9088-70e5eeaf8368
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=653687f6-8ab7-49a5-9088-70e5eeaf8368 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 653687f6-8ab7-49a5-9088-70e5eeaf8368
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=653687f6-8ab7-49a5-9088-70e5eeaf8368 ro single 
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
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 653687f6-8ab7-49a5-9088-70e5eeaf8368
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 653687f6-8ab7-49a5-9088-70e5eeaf8368
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda3)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set cced-990e
    drivemap -s (hd0) ${root}
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=653687f6-8ab7-49a5-9088-70e5eeaf8368 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3b494b31-4386-4867-bbf0-859903b9e32d none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


 146.8GB: boot/grub/core.img
  50.2GB: boot/grub/grub.cfg
  20.5GB: boot/initrd.img-2.6.35-22-generic
 146.8GB: boot/vmlinuz-2.6.35-22-generic
  20.5GB: initrd.img
 146.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 5d  |...............]|
000001c0  03 00 82 e3 d6 ff 02 00  00 00 00 00 54 02 00 00  |............T...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by Rubi1200 on 2010-12-02
Hi,
thanks for the full text.

Not sure what to tell you; if Ubuntu is booting normally (which it seems it should do based on the script), then the problem is recovering Windows. However, if you run the recovery partition I would think it will put the Windows bootloader back in the MBR, leaving Ubuntu unavailable.

I suggest you wait and see if other users have some ideas about this.

---

