---
title: "Can't Boot Ubuntu, No Ubuntu Boot Menu After Software Update Reboot"
date: 2010-12-23
forum: General Help
---

### Post by rebugprog on 2010-12-23
I can't seem to get into Ubuntu 10.04 (Lucid Lynx) after a software  update.  I started the Update Manager and left it to do its work.  I  noticed in the update list there were a couple of "reinstalls" of what  appeared to be OS libraries at the top (I was surprised, since I had  only updated a few days ago when I installed Ubuntu).  Later, it told me  I needed to reboot, which I did immediately (.

Now, when I start  up the computer, the hardware manufacturer "hp" logo shows up with the  typical options, I go to a boot menu with the choices Windows XP and  Ubuntu.  Then, if I select Ubuntu, something winds in my machine, and I  get taken back to the "hp" screen.  Windows XP starts normally.

Right  now, I am running Ubuntu from the live cd (I was expecting a recovery  mode option to be there, but I couldn't find one).  I have attempted to  diagnose it through several means.  What is interesting is that I can  find the hard drive, mount it, and see the files from Windows, but I  can't seem to find the Linux partition, except through the install  option on the live cd (I ran it up to the point where it asked me for  the partitioning of the drive).

Does anybody have any ideas on how to recover the Linux boot?  I'm completely new to Linux and don't quite understand all the inner workings yet.

(Sorry for when my English is not understandable or when it's written incorrectly, I'm not a writer)

---

### Post by karthick87 on 2010-12-23
Welcome to ubuntuforums :)

Is that a wubi install??Post the results of [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) with code(#) tags..

---

### Post by hadrons123 on 2010-12-23
did you do a kernel update?

If so it might have messed up the boot config.

Reinstall Ubuntu Grub Bootloader After Windows Wipes it Out
If you run a dual-boot system with Linux and Windows, this has happened to you. You had to do your monthly reinstall of Windows, and now you don’t see the linux bootloader anymore, so you can’t boot into Ubuntu or whatever flavor of linux you prefer.

Here’s the quick and easy way to re-enable Grub.

1) Boot off the LiveCD

2) Open a Terminal and type in the following commands, noting that the first command will put you into the grub “prompt”, and the next 3 commands will be executed there. Also note that hd0,0 implies the first hard drive and the first partition on that drive, which is where you probably installed grub to during installation. If not, then adjust accordingly.

sudo grub

> root (hd0,0)

> setup (hd0)

> exit

Reboot (removing the livecd), and your boot menu should be back.

 

Only read below if Windows is now missing from the boot menu

If you installed Ubuntu before you installed Windows, then Ubuntu will not have anything in the grub configuration for Windows. This is where you’ll have to do a bit of manual editing to the grub boot menu file.

If you open the file /boot/grub/menu.lst with the following command:

sudo gedit /boot/grub/menu.lst

You’ll see a sample section for Windows, which you’ll want to uncomment and add to the boot menu list in whatever position you want it in. (uncomment by removing the #’s)

# title   Windows 95/98/NT/2000
# root   (hd0,0)
# makeactive
# chainloader   +1

Note that you should also verify that hd0,0 is the correct location for Windows. If you had installed Windows on the 4th partition on the drive, then you should change it to (hd0,3).

---

### Post by rebugprog on 2010-12-23
> **karthick87 said:**
> Welcome to ubuntuforums :)

Is that a wubi install??Post the results of [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) with code(#) tags..

This is a mostly fresh wubi install.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,156,224    78,156,162   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       64fc33b0-c368-43c9-86d8-d7a1343d2053   ext4                                     
/dev/sda1        74943E2A943DEEEC                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

======================== sda1/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 74943e2a943deeec
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 74943e2a943deeec
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-27-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 74943e2a943deeec
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-27-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, Linux 2.6.32-27-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 74943e2a943deeec
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-27-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 74943e2a943deeec
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 74943e2a943deeec
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 74943e2a943deeec
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 74943e2a943deeec
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 74943e2a943deeec
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda1/Wubi/etc/fstab: =============================

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

================= sda1/Wubi: Location of files loaded by Grub: =================


   2.8GB: boot/grub/grub.cfg
   5.8GB: boot/initrd.img-2.6.32-24-generic
   5.8GB: boot/initrd.img-2.6.32-26-generic
   7.9GB: boot/initrd.img-2.6.32-27-generic
   5.8GB: boot/vmlinuz-2.6.32-24-generic
   5.8GB: boot/vmlinuz-2.6.32-26-generic
   8.1GB: boot/vmlinuz-2.6.32-27-generic
   7.9GB: initrd.img
   5.8GB: initrd.img.old
   8.1GB: vmlinuz
   5.8GB: vmlinuz.old
```> **hadrons123 said:**
> Here’s the quick and easy way to re-enable Grub.

1) Boot off the LiveCD

2) Open a Terminal and type in the following commands, noting that the first command will put you into the grub “prompt”, and the next 3 commands will be executed there. Also note that hd0,0 implies the first hard drive and the first partition on that drive, which is where you probably installed grub to during installation. If not, then adjust accordingly.

sudo grub

> root (hd0,0)

> setup (hd0)

> exit


When i try it i get stopped at "setup (hd0)"
The error shows:
"Error 17: Cannot mount selected partition"

To the question I didn't quote, while I don't remember what the exact installation was, I assume it was a kernel update, since the hardware doesn't like the OS instructions.

This is an old machine that ran Windows XP before and was dual-booting Windows XP and Ubuntu.  While Windows might have messed up Ubuntu, it hadn't been updated in a long time (and requested quite a few), however I doubt that Windows would have touched Ubuntu even in the updates (then again, there isn't that much documentation, so who knows).

---

