---
title: "GRUB2 problems"
date: 2010-11-27
forum: General Help
---

### Post by goplayer on 2010-11-27
Hello,

I have ubuntu 10.04LTS installed on an external USB drive and so is grub2. Yesterday I updated some software that were recommended by the update manager. Grub2 was among the software updated. When I restarted the system I got the grub shell--no bootmenu. 
I was able to boot by typing:

set root=(hd0,1)
linux /boot/vmlinuz-2.6.32-26-generic-pae root=/dev/sdb1 ro
initrd /boot/initrd.img-2.6.32-26-generic-pae
boot

I looked in grub.cfg file and the root was set to (hd1,1)
I edited the 40_custom file and put the commands (minus boot) that worked. and updated grub2 and again no boot menu. I edited the grub.cfg file (yes I know you're not supposed to do that) and changed (hd1,1) to (hd0,1) again to no avail. 
Finally I had to uninstall grub2 and installed the legacy grub and every thing works fine the root is set to (hd0,0). 
The question I have is there a bug in grub2? Is it a problem staying with legacy grub? How can I solve the issue with grub2?

Thanks.

---

### Post by oldfred on 2010-11-27
Grub likes to install to sda. So even though you installed to an external did it reinstall/update to sda?

For some with external drives this works, but it save the sdb (or whatever) as sdb not UUID. If you reconfigure or have plugged into another system where it is not sdb it will reinstall to the wrong drive.

to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions

chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by goplayer on 2010-11-27
Thanks oldfred. No I do not have grub installed on sda. I wanted ubuntu installed on an external drive so that I can run it at work too (my computer at work runs windows Vista). Everything worked fine until the update and even though I edited the grub.cfg file (which I am not supposed to do) to change the root to (hd0,1) it still does not work. What puzzles me though is if enter the commands as I stated then I can boot. If those commands are in the cfg file they don't.
I do not need a dual boot. All I need is to plug the USB external drive and be able to boot ubuntu. If I want windows I simply reboot without the external drive.

---

### Post by dino99 on 2010-11-27
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

scroll down to " Selected Problems and Bugs " (page bottom)

---

### Post by oldfred on 2010-11-27
WE have seen where the external is sda, not sure why as the internal is usually sda.

To see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.

---

### Post by goplayer on 2010-11-27
When I get the grub prompt if I type ls I get the list of drives (hd0), (hd0,1), (hd1), (hd1,1). I suppose those refer to the two drives I have internal and external. Once I boot ubuntu I can examine the external drive and it is mounted as sdb (sdb1) which would mean that in grub the set root=(hd1,1) should be correct and that is what the grub.cfg file has. However, it seems that at boot time since by USB drive is bootable and I am trying to boot off of it, it is (hd0,1) and that is what I had in the .cfg file before this latest update a couple of days ago and that is what I set root as when I get the grub prompt. 
Maybe what I should do is disconnect my internal drive, boot off the external USB drive and reinstall grub-pc since the internal drive is disconnected then I am thinking that this should work. Does this make any sense? 
Thanks for the replies oldfred and dino99.

---

### Post by oldfred on 2010-11-28
If it is hd0 then grub is seeing the external as the first drive. In that case I would think grub would have reinstalled to hd0, but with grub you always have to check. 

Boot script is the best way to know what is installed where.

---

### Post by goplayer on 2010-11-28
Here is the results.txt file


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 92538944 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /grub/grub.cfg /boot/grub/grub.cfg 
                       /etc/fstab /grub/core.img /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,751,999   976,751,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   619,134,975   619,132,928  83 Linux
/dev/sdb2         619,137,022   625,141,759     6,004,738   5 Extended
/dev/sdb5         619,137,024   625,141,759     6,004,736  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        8E10662F10661F09                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        c0a427a1-9b76-41dc-9fe6-27f817938c82   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        feeae624-5f87-49f8-9944-3af4488bebae   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=c0a427a1-9b76-41dc-9fe6-27f817938c82 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c0a427a1-9b76-41dc-9fe6-27f817938c82

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-26-generic-pae
uuid        c0a427a1-9b76-41dc-9fe6-27f817938c82
kernel        /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=c0a427a1-9b76-41dc-9fe6-27f817938c82 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-26-generic-pae

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-26-generic-pae (recovery mode)
uuid        c0a427a1-9b76-41dc-9fe6-27f817938c82
kernel        /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=c0a427a1-9b76-41dc-9fe6-27f817938c82 ro  single
initrd        /boot/initrd.img-2.6.32-26-generic-pae

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic-pae
uuid        c0a427a1-9b76-41dc-9fe6-27f817938c82
kernel        /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=c0a427a1-9b76-41dc-9fe6-27f817938c82 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-25-generic-pae

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic-pae (recovery mode)
uuid        c0a427a1-9b76-41dc-9fe6-27f817938c82
kernel        /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=c0a427a1-9b76-41dc-9fe6-27f817938c82 ro  single
initrd        /boot/initrd.img-2.6.32-25-generic-pae

title        Chainload into GRUB 2
root        c0a427a1-9b76-41dc-9fe6-27f817938c82
kernel        /boot/grub/core.img

title        Ubuntu 10.04.1 LTS, memtest86+
uuid        c0a427a1-9b76-41dc-9fe6-27f817938c82
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

============================= sdb1/grub/grub.cfg: =============================

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

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8e10662f10661f09
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set c0a427a1-9b76-41dc-9fe6-27f817938c82
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
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set c0a427a1-9b76-41dc-9fe6-27f817938c82
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c0a427a1-9b76-41dc-9fe6-27f817938c82
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=c0a427a1-9b76-41dc-9fe6-27f817938c82 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c0a427a1-9b76-41dc-9fe6-27f817938c82
    echo    'Loading Linux 2.6.32-26-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=c0a427a1-9b76-41dc-9fe6-27f817938c82 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c0a427a1-9b76-41dc-9fe6-27f817938c82
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=c0a427a1-9b76-41dc-9fe6-27f817938c82 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c0a427a1-9b76-41dc-9fe6-27f817938c82
    echo    'Loading Linux 2.6.32-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=c0a427a1-9b76-41dc-9fe6-27f817938c82 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c0a427a1-9b76-41dc-9fe6-27f817938c82
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c0a427a1-9b76-41dc-9fe6-27f817938c82
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8e10662f10661f09
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c0a427a1-9b76-41dc-9fe6-27f817938c82 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=feeae624-5f87-49f8-9944-3af4488bebae none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  47.3GB: boot/grub/core.img
 253.9GB: boot/grub/grub.cfg
 253.8GB: boot/grub/menu.lst
  47.3GB: boot/grub/stage2
  47.5GB: boot/initrd.img-2.6.32-25-generic-pae
  47.5GB: boot/initrd.img-2.6.32-26-generic-pae
  47.3GB: boot/vmlinuz-2.6.32-25-generic-pae
  47.5GB: boot/vmlinuz-2.6.32-26-generic-pae
 176.2GB: grub/core.img
 176.2GB: grub/grub.cfg
  47.5GB: initrd.img
  47.5GB: initrd.img.old
  47.5GB: vmlinuz
  47.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a0 5b 00 00 00  |............[...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2010-11-28
I looks like you have grub installed to the partition which does not impact anything, but have menu.lst from old grub and two sets of grub files one at /grub and the other the normal /boot/grub.

Often it is best just to totally uninstall grub & grub2 and cleanly reinstall grub2.

If you can boot into your system manually you do not have to chroot, just run the uninstall/reinstall commands.

chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by goplayer on 2010-11-28
Thank you for all your help oldfred. I solved the problem. Here's how I did it.
I removed the executable bit from 10_linux, 30_os-prober, and 20_memtest86+ in -- I wanted a completely custom boot menu.

```
sudo -x /etc/grub.d/10_linux /etc/grub.d/20_memtest86+ /etc/grub.d/30_os-prober
```

I then opened the grub.cfg file and copied the menu entries I needed and pasted those in the 40_custom file in /etc/grub.d. In those menu entries I changed set root to ```
set root=(hd0,1)
```

Then in the terminal window I updated grub

```
sudo update-grub
```

I was then able to reboot. I had boot menu and the boot process worked fine.
___________________________________________________________________

Here's the 40_custom file


```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c0a427a1-9b76-41dc-9fe6-27f817938c82
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=c0a427a1-9b76-41dc-9fe6-27f817938c82 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c0a427a1-9b76-41dc-9fe6-27f817938c82
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=c0a427a1-9b76-41dc-9fe6-27f817938c82 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c0a427a1-9b76-41dc-9fe6-27f817938c82
    echo    'Loading Linux 2.6.32-26-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=c0a427a1-9b76-41dc-9fe6-27f817938c82 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c0a427a1-9b76-41dc-9fe6-27f817938c82
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=c0a427a1-9b76-41dc-9fe6-27f817938c82 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c0a427a1-9b76-41dc-9fe6-27f817938c82
    echo    'Loading Linux 2.6.32-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=c0a427a1-9b76-41dc-9fe6-27f817938c82 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c0a427a1-9b76-41dc-9fe6-27f817938c82
    echo    'Loading Linux 2.6.32-26-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=c0a427a1-9b76-41dc-9fe6-27f817938c82 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c0a427a1-9b76-41dc-9fe6-27f817938c82
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=c0a427a1-9b76-41dc-9fe6-27f817938c82 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c0a427a1-9b76-41dc-9fe6-27f817938c82
    echo    'Loading Linux 2.6.32-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=c0a427a1-9b76-41dc-9fe6-27f817938c82 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
```


and here's the grub.cfg file 

```
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
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set c0a427a1-9b76-41dc-9fe6-27f817938c82
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
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set c0a427a1-9b76-41dc-9fe6-27f817938c82
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
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

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c0a427a1-9b76-41dc-9fe6-27f817938c82
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=c0a427a1-9b76-41dc-9fe6-27f817938c82 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c0a427a1-9b76-41dc-9fe6-27f817938c82
    echo    'Loading Linux 2.6.32-26-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=c0a427a1-9b76-41dc-9fe6-27f817938c82 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c0a427a1-9b76-41dc-9fe6-27f817938c82
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=c0a427a1-9b76-41dc-9fe6-27f817938c82 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c0a427a1-9b76-41dc-9fe6-27f817938c82
    echo    'Loading Linux 2.6.32-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=c0a427a1-9b76-41dc-9fe6-27f817938c82 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
### END /etc/grub.d/40_custom ###
```

---

### Post by oldfred on 2010-11-28
That works.:)

It is a bit of a brute force way of doing it. I have a semi-custom as I add entries to 40_custom and edit those. And I turn off the osprober.

I have found that grub sees the boot drive as hd0 in all cases. I have experimented with chainloading MBRs and found whichever drive I boot it is hd0 and then the drives are in order. So when I normally boot sdc and chainboot to sda only works if I call sda hd1. It seems the search by UUID it what really controls finding the correct drive in most cases.

---

