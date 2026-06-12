---
title: "Grub error 15"
date: 2010-04-08
forum: General Help
---

### Post by Suse on 2010-04-08
I've checked the forums for help on the problem I'm experiencing. Some of the answers may address it, but unfortunately I'm not at the stage where - though I've tried - I can't get my head around the answers. Sorry - still most definitely a Linux noob.

My set up is internal hard drive Windows 7, external Ubuntu Karmic. The reason I have it this way, despite Linux being my main OS, is because my internal hard drive is 6 years old and half the capacity of my external new one.

Have tried quite a few set ups with various Linux platforms, but have finally settled on above. As yet, I don't know Linux or Ubuntu all that well. Getting somewhere, but it's a steep learning curve.

Because of constant errors reinstalling WinXP - umpteen installations and it keeps crashing - the problems are with security updates and SP3 - I finally bit the bullet and intalled Win 7. I only need Windows for a few essential programs or I'd happily never look at it again, so it filled me with horror doing this, but I couldn't take the crashes any more. 

So, today, Win 7 installs just nicely. However, I can no longer boot my external Ubuntu hard drive. The error is, 'Grub loading stage 1.5... Grub loading please wait... Error 15'. 

Please can someone help and explain it in the simplest possible way? I load up the live cd, but when I try to follow instructions given to other people with Error 15 (editing files, accessing root) I don't have permissions.

Really hoping I don't have to reinstall Ubuntu as I finally have it set up just perfect.

---

### Post by prodigy_ on 2010-04-08
I think, you should start with running [this script](http://bootinfoscript.sourceforge.net/). From a Live CD, I mean. Post the output here.

---

### Post by Suse on 2010-04-08
Thanks, Prodigy. You're very brave.

Here's my results:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /ntldr /NTDETECT.COM

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd4a0fe34

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   586,083,329   586,083,267   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcbcdf9f3

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   964,687,184   964,687,122  83 Linux
/dev/sdb2         964,687,185   976,768,064    12,080,880   5 Extended
/dev/sdb5         964,687,248   976,768,064    12,080,817  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F8D82EC8D82E84CA                       ntfs                                     
/dev/sdb1        e4b45b96-33a0-4c90-baab-eb1953459c63   ext4                                     
/dev/sdb5        1d09a48f-ace3-4db5-9b0b-3641ae4db0a0   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/e4b45b96-33a0-4c90-baab-eb1953459c63 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sda1        /media/F8D82EC8D82E84CA  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


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
search --no-floppy --fs-uuid --set e4b45b96-33a0-4c90-baab-eb1953459c63
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4b45b96-33a0-4c90-baab-eb1953459c63
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=e4b45b96-33a0-4c90-baab-eb1953459c63 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4b45b96-33a0-4c90-baab-eb1953459c63
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=e4b45b96-33a0-4c90-baab-eb1953459c63 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4b45b96-33a0-4c90-baab-eb1953459c63
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e4b45b96-33a0-4c90-baab-eb1953459c63 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4b45b96-33a0-4c90-baab-eb1953459c63
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e4b45b96-33a0-4c90-baab-eb1953459c63 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set f8d82ec8d82e84ca
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
# / was on /dev/sdb1 during installation
UUID=e4b45b96-33a0-4c90-baab-eb1953459c63 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=1d09a48f-ace3-4db5-9b0b-3641ae4db0a0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  18.1GB: boot/grub/core.img
  43.1GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
   1.1GB: boot/initrd.img-2.6.31-20-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
   1.0GB: boot/vmlinuz-2.6.31-20-generic
   1.1GB: initrd.img
    .5GB: initrd.img.old
   1.0GB: vmlinuz
    .5GB: vmlinuz.old

---

### Post by prodigy_ on 2010-04-08
Ok, the problem is that your config file (grub.cfg) belongs to Grub2 while it looks like legacy grub (0.97) resides in the MBR of **sdb** (your Linux drive).

To resolve this you may use the following commands (from Live CD):

1. ```
sudo mount /dev/sdb1 /mnt
```
2. ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```

Then you'll need to reboot and (from your Ubuntu installation) you may use:

3. ```
sudo update-grub
``` if you want to add an entry for Win7 to Grub boot menu. (Before doing this, run System/Administration/Update Manager though.)

Make sure that you're booting from your Linux drive when you reboot (or you'll just boot into Win7, obviously). 

---

Alternatively, you can install Grub2 to **sda** (your Win7 drive). Then you won't need to choose the drive that you want to boot from at every reboot.

More info in [this HOWTO](https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202).

---

### Post by Suse on 2010-04-08
I've carried out steps 1 and 2. The Grub bootloader menu has returned, but no matter which option I pick, I get a message: 'Error: no such device [huge code], Failed to boot default entries, press any key to continue.'

---

### Post by prodigy_ on 2010-04-08
Ok, then use the workaround described [here](http://ubuntuforums.org/showpost.php?p=8384516&postcount=2) to disable the use UUIDs for Grub.

You can do it all directly from from Grub boot menu (when you press "c" there you're dropped to Grub shell).

Take note that instead of ```
set root=(hd0,1)
``` you'll need ```
set root=(hd1,1)
```

---

### Post by oldfred on 2010-04-08
Did you get any errors when you reinstalled grub?

IF you run the script has the first entry changed from 
=> Grub [COLOR=DarkRed]0.97[/COLOR] is installed in the MBR of /dev/sdb and looks on the same drive
in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

to something like this?
 => Grub [COLOR=DarkRed]1.97[/COLOR] is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub.

---

### Post by Suse on 2010-04-08
Thanks, guys.

Prodigy, if I'm understanding correctly, I booted to the external drive Grub menu, pressed 'c'. Where it said set root, it was already set to hd1,1. 

Oldfred, I can't see anywhere that it gives me this information. I ran the script again and got this:


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /ntldr /NTDETECT.COM

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

sdc: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd4a0fe34

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   586,083,329   586,083,267   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcbcdf9f3

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   964,687,184   964,687,122  83 Linux
/dev/sdb2         964,687,185   976,768,064    12,080,880   5 Extended
/dev/sdb5         964,687,248   976,768,064    12,080,817  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F8D82EC8D82E84CA                       ntfs                                     
/dev/sdb1        e4b45b96-33a0-4c90-baab-eb1953459c63   ext4                                     
/dev/sdb5        1d09a48f-ace3-4db5-9b0b-3641ae4db0a0   swap                                     
/dev/sdc         1E00-010B                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/F8D82EC8D82E84CA  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc         /media/1E00-010B         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


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
search --no-floppy --fs-uuid --set e4b45b96-33a0-4c90-baab-eb1953459c63
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4b45b96-33a0-4c90-baab-eb1953459c63
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=e4b45b96-33a0-4c90-baab-eb1953459c63 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4b45b96-33a0-4c90-baab-eb1953459c63
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=e4b45b96-33a0-4c90-baab-eb1953459c63 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4b45b96-33a0-4c90-baab-eb1953459c63
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e4b45b96-33a0-4c90-baab-eb1953459c63 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4b45b96-33a0-4c90-baab-eb1953459c63
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e4b45b96-33a0-4c90-baab-eb1953459c63 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set f8d82ec8d82e84ca
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
# / was on /dev/sdb1 during installation
UUID=e4b45b96-33a0-4c90-baab-eb1953459c63 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=1d09a48f-ace3-4db5-9b0b-3641ae4db0a0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .7GB: boot/grub/core.img
  43.1GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
   1.1GB: boot/initrd.img-2.6.31-20-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
   1.0GB: boot/vmlinuz-2.6.31-20-generic
   1.1GB: initrd.img
    .5GB: initrd.img.old
   1.0GB: vmlinuz
    .5GB: vmlinuz.old

---

### Post by Suse on 2010-04-08
Woah. I couldn't find it because I was searching for Grub and not Grub 2. Um. Not sure how I've managed this. When I boot into the bootloader, it's the older version of Grub. I'll go check which version. 

I do recall, when I first reinstalled Ubuntu about a month ago, automatic updates asking me if I wanted to update Grub to a different version, and saying yes, but nothing appearing to change. Maybe this was Grub 2. Also, today when I was prowling around the boot folder after running the live cd, I seem to recall seeing something about a couple of different versions. Sorry I'm not being very helpful.

ETA: When I try to boot, the menu is 1.97 beta 4.

---

### Post by oldfred on 2010-04-08
I would try the manual boot per prodigy_ suggestions.

No, you have upgraded to grub2 which for Karmic is 1.97 beta4. Lucid will be 1.98 for grub2.

It looks correct in the MBR, but must have problems.

---

### Post by prodigy_ on 2010-04-08
I'll explain.

The "huge code" that you see in Grub error message is the UUID of some partition.

Now, bootinfo script says that the UUID value in your boot.cfg file is perfectly correct. Since you still can't boot, it may be due to a Grub2 bug. (Possibly [this one](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/403408).)

The workaround is to tell Grub to use /dev/sdXX instead of UUID. In your case it'll be /dev/sdb1. The exact set of commands for you (from Grub boot menu):

```
c
set root=(hd1,1)
linux /vmlinuz root=/dev/sdb1 ro
initrd /initrd.img
boot
```

If it'll work then you can follow the rest of the instructions in the post I linked earlier (to make this change permanent).

---

### Post by Suse on 2010-04-08
OK, tried loading the menu, then I went into edit. Is that right?

There was a lot of info there. I changed it to your commands above, deleting everything else. Then I did control x to boot and got the message, 'booting a command list, error: unknown command c, press any key to continue.'

If it's any help, this is what was there before:

recordfail=1
if [ -n ${have_grubenv} ] ; then save_env recordfail ; fi
set quiet=1
insmod ext2
setroot=(hd1,1)
search --no-floppy --fs-uuid --set 'huge code'

linux /boot /vmlinuz-2.6.31-20-generic root=uuid='huge code' ro quiet splash
initrd /boot/initrd.img-2.6.31.20-generic

I really appreciate your time, Prodigy.

---

### Post by Suse on 2010-04-09
Just realised my mistake in pressing 'e'. OK, have gone into the command line. After keying the second line 'linux...', I get, 'error: file not found'.

I don't know if this is a sign of a bug, but when I first reinstalled Ubuntu it updated Grub that day, and when I rebooted there were seven menu options. First is Ubuntu Linux 2.6.31-20-generic, which I always go into. Second is recovery. Third is Ubuntu 2.6.31-14-generic. Then it's recovery, two memory tests, and XP (which is on /dev/sda1).

---

### Post by Suse on 2010-04-10
Can anyone help please?

---

### Post by oldfred on 2010-04-10
As new kernel updates are released they are added to the menu. We normally recommend that you keep 2 versions as the newer may not let you boot.

Your problem seems to be different. You were able to use grub2.

I think this suggests eliminating the entire search line before manually booting as you did, you should be able to use tab on parts of your input to make it easier not to make typos:
Boot Problems:search or no such device
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

### Post by Suse on 2010-04-10
Hi,

I carried out step 1: deleted the no-floppy line.

When I tried to boot, it gave me 'error: file not found'.

---

### Post by oldfred on 2010-04-10
I am grasping at straws here. Your boot_info script looks ok and the files seem to be there.

I have seen where some BIOS (particularly intel) will not boot unless there is a boot flag on a primary partition. Windows has to have it, linux does not use it. I might try adding a boot flag on sdb1. beyond that I am lost.

---

### Post by Suse on 2010-04-10
Hi Oldfred, I do really appreciate you trying here. My BIOS is American Megatrends. I'm not sure what adding a boot flag on sdb1 means or how I'd do that.

I wonder if all this is to do with the order in which I've installed the operating systems, due to using two hard drives with operating systems rather than a dual boot single hard drive. I don't really understand how it works, but I wonder if things would be different if I'd installed Windows first, then Ubuntu.

As I mentioned, I've installed and reinstalled versions of Windows and Linux. So this time round, it was Ubuntu first, external, and Windows 7 second (over WinXP), internal. Prior to my second last install of Linux (PCLOS), I've never even had a boot menu. I've always had to go into the BIOS and swap hard drive priority around, depending on whether I want to use Linux or Windows. This time round, swapping to the external hard drive doesn't get me further than the Grub menu.

Probably this has nothing to do with anything. Just trying to offer all the info I can think of that may possibly help.

---

### Post by oldfred on 2010-04-10
You can set boot flag with gparted or disk utility from a live cd. With gparted it is right click on partition and manage flags. With disk utility it is a check box on the partition.

Order of install should not matter. I prefer having operating systems on separate drives although all mine are internal. You still should be able to use f12 or whatever and boot each drive if it is set up correctly. Then with grub it will also find windows and allow you to boot either when you set ubuntu as the default.

Is you external an esata?

---

### Post by Suse on 2010-04-10
I haven't changed the boot flag yet, because I wanted to run by you what I saw in GParted. Prior to this, I have never even noticed there being an sdc.

sda - my Windows drive
sdb: fat32 at 3.76 gb
sdc - my Linux drive, which breaks down to sdc1 ext 4 (460 gb - the installation), sdc2 extended, and sdc5 Linux-swap.

No, my external hard drive isn't esata.

---

### Post by oldfred on 2010-04-10
Perhaps part or all of the problem is the external is at sdc when before it was sdb? It looks like the 4GB usb key became sdb. Now we also have to try with and without each. Generally because UUIDs are used the boot order should not matter. 

All the hd1 commands then should be hd2 if the USB key was hd1.

---

### Post by Suse on 2010-04-10
Yes, I'm thinking the same in a muddled up way. So should I try setting sdc1 with a boot flag? I haven't tried anything yet, because I'm worried about messing things up so badly I won't get into Windows. Then again, I have a live Ubuntu cd, so that's not going to be a problem, is it?

Incidentally, when I looked at sda1, it didn't give me the opportunity to do anything boot flag related, but when I right clicked the others, it looked like it would let me set a boot flag.

---

### Post by oldfred on 2010-04-10
You only should have one boot flag per drive and for windows it has to be the boot partition. I now do not think that is the problem but it does not hurt to have it.

I think the drive order is the issue.

---

### Post by Suse on 2010-04-10
I have confused the issue, apologies. My linx drive *is *sdb. I had plugged in a flash drive to pull a document from it. This hasn't been the problem all along though - I only plugged the flash drive in for ten minutes. 

Now when I go into GParted, there are only sda and sdb. I do wonder why Linux changes to sdc, rather than the flash drive becoming that, because that is what's happening.

I've tried setting the three parts of Linux (sdb 1, 2 and 5) with the boot flag, but the problem is still the same.

---

### Post by oldfred on 2010-04-10
The flag only needs to be on one primary partition. Some BIOS check before booting as that is the windows requirement.

Although I do not think it will help try rerunning the boot_info script. It looked ok originally so I do not expect to be able to see anything.

---

### Post by Suse on 2010-04-11
These are the new results. Whether this makes a difference: the boot flag is now set to the correct Linux partition. Prior to this, it wasn't set at for Linux.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /ntldr /NTDETECT.COM

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd4a0fe34

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   586,083,329   586,083,267   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcbcdf9f3

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   964,687,184   964,687,122  83 Linux
/dev/sdb2         964,687,185   976,768,064    12,080,880   5 Extended
/dev/sdb5         964,687,248   976,768,064    12,080,817  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F8D82EC8D82E84CA                       ntfs                                     
/dev/sdb1        e4b45b96-33a0-4c90-baab-eb1953459c63   ext4                                     
/dev/sdb5        1d09a48f-ace3-4db5-9b0b-3641ae4db0a0   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/F8D82EC8D82E84CA  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


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
search --no-floppy --fs-uuid --set e4b45b96-33a0-4c90-baab-eb1953459c63
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4b45b96-33a0-4c90-baab-eb1953459c63
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=e4b45b96-33a0-4c90-baab-eb1953459c63 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4b45b96-33a0-4c90-baab-eb1953459c63
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=e4b45b96-33a0-4c90-baab-eb1953459c63 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4b45b96-33a0-4c90-baab-eb1953459c63
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e4b45b96-33a0-4c90-baab-eb1953459c63 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e4b45b96-33a0-4c90-baab-eb1953459c63
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e4b45b96-33a0-4c90-baab-eb1953459c63 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set f8d82ec8d82e84ca
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
# / was on /dev/sdb1 during installation
UUID=e4b45b96-33a0-4c90-baab-eb1953459c63 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=1d09a48f-ace3-4db5-9b0b-3641ae4db0a0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .7GB: boot/grub/core.img
  43.1GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
   1.1GB: boot/initrd.img-2.6.31-20-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
   1.0GB: boot/vmlinuz-2.6.31-20-generic
   1.1GB: initrd.img
    .5GB: initrd.img.old
   1.0GB: vmlinuz
    .5GB: vmlinuz.old

---

### Post by oldfred on 2010-04-11
IF you boot from sdb do you get any grub errors as it shows grub2 in the MBR now.
Does your win7 boot ok when you boot from sda? You still seem to have some older windows files in the boot but they may not make a difference.

---

### Post by Suse on 2010-04-11
Windows boots no problem. I have a back up of XP, so those should be the older files.

No, sadly, when I boot from sdb, I still have, 'error: no device: e4b4etc'.

---

### Post by oldfred on 2010-04-11
If you have tried editing the manual boot entries several times and they do not work, then reverting to old grub may be the only possibility. I normally do not recommend it.

HowTo: Revert from grub2 to Legacy Grub. 
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

---

### Post by oldfred on 2010-04-11
Have we done everything. I found these links and think you have tried most of the suggestions:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)
[http://ubuntuforums.org/showthread.php?t=1337254](http://ubuntuforums.org/showthread.php?t=1337254)

---

### Post by Suse on 2010-04-12
Hi Oldfred,

I had tried most of the things in those links. I've since uncommented GRUB-DISABLE-LINUX-UUID=true. When I try sudo update-grub, I then get grub-probe error: cannot find a device for /.

So I've tried uninstalling and reinstalling Grub. In short, I got the message, 'Couldn't find package manager' when purging. I carried on, and it went fine until I keyed 'sudo grub-install /dev/sdb'. After this I get, 'Could not find device for /boot:Not found of not a block device'.

This is a copy of everything:

ubuntu@ubuntu:~$ sudo mv /boot/grub /boot/grub_backup
ubuntu@ubuntu:~$ sudo mkdir /boot/grub
ubuntu@ubuntu:~$ ls /boot
abi-2.6.31-14-generic     memtest86+.bin
config-2.6.31-14-generic  System.map-2.6.31-14-generic
grub                      vmcoreinfo-2.6.31-14-generic
grub_backup
ubuntu@ubuntu:~$ sudo apt-get --purge remove startupmanager
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ubuntu@ubuntu:~$ sudo apt-get --purge remove startupmanager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package startupmanager
ubuntu@ubuntu:~$ sudo apt-get --purge remove grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub-common* grub-pc*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 4,170kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 120318 files and directories currently installed.)
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for sreadahead ...
Processing triggers for install-info ...
ubuntu@ubuntu:~$ sudo apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  grub-common
Suggested packages:
  grub-doc mdadm multiboot-doc grub-emu
The following NEW packages will be installed:
  grub grub-common
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,400kB of archives.
After this operation, 3,363kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main grub-common 1.97~beta4-1ubuntu3 [994kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main grub 0.97-29ubuntu59 [407kB]
Fetched 1,400kB in 1s (950kB/s)     
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 120095 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.97~beta4-1ubuntu3_i386.deb) ...
Selecting previously deselected package grub.
Unpacking grub (from .../grub_0.97-29ubuntu59_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for sreadahead ...
Setting up grub-common (1.97~beta4-1ubuntu3) ...

Setting up grub (0.97-29ubuntu59) ...

ubuntu@ubuntu:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/memtest86+.bin
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd4a0fe34

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36482   293041633+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbcdf9f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60049   482343561   83  Linux
/dev/sdb2           60050       60801     6040440    5  Extended
/dev/sdb5           60050       60801     6040408+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo grub-install /dev/sdb
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

*

After checking this error on Google, I've tried keying, 'grub-install --recheck /dev/sda1', which gives me, same error.

I tried, 'sudo grub', then 'find /boot/grub/stage1', which gives me 'Error 15:file not found'.

Under 'Just Notes' of the How to Revert link you posted above, I've tried the failsafe method, but it doesn't work for me. I've also tried the advice for if update-grub fails to find other OS's (not sure why, thought I might as well). It works fine till I key, 'sudo update-grub', then I get, 'grub-probe: error: cannot find a device for /.'

I'm utterly at a loss with all of this. If I can't even reinstall Grub, is there anything else I can do? Does this mean I need to do a fresh install of Ubuntu? From what I've read on the forums, I'm not even sure that would work.

Thanks.

---

### Post by Suse on 2010-04-12
I've tried following the info on this [link ]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")too, and had this result:

ubuntu@ubuntu:~$ mount | tail -1 
/dev/sda1 on /media/F8D82EC8D82E84CA type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
ubuntu@ubuntu:~$ mount | tail -2
/dev/sdb1 on /media/e4b45b96-33a0-4c90-baab-eb1953459c63 type ext4 (rw,nosuid,nodev,uhelper=devkit)
/dev/sda1 on /media/F8D82EC8D82E84CA type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
ubuntu@ubuntu:~$ ls /media/e4b45b96-33a0-4c90-baab-eb1953459c63/boot
abi-2.6.31-14-generic         memtest86+.bin
abi-2.6.31-20-generic         System.map-2.6.31-14-generic
config-2.6.31-14-generic      System.map-2.6.31-20-generic
config-2.6.31-20-generic      vmcoreinfo-2.6.31-14-generic
grub                          vmcoreinfo-2.6.31-20-generic
initrd.img-2.6.31-14-generic  vmlinuz-2.6.31-14-generic
initrd.img-2.6.31-20-generic  vmlinuz-2.6.31-20-generic
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/0d104aff-ec8c-44c8-b811-92b993823444 /dev/sdb
mkdir: cannot create directory `/media/0d104aff-ec8c-44c8-b811-92b993823444/boot': No such file or directory
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/e4b45b96-33a0-4c90-baab-eb1953459c63 /dev/sdb
Installation finished. No error reported.
This is the contents of the device map /media/e4b45b96-33a0-4c90-baab-eb1953459c63/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
ubuntu@ubuntu:~$ 

When I reboot, it's still exactly the same problem. I'm supposing, now that I've just read it, this is because my Ubuntu is on a second hard drive. Since - I think?? - I'm am indeed still using Grub two, that's another reason the 'Recovery using Microsoft Windows and Its Bootloader' won't work, so I haven't followed those instructions. I will try this Super Grub thing, once I've stopped weeping inside. :wink:

---

### Post by m4tic on 2010-04-12
if you want to _reinstall grub_, try this using the **ubuntu 9.10** live cd
To list your drives and partition, do
```
sudo fdisk -l
```
 
*(where x is device letter, # is partition number)*
```
[FONT=Courier New]$sudo mount /dev/sdx# /mnt[/FONT]
[FONT=Courier New]$sudo mount --bind /dev /mnt/dev[/FONT]
$sudo mount --bind /proc /mnt/proc
[FONT=Courier New]sudo chroot /mnt[/FONT]
[FONT=Courier New]#grub-install --recheck /dev/sdx[/FONT]
 
[FONT=Courier New]#reboot[/FONT] 

```
 
Then when it boots, go to your ubuntu partition and enter in terminal ```
 $sudo update-grub2
```
 
After the last command. It should include all OS's on the other device
 
ED: *i only read first post*

---

### Post by Suse on 2010-04-12
Oh, what a day.

Finally, I have Ubuntu. I don't think my experiences will help anyone, but here goes anyway. 

Thanks, m4tic, oldfred and prodigy. I tried what you suggested, m4tic. Unfortunately same old error. I also followed all the relevant instructions on the link I pasted two posts up. 

Decided to install Ubuntu again on a small partition side by side with Ubuntu. Well, I thought it might make Grub all nice again. Of course, same error.

Then I completely reinstalled Ubuntu and ... [SIZE="1"]same error[/SIZE].

So I installed PCLOS. Everything booted up nicely - Linux and Windows. Next, I installed Ubuntu, completely wiping PCLOS.

When Ubuntu attempted to reboot at the end of the install, I got the error: 'loading stage 1.5, Grub loading, please wait, error 15'. And now I remember I had this error before when installing Ubuntu once. On that previous ocassion, I reinstalled Ubuntu and all seemed well. Can't remember when, where, or whatever.

However, when I went into the BIOS to instruct my PC to boot from my primary (Windows) hard drive, not the external Ubuntu (I swear I'm not making any of this up), it launched the Grub menu - it's never ever launched Grub unless the BIOS is set to boot from the external drive. Maybe I'm going mad. From the Grub menu, I told it to boot Ubuntu - and it did! I then checked Windows 7 was working, and it is.

Now what I'm wondering is, if I were to update Grub to Grub 2, is it likely things would mess up again, bearing in mind I've just had this loading stage 1.5 error 15?

Is there any benefit to having Grub 2?

---

### Post by oldfred on 2010-04-12
IF you have it working I would not change. 

What you did different was install grub to the internal drive not the external that has the Ubuntu install. If you unplug the external you will not be able to boot. You will see the grub in sda and pointing to a UUID that is on the external if you rerun the boot info script (you do not have to post it). I would also install grub to the external and see if you can get that to boot, only then you may want to reinstall the windows boot loader to the internal.

I like to have the boot loader on the same drive as the operation system but have not seen anyone with the problem(s) you have had. There must be a BIOS or drive configuration somewhere that we are missing?? All my drives are internal and sometimes the externals have had issues with drive numbers. Usually when Ubuntu is installed on the external grub goes on the internal and users want to switch that around so they can boot without the external and we just reinstall grub and windows boot loaders and it works.

Grub2 finds other systems better, it is the future as old grub has not been maintained for years, but some computers still have issues with grub2. The new 1.98 with Lucid has further improvements in grub2.

---

### Post by Suse on 2010-04-12
Gah! Yes, you are right. I don't know why that's happened, as I did a simple complete wipe of the external hard drive - no telling Ubuntu where precisely to install what, just to wipe PCLOS and reclaim the external hard drive. But funnily enough, PCLOS does actually call the external drive sda, and the internal sdb (reversing the way Ubuntu does things). It's done that both times I installed it. Maybe that had something to do with it (she says, clutching at straws).

Obviously I'd prefer the internal drive to have a Win7 bootloader, but I don't have a clue how to do that. Oh, unless I install that Super Grub thing again. That gave me the option of which drive to boot. Fiddling about with Windows itself scares me, because I know it wants to take over everything it can.

---

### Post by oldfred on 2010-04-12
This has instructions on installing boot loaders:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You can also from linux install a basic windows boot loader where sdX is your windows drive sda, sdb etc:
sudo  apt-get install lilo
sudo lilo -M /dev/sdX mbr

---

### Post by Suse on 2010-04-12
You're not going to believe this, oldfred. I just carried out the second option to restore the Windows bootloader. Now the internal hard drive boots straight into Windows, no menus or anything. But the external is now refusing to boot: loading stage 1.5, Grub loading, please wait, error 15. Is there any way to reverse what I've just done?

---

### Post by oldfred on 2010-04-12
Instead of re-installing grub to sdb install it to sda the internal drive. 

There has to be something about your external that it does not want to let you boot.

---

### Post by Suse on 2010-04-12
I must be getting a bit smarter because I thought that too. Do you know how I would normally do I that? I tried following the [How To]("https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202") suggested by prodigy, but it doesn't bring up the prompt. It just tells me Grub is already installed. 

Do I need to do something first to tell it where to install? I tried 

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Discovered that wasn't a clever idea. I had to reinstall the Windows bootloader as I couldn't get into Win7 after that - a Grub error.

---

### Post by oldfred on 2010-04-12
it is the same except sdb or (hd1) in grub legacy.

Your install is not in sda1 either its sdb1. And those commands for for grub2. Have not we changed to grub legacy? I am so lost also.

sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb


Grub legacy requires the root, setup commands.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
#reset grub boot
sudo grub
find /boot/grub/stage1 #you will get a response such as  (hd1,1)
root (hdx,y) #use the numbers from the previous command x is drive, y is partition  or root (hd1,1)
setup (hd1) # use the number from the find hdx or hd1

It is very important to use the correct reinstall. the error 15 command is often from mixed grubs where one is installed and the commands for the other are used to partially install it.

---

### Post by Suse on 2010-04-13
It just gave the usual error, so I reinstalled Ubuntu. I actually installed PCLOS first again, thinking I might go back there instead. Thing is, the both drives boot no problem with that OS. How strange. And PCLOS uses Grub.

Anyway, PCLOS has its own little quirks, so I reinstalled Ubuntu. All is well. I can't boot from external drive - it freezes on 'Grub loading stage 1.5: grub loading, please wait'. But my internal drive now has the Grub menu and allows me to boot Ubuntu or Win7.

I didn't do anything differently in this install, except use another Karmic cd. My previous install kept freezing and asked for the keyring thing to start the internet each time I booted up. This time round, seems ok.

Thank you for all your help, oldfred. You've been so patient and generous with your time. :)

---

### Post by oldfred on 2010-04-13
There has to be some issue with grub and you external drive. I did see one user a day or two ago say his external was only bootable using raid as the BIOS setting. Grub generally does not like raid for desktop installs as raid is for server installs and has different add-ins.

You are welcome. Many times we spend too much time trying to fix when a reinstall often is the better choice.

---

### Post by m4tic on 2010-04-15
Load default settings in BIOS, if it does not work, you might want to try out LILO, or do the method i posted using the old Grub in Ubuntu 9.04 (8.10 and previous won't work since they use EXT3)

---

