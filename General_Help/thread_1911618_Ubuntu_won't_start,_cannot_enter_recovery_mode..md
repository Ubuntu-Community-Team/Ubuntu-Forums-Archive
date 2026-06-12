---
title: "Ubuntu won't start, cannot enter recovery mode."
date: 2012-01-19
forum: General Help
---

### Post by Yana O on 2012-01-19
First off, i'm a complete beginner. 

I'm running Oneiric Ocelot. I installed it from Windows, so it's running alongside Windows. The problems started, after i pulled the plug in a hurry. After that i haven't been able to access Ubuntu at all. The screen with Ubuntu logo in it appears, then just a black screen with ''Ok''. I've tried to access recovery mode with shift and esc, so far no success. I've also tried to rescue a couple of files using Windows and some tools, but no success there either. Ubuntu is protected with a password. I would just install Ubuntu again, but there are some txt files i need.

Any help appreciated..

---

### Post by Rubi1200 on 2012-01-20
Hi and welcome to the forums :-)

If you installed with Wubi (which is what your post suggests) then it is very likely that there is file corruption due to the the hard shutdown. Wubi is very sensitive to hard shutdowns.

If possible, post the results of the boot info script so we can make sure of what happened. There is a link at the bottom of my post with instructions.

You can also try using [ext2read]("http://ext2read.blogspot.com/") to recover any important data from the Ubuntu root.disk. 

However, if the root.disk was damaged then this will probably not work.

Then read this:
[COLOR=Black]Another recurring problem, missing the root.disk on a Wubi install, is dealt with here by forum member bcbc:
[http://ubuntu-with-wubi.blogspot.com...-rootdisk.html]("http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html")[/COLOR]

---

### Post by guzamakat on 2012-01-22
Hi there,

I'm having this problem as well. Ubuntu 11.04 crashed when I started Skype (either because a problem with Skype or with my new webcam) and after that I got this startup message saying root.disk could not be found. Is there any way to repair this error? I tried Boot Repair (from livecd) but it just kept saying "scanning systems" ad infinitum, and I tried reinstallnig grub manually but that didn't do anything.

On a side note, is there an Ubuntu flavour that actually has some sort of useable recovery console when startup fails? GRUB is annoying the hell out of me, with its blinking cursor on a black screen, about as user friendly as a 1992 IBM terminal.

---

### Post by Yana O on 2012-01-30
Thanks for the advice. The problem still exists. The root.disk is not missing and the disc has been checked.
I can see the windows files on ubuntu live cd, or puppy linux, but i can't find the files from old ubuntu. Not quite sure where to look for them though..

Here is the boot info..
```


#                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   117,207,039   117,000,192   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        F84467F24467B1D4                       ntfs       System Reserved
/dev/sda2        9A0E6A8A0E6A5F6F                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== sda2/Wubi/boot/grub/grub.cfg: =========================

--------------------------------------------------------------------------------
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
insmod ntfs
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 9A0E6A8A0E6A5F6F
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ntfs
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root 9A0E6A8A0E6A5F6F
  loopback loop0 /ubuntu/disks/root.disk
  set root=(loop0)
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
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
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 9A0E6A8A0E6A5F6F
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=9A0E6A8A0E6A5F6F loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 9A0E6A8A0E6A5F6F
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    echo    'Loading Linux 3.0.0-13-generic ...'
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=9A0E6A8A0E6A5F6F loop=/ubuntu/disks/root.disk ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-13-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 9A0E6A8A0E6A5F6F
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9A0E6A8A0E6A5F6F loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 9A0E6A8A0E6A5F6F
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9A0E6A8A0E6A5F6F loop=/ubuntu/disks/root.disk ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
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
--------------------------------------------------------------------------------

============================= sda2/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
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
--------------------------------------------------------------------------------

================= sda2/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-8-generic              199
               =                boot/initrd.img-3.0.0-13-generic               7
               =                boot/vmlinuz-2.6.38-8-generic                  1
               =                boot/vmlinuz-3.0.0-13-generic                  2
               =                initrd.img.old                                199
               =                vmlinuz                                        2
               =                vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by Rubi1200 on 2012-01-30
Yes, it is an odd situation. Let me ask some other members to take a look and offer their perspectives on this.

Thanks.

---

### Post by bcbc on 2012-01-30
In order to boot recovery mode you need to position to the *Recovery mode* entry and press 'E' to edit it. Then delete the line:
```
set gfxpayload=$linux_gfx_mode
```
Then Ctrl+X to boot.

This is a bug (affecting only Wubi) that has been fixed in the development release, but I don't know whether it's made it's way to Oneiric yet. Note that the recovery mode you get to is a "Read only recovery" and so you would have to "Remount read/write" (option 3) in order to change passwords or make changes to the disk.

In general, after a hard shutdown on wubi that results in problems:
1. run "chkdsk /f" or (chkdsk /r - personally I would only do /r if you think you have a failing disk).
2. if it's still wonky, fsck the root.disk from a live CD
3. restore from backup (you would have to have a backup of the root.disk or your reinstall with your backed up data).

---

### Post by Yana O on 2012-01-30
Hey.

I was able to simply mount the root.disc (which was still there) and collect what i needed. 
Thanks a lot for everyone who replied! Wubi is history from now on...

---

### Post by Rubi1200 on 2012-01-30
Excellent! Glad you got things sorted out :-)

Thanks to bcbc for the great advice too.

Please mark this thread Solved using the Thread Tools near the top of the page.

---

