---
title: "Problems with Windows 7/Ubuntu 10.10 dual-boot: Windows 7 can't find Ubuntu partition"
date: 2011-04-08
forum: General Help
---

### Post by SkinnyLuigi on 2011-04-08
Hello everyone,

I am trying to install Ubuntu 10.10 alongside a Windows 7 installation and it is not going well.

After much problems with the Ubuntu installer not being able to recognize the hard disk, I finally managed to fix that problem (plugged drive into a different SATA port) and partition off part of my main drive and install Ubuntu. The problem is that the computer, on reboot, boots directly into Windows 7... I poked around in a few places and found this:

[http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/](http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/)

The problem is that I cannot get passed the step where I have to open a command prompt and use BCDEdit to point my Ubuntu bootloader thing to the right drive; there's no way for me to do this step.

When I right click "My computer" and go to "manage", I am able to see the Ubuntu partition (I know by its size) but there is no drive letter and it won't let me set one.

I tried restarting the computer and the boot-up screen does show both Windows 7 and Ubuntu, but selecting Ubuntu boots up into a DOS-Prompt-ish looking terminal which I guess is "Grub" (sorry, I'm fairly new to Linux).

Can anyone help? I understand sometimes Windows 7 can't see the Linux partition because its formatted as ext4 (mine is) and not FAT32 or NTSC.

Is there any solution for this?

Thanks everyone!

--Skinny

---

### Post by uRock on 2011-04-08
Hello and welcome to the forums,

What are your system specs?

Cheers,
uRock

---

### Post by Hedgehog1 on 2011-04-09
Deleted - I was going the wrong direction...

---

### Post by SkinnyLuigi on 2011-04-09
Hi, sorry but I am not 100% sure what specs would help

Sabertooth x58 motherboard, 64bit Windows7, 12gb ram, i7 quadcore, hard disk is an SSD in a Sata2 slot.  Main partition's format is NTSC fow Win7 and the Ubuntu partition is ext4. I haven't played around much with boot options or the bios.  Does that help at? Is there any other information that would be helpful?

Partition sizes are 60 gb for Windows and 20gb for Ubuntu.

Thanks!

---

### Post by Hedgehog1 on 2011-04-09
OK - this time I really mean it...

Please boot off the LiveCD/LiveUSB, select TRY, and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.


***The Hedge***

:KS

---

### Post by SkinnyLuigi on 2011-04-09
Okay, so I ran the script as instructed in the link given in the last post. Here is the output.

Any help really appreciated!! Thanks everyone!

----------------------------------------------------------------------------------------------------------
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 3,907,023,962 3,907,021,915   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   117,467,781   117,260,934   7 HPFS/NTFS
/dev/sdb3         117,469,182   156,301,311    38,832,130   5 Extended
/dev/sdb5         156,114,944   156,301,311       186,368  82 Linux swap / Solaris
/dev/sdb6         117,469,184   155,926,527    38,457,344  83 Linux
/dev/sdb7         155,928,576   156,102,655       174,080  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3404CA2A04C9EF44                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3E669D87669D4097                       ntfs       System Reserved               
/dev/sdb2        A8869E70869E3F2E                       ntfs                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        321ea770-71d1-4f2d-a9db-44231a747a4b   swap                                     
/dev/sdb6        3ef4ba29-35a0-4e6e-9b71-06cd9c115860   ext4                                     
/dev/sdb7        2b1a88f6-a658-4b7e-8d87-21b40fbeaf45   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 3ef4ba29-35a0-4e6e-9b71-06cd9c115860
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 3ef4ba29-35a0-4e6e-9b71-06cd9c115860
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
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 3ef4ba29-35a0-4e6e-9b71-06cd9c115860
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3ef4ba29-35a0-4e6e-9b71-06cd9c115860 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 3ef4ba29-35a0-4e6e-9b71-06cd9c115860
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3ef4ba29-35a0-4e6e-9b71-06cd9c115860 ro single 
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
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 3ef4ba29-35a0-4e6e-9b71-06cd9c115860
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 3ef4ba29-35a0-4e6e-9b71-06cd9c115860
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 3e669d87669d4097
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

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=2b1a88f6-a658-4b7e-8d87-21b40fbeaf45 none            swap    sw              0       0

=================== sdb6: Location of files loaded by Grub: ===================


  71.1GB: boot/grub/core.img
  62.6GB: boot/grub/grub.cfg
  61.5GB: boot/initrd.img-2.6.35-22-generic
  71.1GB: boot/vmlinuz-2.6.35-22-generic
  61.5GB: initrd.img
  71.1GB: vmlinuz
```

---

### Post by uRock on 2011-04-09
> **SkinnyLuigi said:**
> Hi, sorry but I am not 100% sure what specs would help

What graphics card do you have?

---

### Post by oldfred on 2011-04-09
Have you tried booting from sda? In BIOS change drives or just to try it, use your one time boot key (mine is f12).

You have all your operating systems on one 80GB drive and just data on your sda 2TB drive?

Just for info - except I have Ubuntu on every drive (except my old winXP drive).
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

---

### Post by SkinnyLuigi on 2011-04-09
Hi everyone,

I will try the last suggestion when I get a chance, thanks!


As for the two further questions posed:

My graphics cards is a [FONT=MS Sans Serif, Verdana, Arial][SIZE=1]XFX Radeon HD  5830.[/SIZE][/FONT]

And yes, all my OS's (just Windows 7 and Ubuntu) are on the 80GB SSD, and the data is all on the other drive.

I will try the previous suggestion and report back.

Thanks again!


R

---

