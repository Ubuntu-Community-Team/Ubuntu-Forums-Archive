---
title: "GRUB problem"
date: 2009-12-09
forum: General Help
---

### Post by tombaugh on 2009-12-09
Hi,

I just added a drive to my PC and installed Ubuntu on it. When I boot this drive GRUB gives me the choice between the new Ubuntu system and Windows XP, which is on another drive. However, there is yet another drive on the system which already had Ubuntu on it, and when I try to boot that one (as usual) I get GRUB error 22. I would like to get that working again since it's my main system.

This is the situation:

/dev/sda ext3 backup drive
/dev/sdb ext4 new Ubuntu system
/dev/sdc ext3 existing Ubuntu system
/dev/sdd ntfs Windows XP

This is menu.lst on my old Ubuntu system:

```
title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        445ce9f8-0fc7-40cc-9dd4-192896b056c3
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=445ce9f8-0fc7-40cc-9dd4-192896b056c3 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title          Windows XP
rootnoverify   (hd1,0)
map            (hd0) (hd1)
map            (hd1) (hd0)
chainloader    +1

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        445ce9f8-0fc7-40cc-9dd4-192896b056c3
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=445ce9f8-0fc7-40cc-9dd4-192896b056c3 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-15-generic
uuid        445ce9f8-0fc7-40cc-9dd4-192896b056c3
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=445ce9f8-0fc7-40cc-9dd4-192896b056c3 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
uuid        445ce9f8-0fc7-40cc-9dd4-192896b056c3
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=445ce9f8-0fc7-40cc-9dd4-192896b056c3 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.10, memtest86+
uuid        445ce9f8-0fc7-40cc-9dd4-192896b056c3
kernel        /boot/memtest86+.bin
quiet

```

On the new Ubuntu system I can't find menu.lst.

---

### Post by Wiifreak on 2009-12-09
I have maybe a similar problem.
I can't find mine menu.lst either.

I got errors about stage 1 being corrupt and files not found.

Is there a bug in Grub?

I had to reinstall Windows, so have no grub, but can't install it because of these errors...

Anyone got the solution?

---

### Post by tombaugh on 2009-12-09
I restarted and GRUB now gives me the option of booting from /dev/sdc as well. However, when I do that I first see the Ubuntu logo for quite some time and then there's only a blinking cursor.

edit: I now booted in recovery mode and get this error:

```
request_module: runaway loop modprobe binfmt-464c
```

---

### Post by tombaugh on 2009-12-09
Here's a bit more information.

Selecting Windows XP in GRUB gives

```
error: invalid signature
```

This is the fdisk output:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8d3f8d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00074c44

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       59577   478552221   83  Linux
/dev/sdb2           59578       60801     9831780    5  Extended
/dev/sdb5           59578       60801     9831748+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ab24e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       59345   476688681   83  Linux
/dev/sdc2           59346       60801    11695320    5  Extended
/dev/sdc5           59346       60801    11695288+  82  Linux swap / Solaris

Disk /dev/sdd: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9d9bdfac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       14945   120045681    7  HPFS/NTFS

```

---

### Post by tombaugh on 2009-12-09
After some reading I think I may have to reinstall GRUB to the MBR of the drive holding my original Ubuntu system. However, I cannot follow the procedure in [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) because I do not have grub installed (I have grub-pc according to synaptic but I don't know how to run that). I could install grub and remove grub-pc but I don't want to risk being shut out of my system completely. Can anyone please offer a bit of assistance here?

edit: update-grub gives me

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 9.10 (9.10) on /dev/sdc1
grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

Found Microsoft Windows XP Professional on /dev/sdd1
grub-probe: error: Cannot find a GRUB drive for /dev/sdd1.  Check your device.map.

done
```

device.map looks like this:

```

(hd0)    /dev/sda
(hd1)    /dev/sdb
```

---

### Post by bumanie on 2009-12-09
Removed instructions as it is unclear whether the poster is using grub-legacy or grub 2 - he/she posted a /boot/grub/menu.lst, but sudo update-grub showed a grub.cfg being generated.

---

### Post by bumanie on 2009-12-09
You posted a grub-legacy list - not grub2 list - if you are running grub2  what I have just posted won't work. May be you have upgraded to grub2 and not got rid of the old list as yet and you have posted the wrong list. Think I will remove what I put before things go really wrong.

---

### Post by tombaugh on 2009-12-09
The menu.lst I posted is from my original Ubuntu system which does not boot any more. This system was upgraded to 9.10 so it uses grub. The update-grub output is from the new system (clean install, so grub2). Now I would like to get grub on the old system, or grub2 on the new system to work so that I can boot into the old system and the windows system again.

Thanks!

---

### Post by bumanie on 2009-12-09
Yes, as soon as you posted the message re update-grub and grub.cfg popped up I realised you were using grub 2 on 9.10. I had read that if someone did an upgrade via upgrade-manager that grub-legacy would remain the bootloader - so when you posted /boot/grub/menu.lst I assumed you had done that. Unfortunately, I am not very good with grub 2 as yet, so I am not sure I can help. Have a [look here]("http://members.iinet.net/~herman546/p20.html") and see if anything helps - if not you will have to wait until someone who knows more about grub2 than I do comes along. Sorry, but I have been studying until last week and have not had time to get up to speed on grub 2 as yet - hope to during the study break.
Good luck and I am glad that we caught things before a big error was made. Herman's site should help, and there are links to other grub 2 information as well. Hope it helps.

---

### Post by joes7 on 2009-12-09
> **Wiifreak said:**
> I have maybe a similar problem.
I can't find mine menu.lst either.

I got errors about stage 1 being corrupt and files not found.

Is there a bug in Grub?

I had to reinstall Windows, so have no grub, but can't install it because of these errors...

Anyone got the solution?

No, there isn't a bug. This usually happens because one doesn't have enough permissions on Xubuntu / Ubuntu. Log in on safe mode (recovery mode) and look for the file. It should be there. If it isn't, try logging in as "root".

Regards

---

### Post by ranch hand on 2009-12-09
Just to make things easier for all of us, if you can boot into 9.10, run;
```

grub-install -v

```

No matter what you can boot into we need the results from;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

If you can't boot to Ubuntu do this from your LiveCD and post the results.

---

### Post by tombaugh on 2009-12-09
I tried reinstalling GRUB

```
sudo grub-install --recheck /dev/sdc
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.
(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
(hd3)    /dev/sdd

sudo grub-install --recheck /dev/sdd
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.
(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
(hd3)    /dev/sdd
```GRUB version:

```
grub-install -v
grub-install (GNU GRUB 1.97~beta4)
```boot info script:

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=4cc4eae9-ba27-4076-b416-d3a5cad3dd20)/boot/grub.
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub.
 => Grub 1.97 is installed in the MBR of /dev/sdc and looks for 
    (UUID=4cc4eae9-ba27-4076-b416-d3a5cad3dd20)/boot/grub.
 => Grub 1.97 is installed in the MBR of /dev/sdd and looks for 
    (UUID=4cc4eae9-ba27-4076-b416-d3a5cad3dd20)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf8d3f8d3

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   976,768,064   976,768,002  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00074c44

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   957,104,504   957,104,442  83 Linux
/dev/sdb2         957,104,505   976,768,064    19,663,560   5 Extended
/dev/sdb5         957,104,568   976,768,064    19,663,497  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ab24e

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   953,377,424   953,377,362  83 Linux
/dev/sdc2         953,377,425   976,768,064    23,390,640   5 Extended
/dev/sdc5         953,377,488   976,768,064    23,390,577  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9d9bdfac

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   240,091,424   240,091,362   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="backup" UUID="0fd7125e-9073-403b-80ea-ee38ed421216" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="4cc4eae9-ba27-4076-b416-d3a5cad3dd20" TYPE="ext4" 
/dev/sdb5: UUID="6c7b0df1-6d54-47e1-9947-6e32c2bc1dfd" TYPE="swap" 
/dev/sdc1: UUID="445ce9f8-0fc7-40cc-9dd4-192896b056c3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: UUID="27166425-6b96-4629-95f6-4b1c2c7f95a5" TYPE="swap" 
/dev/sdd1: UUID="2C88FC3188FBF764" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/pieter/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pieter)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set 4cc4eae9-ba27-4076-b416-d3a5cad3dd20
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 4cc4eae9-ba27-4076-b416-d3a5cad3dd20
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=4cc4eae9-ba27-4076-b416-d3a5cad3dd20 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 4cc4eae9-ba27-4076-b416-d3a5cad3dd20
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=4cc4eae9-ba27-4076-b416-d3a5cad3dd20 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 4cc4eae9-ba27-4076-b416-d3a5cad3dd20
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=4cc4eae9-ba27-4076-b416-d3a5cad3dd20 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 4cc4eae9-ba27-4076-b416-d3a5cad3dd20
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=4cc4eae9-ba27-4076-b416-d3a5cad3dd20 ro single 
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
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (on /dev/sdc1)" {
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=445ce9f8-0fc7-40cc-9dd4-192896b056c3 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode) (on /dev/sdc1)" {
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=445ce9f8-0fc7-40cc-9dd4-192896b056c3 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-15-generic (on /dev/sdc1)" {
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=445ce9f8-0fc7-40cc-9dd4-192896b056c3 ro quiet splash
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode) (on /dev/sdc1)" {
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=445ce9f8-0fc7-40cc-9dd4-192896b056c3 ro single
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sdc1)" {
    linux /boot/memtest86+.bin 
}
menuentry "Microsoft Windows XP Professional (on /dev/sdd1)" {
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=4cc4eae9-ba27-4076-b416-d3a5cad3dd20 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6c7b0df1-6d54-47e1-9947-6e32c2bc1dfd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

=========================== sdc1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

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
hiddenmenu

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
# kopt=root=UUID=445ce9f8-0fc7-40cc-9dd4-192896b056c3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=445ce9f8-0fc7-40cc-9dd4-192896b056c3

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

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        445ce9f8-0fc7-40cc-9dd4-192896b056c3
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=445ce9f8-0fc7-40cc-9dd4-192896b056c3 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet


title          Windows XP
rootnoverify   (hd1,0)
map            (hd0) (hd1)
map            (hd1) (hd0)
chainloader    +1

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        445ce9f8-0fc7-40cc-9dd4-192896b056c3
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=445ce9f8-0fc7-40cc-9dd4-192896b056c3 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-15-generic
uuid        445ce9f8-0fc7-40cc-9dd4-192896b056c3
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=445ce9f8-0fc7-40cc-9dd4-192896b056c3 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
uuid        445ce9f8-0fc7-40cc-9dd4-192896b056c3
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=445ce9f8-0fc7-40cc-9dd4-192896b056c3 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.10, memtest86+
uuid        445ce9f8-0fc7-40cc-9dd4-192896b056c3
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=445ce9f8-0fc7-40cc-9dd4-192896b056c3 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=27166425-6b96-4629-95f6-4b1c2c7f95a5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.28-15-generic
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-15-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.28-15-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-15-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

================================ sdd1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer 
```

---

### Post by Leppie on 2009-12-09
Why did you install grub on every disk?
Have you tried to boot after reinstalling?

---

### Post by tombaugh on 2009-12-09
> **Leppie said:**
> Why did you install grub on every disk?
Have you tried to boot after reinstalling?

Because [http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-install]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#grub-install") says 

> If you're not sure which hard disk's MBR you want to install GRUB2 to, it's possibly best to install GRUB to all of your disks, just to make sure.

I tried booting but it still doesn't work. Trying to boot into ubuntu on sdc gives

```
request_module: runaway loop modprobe binfmt-464c
```while trying to boot into windows on sdd gives

```
error: invalid signature
```

---

### Post by tombaugh on 2009-12-09
Hooray, another grub-update allowed me to boot into the old ubuntu (although a bit slow). Now let's see if windows works...

---

### Post by Leppie on 2009-12-09
do you have two karmic installations with one using grub2 and one grub-legacy?

---

### Post by tombaugh on 2009-12-09
> **Leppie said:**
> do you have two karmic installations with one using grub2 and one grub-legacy?

Yes, because the first one was an upgrade and the second one a clean install. But I'll switch to grub2...

Thanks everyone for the assistance!

---

### Post by Leppie on 2009-12-09
> **tombaugh said:**
> Yes, because the first one was an upgrade and the second one a clean install. But I'll switch to grub2...

Thanks everyone for the assistance!

is xp booting properly as well now?
if not, you may want to try to add "insmod ntfs" to the xp section

---

### Post by tombaugh on 2009-12-09
> **Leppie said:**
> is xp booting properly as well now?
if not, you may want to try to add "insmod ntfs" to the xp section

Yes, everything is working fine now! I'll have to look into the documentation to make a friendlier grub menu though...

---

### Post by ranch hand on 2009-12-09
This is great.

In the future if you need to do "grub-install" do not do it with the commands you were using;
> 
grub> find xxxxxxx
grub> root (hdx,y)
grub> setup (hdx)
grub> quit

That is for grub-legacy.

For grub2 use these instructions if you have to go to the live CD;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

One of the neat things about grub2 is if you can boot to any grub2 using OS you can install grub on your MBR using the OS you can boot to as boot/root by simply running;
```

sudo grub-install /dev/sda

```
That is assuming you want it on sda.  You do not need a CD at all if you can boot to any of them.  Just run that and;
```

sudo update-grub

```
and it will be just as good as what ever OS you were booting from before.

One thing to keep in mind.  Grub1.97 is in the testing repo (you are using grub1.97beta4).  When the update hits "update-grub" will not work any more.  It was never supposed to.

"grub-mkconfig" will be doing that job.  It is better.  Instead of the minimal list you get for feed back as to what is happening, you get the newly generated /boot/grub/grub.cfg file displayed in terminal so you can tell if it is right.

I want that on my 9.10 installs so bad I can taste it.  I love it on 10.04-testing (they call it Lucid Lynx, I prefer Lounge Lizard).

---

