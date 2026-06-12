---
title: "problems after resizing with gparted"
date: 2010-07-15
forum: General Help
---

### Post by luvgirl12345 on 2010-07-15
I resized (grow) sda5 with gparted and now I cant boot anymore. GRUB hangs when its loading.

thanks for any help I might get :p luvgirl12345

---

### Post by Braik on 2010-07-15
You will not have an answer without a complete question, don't forget that we are not in your mind
 
> **luvgirl12345 said:**
> I resized (grow) sda5 with gparted and now I cant boot anymore. 
 
Ok, you resized sda5 partition, but what was inside? what was inside other partitions (there were sda1 to sda4 at least, maybe sda6 to....)
If you cannot answer this the only solution for me is to boot with a liveCD, open a terminal and type
```
fdisk -l
```
with an lower case L, and not a one.
 
Copy and paste the result of the command
 
> **luvgirl12345 said:**
> 
GRUB hangs when its loading.
 
 
What are the error messages of GRUB?

---

### Post by luvgirl12345 on 2010-07-15
Im sorry:

```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe2a1bb7d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3               1       77826   625131519+   5  Extended
/dev/sda5               1       76697   616068621   83  Linux
/dev/sda6           76698       77826     9059328   82  Linux swap / Solaris
```

No error message in GRUB it just hangs at GRUB Loading.

---

### Post by Braik on 2010-07-15
I am a little confused, there are some point that looks weird for me, first you only have partitions sda3, 5 and 6 (no 1,2 and 4) but I don't think this is an issue, second your partition sda5 don't have the * symbol in the boot column, again I don't know if this is an issue because GRUB normally don't need this information.
 
I think that when you resized your partition (have you erased a Windows or other system partition? sda1, 2 and 4 dissapearing) your GRUB was a little bit confused so It tries to load but don't find the correct parameters.
 
What I propose to you is to re-install grub with this link:
[https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2](https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2)
 
You just must be sure that you were using GRUB2 (Ubuntu 9.10 and above) and think that your system partition (point 4) is the /dev/sda5.
 
If there is anybody that can confirm my ideas it will be great

---

### Post by drs305 on 2010-07-15
I assume this is after you resized and then restored with fsarchiver (per the posts from yesterday)?

Please run the boot info script from the LiveCD and post the contents of RESULTS.txt here between "code" tags. You can generate the code tags by pressing the # icon.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by luvgirl12345 on 2010-07-15
> **drs305 said:**
> I assume this is after you resized and then restored with fsarchiver (per the posts from yesterday)?

Please run the boot info script from the LiveCD and post the contents of RESULTS.txt here between "code" tags. You can generate the code tags by pressing the # icon.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

A few things I forgot to say before: 
I use BURG (Its a layer for GRUB)
I just noticed old menuentrys were still in the file: windows and a quick try at mac (Just thought this Might be why GRUB is acting up... but i doubt it because a menuentry only submits the command when you click it) I dont know how to remove this stuff... I was only following tuts :)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/burg.

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub 2's core.img
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda3                   1 1,250,263,039 1,250,263,039   5 Extended
/dev/sda5                  63 1,232,137,304 1,232,137,242  83 Linux
/dev/sda6       1,232,144,384 1,250,263,039    18,118,656  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda3: PTTYPE="dos" 
/dev/sda5        f48177fc-0532-4a84-a81a-e34df78710a1   ext4                                     
/dev/sda6        66665b1f-ad67-4b3f-a53d-ff4f82052ac4   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f48177fc-0532-4a84-a81a-e34df78710a1
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f48177fc-0532-4a84-a81a-e34df78710a1
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f48177fc-0532-4a84-a81a-e34df78710a1
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=f48177fc-0532-4a84-a81a-e34df78710a1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f48177fc-0532-4a84-a81a-e34df78710a1
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=f48177fc-0532-4a84-a81a-e34df78710a1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f48177fc-0532-4a84-a81a-e34df78710a1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f48177fc-0532-4a84-a81a-e34df78710a1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0ecac084cac06a13
    chainloader +1
}
menuentry "Mac OS X (32-bit) (on /dev/sda2)" {
    insmod hfsplus
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 455237d2a3607103
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 455237d2a3607103 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sda2)" {
    insmod hfsplus
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 455237d2a3607103
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 455237d2a3607103 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "MacOS X Snow Leopard" {
        insmod hfsplus
        set root=(hd0,1) #change X to the Mac SL partition
        multiboot /boot
}
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f48177fc-0532-4a84-a81a-e34df78710a1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=66665b1f-ad67-4b3f-a53d-ff4f82052ac4 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 184.8GB: boot/grub/core.img
 184.8GB: boot/grub/grub.cfg
 184.8GB: boot/initrd.img-2.6.32-23-generic
 184.8GB: boot/initrd.img-2.6.32-24-generic
 184.8GB: boot/vmlinuz-2.6.32-23-generic
 184.9GB: boot/vmlinuz-2.6.32-24-generic
 184.8GB: initrd.img
 184.8GB: initrd.img.old
 184.9GB: vmlinuz
 184.8GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```one more thing: I didn't wipe the partition I only resized it... I'm not sure if I used fsarchiver right but I didn't see a difference before and after (maybe I didn't even need to use fsarchiver??)


edit: Its 12:35... I'm going to bed and will check back in the morning.

---

### Post by drs305 on 2010-07-15
I haven't used burg, so I don't know how it is represented in RESULTS.txt. The only thing that stands out (aside from not having any primary partitions) is that the initial line says that burg is installed but the final entries don't show a /boot/burg listing.  I don't know if the boot info script would show the /boot/burg folder at the bottom or not.

Without knowing how burg's file system works, the only thing I would recommend would be to reinstall Grub2. You would have to get someone familiar with burg to help you reinstall BURG unless you already know how.

Since you can't boot the OS, to reinstall Grub 2: boot to the LiveCD, mount /dev/sda5 and then (re)install Grub2.

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Note that you mount a specific partition in the first command (sda**5**), but the *device* only in the second **sda**.
These commands will install the Grub2 files to /dev/sda5 and will write some Grub information to the MBR of sda.

After reinstalling:
```
sudo umount /dev/sda5
```
and reboot.

---

### Post by luvgirl12345 on 2010-07-16
I did that and now get: 
```
error : no such partition grub rescue>
```

edit: if I try sudo grub in the terminal it spits out: sudo: grub: command not found. That means all those tuts about restoring grub don't work for me... Im beginning to wonder if I will ever get my computer to work again...

---

### Post by luvgirl12345 on 2010-07-16
```
Warning: invalid flag 0x0820 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe2a1bb7d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3               1       77826   625131519+   5  Extended
```**** what happened here?? sda5 is gone... WTF???

edit: I have no idea why but my whole disk seems to have gotten wiped... I am going to format it to ext4 and restore fsarchiver and report back... weird!!

edit2: restoring lucid.fsa to sda1 (4%) will report back when done...
Edit3: the power just went puff got to start over again...

---

### Post by luvgirl12345 on 2010-07-16
I restored fsarchive but GRUB doesnt even load anymore it just hangs at a black screen with a blinking cursor!?!?!?! HELP!!!

---

### Post by drs305 on 2010-07-16
> **luvgirl12345 said:**
> I restored fsarchive but GRUB doesnt even load anymore it just hangs at a black screen with a blinking cursor!?!?!?! HELP!!!

Have you tried Post 7's reinstall instructions. If you now have an sda1 change the instructions to reflect that. 

Since you have changed things around a bit, run the boot info script again if reinstalling G2 doesn't work.

---

### Post by luvgirl12345 on 2010-07-16
```
                    Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63 1,250,258,624 1,250,258,562  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        f48177fc-0532-4a84-a81a-e34df78710a1   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f48177fc-0532-4a84-a81a-e34df78710a1
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set f48177fc-0532-4a84-a81a-e34df78710a1
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f48177fc-0532-4a84-a81a-e34df78710a1
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=f48177fc-0532-4a84-a81a-e34df78710a1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f48177fc-0532-4a84-a81a-e34df78710a1
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=f48177fc-0532-4a84-a81a-e34df78710a1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f48177fc-0532-4a84-a81a-e34df78710a1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f48177fc-0532-4a84-a81a-e34df78710a1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0ecac084cac06a13
    chainloader +1
}
menuentry "Mac OS X (32-bit) (on /dev/sda2)" {
    insmod hfsplus
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 455237d2a3607103
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 455237d2a3607103 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sda2)" {
    insmod hfsplus
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 455237d2a3607103
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 455237d2a3607103 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "MacOS X Snow Leopard" {
        insmod hfsplus
        set root=(hd0,1) #change X to the Mac SL partition
        multiboot /boot
}
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f48177fc-0532-4a84-a81a-e34df78710a1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=66665b1f-ad67-4b3f-a53d-ff4f82052ac4 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 526.2GB: boot/grub/core.img
 526.2GB: boot/grub/grub.cfg
 526.3GB: boot/initrd.img-2.6.32-23-generic
 526.3GB: boot/initrd.img-2.6.32-24-generic
 526.2GB: boot/vmlinuz-2.6.32-23-generic
 526.3GB: boot/vmlinuz-2.6.32-24-generic
 526.3GB: initrd.img
 526.3GB: initrd.img.old
 526.3GB: vmlinuz
 526.2GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde  
```not sure if this is bad but theres no swap...

edit: I did the stuff on post 7 before running boot info script

---

### Post by drs305 on 2010-07-16
Not having a swap is not a problem that needs addressing at the moment. 

I don't see a problem in the RESULTS.txt at first check. Try rebooting while holding down the SHIFT key. Grub2 may be working and it may be a problem *after* grub passes control to the kernel.

If holding down the SHIFT key reveals the menu, highlight the kernel you wish and try booting. If it fails, repeat and select another kernel and try again. (For instance, 24 first, then 23 if 24 doesn't work).

If neither work, from the LiveCD, try mounting sda1 and see if you can view your files.
```

sudo mkdir /mnt/temp
sudo mount /dev/sda1 /mnt/temp
gksu nautilus /boot &

```

---

### Post by luvgirl12345 on 2010-07-16
I will try that. 

edit: I can view files if i mount the drive normaly through nautilus...

SOLVED!!! just need to setup swap... thanks drs305

---

