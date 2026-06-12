---
title: "error: out of disk - on upgrade"
date: 2011-01-02
forum: General Help
---

### Post by inertself on 2011-01-02
Had 9.04 and winxp dual boot setup for quite awhile with no problems, loved it!  Upgraded to 10.04 or 10.10 (can't remember which one) one day and after reboot I got an error: out of disk and grub rescue prompt.  Went through a few different attempts to wipe out and re-install grub which did not help.  I then wiped out the ext partition and re-installed 9.04, which allowed grub to work properly but it would only boot to my windows partition, when I tried to boot to the 9.04 partition it would say that the partition did not exist.  I tried re-installing 10.10 again which went back to the same old error:out of disk and grub rescue prompt. 

Here is the link to my boot info : [http://paste.ubuntu.com/549586/](http://paste.ubuntu.com/549586/)

Thanks to wilee-nilee for helping out this far, apparently when I tried to fix grub it put copies of it all over the place :shock:

New to the complex stuff, but have been doing basic dual boot setups for awhile on all my friends machines.  Any help would be greatly appreciated.

Oh - I cannot mess with anything on the xp partition, wiping it out would be a huge pain since I have licensed software that is not easily replaced.

Here is the text from the link, it's easier:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/winboot/wubildr

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

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
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   210,483,629   210,483,567   7 HPFS/NTFS
/dev/sda2         210,485,248   621,236,223   410,750,976  83 Linux
/dev/sda3         621,238,270   625,139,711     3,901,442   5 Extended
/dev/sda5         621,238,272   625,139,711     3,901,440  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8EE04E75E04E6395                       ntfs                                     
/dev/sda2        7fc1a66a-f0e8-44b0-8243-a2437636dba7   ext4                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        e35b0f03-aadd-43ee-aba1-4158dc1c9482   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/7fc1a66a-f0e8-44b0-8243-a2437636dba7 ext4       (rw,nosuid,nodev,uhelper=udisks)


======================== sda1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 3
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


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
search --no-floppy --fs-uuid --set 7fc1a66a-f0e8-44b0-8243-a2437636dba7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 7fc1a66a-f0e8-44b0-8243-a2437636dba7
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
	search --no-floppy --fs-uuid --set 7fc1a66a-f0e8-44b0-8243-a2437636dba7
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7fc1a66a-f0e8-44b0-8243-a2437636dba7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7fc1a66a-f0e8-44b0-8243-a2437636dba7
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7fc1a66a-f0e8-44b0-8243-a2437636dba7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7fc1a66a-f0e8-44b0-8243-a2437636dba7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7fc1a66a-f0e8-44b0-8243-a2437636dba7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 8ee04e75e04e6395
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
UUID=7fc1a66a-f0e8-44b0-8243-a2437636dba7 /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


 193.8GB: boot/grub/core.img
 129.3GB: boot/grub/grub.cfg
 108.3GB: boot/initrd.img-2.6.35-22-generic
 193.8GB: boot/vmlinuz-2.6.35-22-generic
 108.3GB: initrd.img
 193.8GB: vmlinuz
```

---

### Post by Rubi1200 on 2011-01-02
The problem I see is here on sda1:
```
/ubuntu/winboot/menu.lst
```You have vestiges of an old Wubi install which is being picked up, I think, at some point during the boot process.

If you look further down in the results you can see that the script is picking up on this.

Other than that, everything looks normal.

I think the way to resolve this is:
restore the Windows bootloader and then reinstall GRUB from the LiveCD
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Apologies to wilee-nilee for jumping in like this :-)

---

### Post by wilee-nilee on 2011-01-02
> **Rubi1200 said:**
> The problem I see is here on sda1:
```
/ubuntu/winboot/menu.lst
```You have vestiges of an old Wubi install which is being picked up, I think, at some point during the boot process.

If you look further down in the results you can see that the script is picking up on this.

Other than that, everything looks normal.

I think the way to resolve this is:
restore the Windows bootloader and then reinstall GRUB from the LiveCD
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Apologies to wilee-nilee for jumping in like this :-)

Hey we are all here together, notice the menu.list in the script as well.

Probably needs a grub purge.

Thanks Rubi1200, I thought this needed a little more eyes on it.

---

### Post by inertself on 2011-01-02
OK great, I'll give that a try and then update you guys.  Thanks :)

---

### Post by inertself on 2011-01-02
All I have is the restore CD that came with my computer, not an actual winxp cd.  The only options I have are to wipe out and restore to original state, or not to.  If I get a generic winxp cd will that work?

Never-mind, it will work.

---

### Post by inertself on 2011-01-02
OK well I used the xp cd to run fixboot and the fixmbr.  This all worked fine and I was able to boot directly into xp.  

Now the problem is basically the same when I try to re-install grub.  I went through the commands
sudo fdisk -l
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

all those went smoothly
but then when I went to use
sudo update-grub
it doesn't think I have mounted the partition.  I rebooted anyway and I'm back to the same old error: out of disk and grub rescue prompt.

---

### Post by wilee-nilee on 2011-01-02
So run the script again it is in my signature, when you go to paste the text click on the # in the reply window and paste between the code tags.

---

### Post by inertself on 2011-01-02
I re-did the fixboot and fixmbr, so things might already be different:


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/winboot/wubildr

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

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
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   210,483,629   210,483,567   7 HPFS/NTFS
/dev/sda2         210,485,248   621,236,223   410,750,976  83 Linux
/dev/sda3         621,238,270   625,139,711     3,901,442   5 Extended
/dev/sda5         621,238,272   625,139,711     3,901,440  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8EE04E75E04E6395                       ntfs                                     
/dev/sda2        7fc1a66a-f0e8-44b0-8243-a2437636dba7   ext4                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        e35b0f03-aadd-43ee-aba1-4158dc1c9482   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


======================== sda1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 3
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt

================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

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
search --no-floppy --fs-uuid --set 7fc1a66a-f0e8-44b0-8243-a2437636dba7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 7fc1a66a-f0e8-44b0-8243-a2437636dba7
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
    search --no-floppy --fs-uuid --set 7fc1a66a-f0e8-44b0-8243-a2437636dba7
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7fc1a66a-f0e8-44b0-8243-a2437636dba7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 7fc1a66a-f0e8-44b0-8243-a2437636dba7
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7fc1a66a-f0e8-44b0-8243-a2437636dba7 ro single 
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
    search --no-floppy --fs-uuid --set 7fc1a66a-f0e8-44b0-8243-a2437636dba7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 7fc1a66a-f0e8-44b0-8243-a2437636dba7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 8ee04e75e04e6395
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
UUID=7fc1a66a-f0e8-44b0-8243-a2437636dba7 /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


 193.8GB: boot/grub/core.img
 129.3GB: boot/grub/grub.cfg
 108.3GB: boot/initrd.img-2.6.35-22-generic
 193.8GB: boot/vmlinuz-2.6.35-22-generic
 108.3GB: initrd.img
 193.8GB: vmlinuz

```

---

### Post by wilee-nilee on 2011-01-02
I think we need to get the grub mix out and grub2 in all by itself. Follow the chroot method in this link.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

I don't think the menu.list in the XP is causing the menu.list in the script, it seems to be just left over from the install of 9.04 as a dual boot for some reason.

So it may worth doing the chroot purge and then seeing if after you boot back to Ubuntu, 
sudo update-grub
then try XP.

---

### Post by inertself on 2011-01-02
I tried the second method on the link for restoring grub, and I'm back to square one again.  I am about to just run windows on the 108gb partition that I have setup for it and worry about fixing it later.  I've tried all of this in the past and again today, nothing seems to work.  When I installed the 9.10 version grub worked but it wouldn't recognize the linux partition but at least it would let me boot to windows without the grub bootloader cd.

---

### Post by wilee-nilee on 2011-01-02
> **inertself said:**
> I tried the second method on the link for restoring grub, and I'm back to square one again.  I am about to just run windows on the 108gb partition that I have setup for it and worry about fixing it later.  I've tried all of this in the past and again today, nothing seems to work.  When I installed the 9.10 version grub worked but it wouldn't recognize the linux partition but at least it would let me boot to windows without the grub bootloader cd.

Did you see this part of the link.

Why Chroot?
Since you will boot from the Live CD, commands executed in the normal manner would act on the Live CD's temporary system files and not the files on your real installation's partition. By 'chroot-ing' into your Ubuntu partition, the commands will act on your installation and remain after you remove the CD and reboot.

If you followed my link you posted to fast to have done it correctly

---

### Post by inertself on 2011-01-02
> **wilee-nilee said:**
> I think we need to get the grub mix out and grub2 in all by itself. Follow the chroot method in this link.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

I don't think the menu.list in the XP is causing the menu.list in the script, it seems to be just left over from the install of 9.04 as a dual boot for some reason.

So it may worth doing the chroot purge and then seeing if after you boot back to Ubuntu, 
sudo update-grub
then try XP.


OK I'll give this a shot, then I'm calling it a night.  Seems to me I may have done this also, chroot sounds familiar (my computer has been booting to only xp for like 5 months now).  I'm going to try this though and we'll hope it takes care of it.

---

### Post by inertself on 2011-01-02
Wait which one should I do - wubi only?

---

### Post by wilee-nilee on 2011-01-02
> **inertself said:**
> OK I'll give this a shot, then I'm calling it a night.  Seems to me I may have done this also, chroot sounds familiar (my computer has been booting to only xp for like 5 months now).  I'm going to try this though and we'll hope it takes care of it.

There may a conflict though here in that your script shows this.
Boot files/dirs:   /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/winboot/wubildr

When it should just look like this, if Wubi is basically gone.
Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

So the problem may be a mixture of things you have 4 bootloaders or the remnants of and 2 operating systems, do you see where I'm going with this. It is fixable but in the right way and correct order. So we know XP will boot in if the MS bootloader is in the MBR, and you have a rescue grub cd of some sort that gets you into XP as well.

So I think the purge and reinstall of grub will fix part of the problem we also want to clean up your XP boot as posted, if you want to insure its stability.

Don't give up and just try running XP without getting it cleaned up correctly as well, you may have problems again.

---

### Post by wilee-nilee on 2011-01-02
> **inertself said:**
> Wait which one should I do - wubi only?

No run the regular chroot on the installed setup. You don't have a working wubi correct?

---

### Post by inertself on 2011-01-02
Ok thanks.  No I don't have a working wubi - that's for vbox right?  I got rid of that awhile back.  I'm doing the steps in the why chroot? section now.  I just had to reboot because I set the mount point to /mnt instead of /mnt/temp

---

### Post by wilee-nilee on 2011-01-02
> **inertself said:**
> Ok thanks.  No I don't have a working wubi - that's for vbox right?  I got rid of that awhile back.  I'm doing the steps in the why chroot? section now.  I just had to reboot because I set the mount point to /mnt instead of /mnt/temp

You could of tried it without the chroot but messing around at this point seems counter productive, you sharpen the blade so to speak before you start cutting. Seems like the more likely method of clean up.

Wubi doesn't have anything to do with vbox you wouldn't see any boot stuff for it. Wubi and vbox share that sort of virtual idea though in the way they run, but wubi needs to boot from the MS bootloader so it puts boot files and its voodoo in the MS boot.

---

### Post by inertself on 2011-01-02
shucks, and I thought that was going to work.  Went through it and all went good - I have not done that method before.  Got the same message on reboot - error: out of disk. 
Everything went smoothly I thought, did exactly as the instructions said.  Maybe try going back to 9.10?

---

### Post by inertself on 2011-01-02
It even listed everything seemingly perfect after the update-grub command was done.  Here is the latest boot info:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/winboot/wubildr

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

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
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   210,483,629   210,483,567   7 HPFS/NTFS
/dev/sda2         210,485,248   621,236,223   410,750,976  83 Linux
/dev/sda3         621,238,270   625,139,711     3,901,442   5 Extended
/dev/sda5         621,238,272   625,139,711     3,901,440  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8EE04E75E04E6395                       ntfs                                     
/dev/sda2        7fc1a66a-f0e8-44b0-8243-a2437636dba7   ext4                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        e35b0f03-aadd-43ee-aba1-4158dc1c9482   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


======================== sda1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 3
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt

================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

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
search --no-floppy --fs-uuid --set 7fc1a66a-f0e8-44b0-8243-a2437636dba7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 7fc1a66a-f0e8-44b0-8243-a2437636dba7
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
    search --no-floppy --fs-uuid --set 7fc1a66a-f0e8-44b0-8243-a2437636dba7
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7fc1a66a-f0e8-44b0-8243-a2437636dba7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 7fc1a66a-f0e8-44b0-8243-a2437636dba7
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7fc1a66a-f0e8-44b0-8243-a2437636dba7 ro single 
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
    search --no-floppy --fs-uuid --set 7fc1a66a-f0e8-44b0-8243-a2437636dba7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 7fc1a66a-f0e8-44b0-8243-a2437636dba7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 8ee04e75e04e6395
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
UUID=7fc1a66a-f0e8-44b0-8243-a2437636dba7 /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


 193.8GB: boot/grub/core.img
 129.3GB: boot/grub/grub.cfg
 108.3GB: boot/initrd.img-2.6.35-22-generic
 193.8GB: boot/vmlinuz-2.6.35-22-generic
 108.3GB: initrd.img
 193.8GB: vmlinuz


```


Maybe try getting the latest version of 10.10 since this is the old one that I originally tried installing?

---

### Post by wilee-nilee on 2011-01-02
I think just waiting for the person I sent the PM to, to have a look will be your best bet.

The script looks the same so I think something is going on not sure what.

---

### Post by oldfred on 2011-01-02
wilee-nilee - Bears lost, so I am back, but you guys have done everything I would suggest. Normally if the quick grub2 reinstall does not work the full chroot one does. I do not think anything related to the wubi is an issue as the windows boots.  Wubi should be cleaned out but that is later.

this link says the out of disk is a issue with finding the UUID or the search with floppy, UUID looks correct:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

inertself - After you reinstalled grub2:
Do you get to grub menu or is error before that?
Do you have a floppy disk and if not is one still enabled in BIOS? Sometimes that confuses the search command. Check BIOS for enabled devices and disable any you do not actually have.

---

### Post by inertself on 2011-01-03
After I installed grub2 I got the two windows the first was where you add script?  I just selected OK, the second was where you select the bootable paritions - I selected the first drive on that not the linux partition.  I didn't get any errors during the process this time, other attempts yes but too far ago to remember which ones.  
 
I do not have a floppy drive on this computer, but when I went into the setup it had a diskette drive as a bootable selection. I disabled it and same results at the moment, I will try re-doing grub again and see how that works.

---

### Post by inertself on 2011-01-03
OK lets see if this works, attempt # 4 (for today)
 
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.
 
ubuntu@ubuntu:~$ sudo mkdir /mnt/temp
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt/temp
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; sudo mount -B $i /mnt/temp$i; done
bash: syntax error near unexpected token `sudo'
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i; done
ubuntu@ubuntu:~$ sudo cp /etc/resolve.conf /mnt/temp/etc/resolve.conf
cp: cannot stat `/etc/resolve.conf': No such file or directory
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
root@ubuntu:/# apt-get update
Hit http://extras.ubuntu.com maverick Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
Hit http://security.ubuntu.com maverick-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Hit http://us.archive.ubuntu.com maverick Release.gpg                
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US 
Hit http://extras.ubuntu.com maverick Release                        
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security Release             
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release                    
Hit http://extras.ubuntu.com maverick/main Sources                             
Hit http://security.ubuntu.com maverick-security/main Sources        
Hit http://us.archive.ubuntu.com maverick-updates Release
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Hit http://security.ubuntu.com maverick-security/restricted Sources  
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main i386 Packages
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://security.ubuntu.com maverick-security/universe i386 Packages
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick/main Sources
Hit http://us.archive.ubuntu.com maverick/restricted Sources
Hit http://us.archive.ubuntu.com maverick/universe Sources
Hit http://us.archive.ubuntu.com maverick/multiverse Sources
Hit http://us.archive.ubuntu.com maverick/main i386 Packages
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/main Sources
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Reading package lists... Done
root@ubuntu:/# apt-get ourge grub grub-pc grub-common
E: Invalid operation ourge
root@ubuntu:/# apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
The following packages will be REMOVED:
  grub-common* grub-pc*
0 upgraded, 0 newly installed, 2 to remove and 200 not upgraded.
After this operation, 5,804kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 119498 files and directories currently installed.)
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
root@ubuntu:/# update-grub
The program 'update-grub' can be found in the following packages:
 * grub
 * grub-efi-amd64
 * grub-efi-ia32
 * grub-pc
 * grub-coreboot
 * grub-ieee1275
Try: apt-get install <selected package>
root@ubuntu:/# update-grub
The program 'update-grub' can be found in the following packages:
 * grub
 * grub-efi-amd64
 * grub-efi-ia32
 * grub-pc
 * grub-coreboot
 * grub-ieee1275
Try: apt-get install <selected package>
root@ubuntu:/# sudo update-grub
sudo: unable to resolve host ubuntu
sudo: update-grub: command not found
root@ubuntu:/# grub-update
grub-update: command not found
root@ubuntu:/# apt-get install grub-common grub-pc
Reading package lists... 0%
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following NEW packages will be installed:
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 200 not upgraded.
Need to get 0B/2,204kB of archives.
After this operation, 5,804kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 119219 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.98+20100804-5ubuntu3_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.98+20100804-5ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
Setting up grub-common (1.98+20100804-5ubuntu3) ...
Setting up grub-pc (1.98+20100804-5ubuntu3) ...
 
Creating config file /etc/default/grub with new version
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ for i in /dev/pts /dev /proc /sys /boot / ; do sudo umount /mnt/temp$i ; done
umount: /mnt/temp/boot: not mounted
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 

```
 
Nope - it didn't.  I dunno, not sure what else to try.

---

### Post by wilee-nilee on 2011-01-03
As you look at your readout that you posted very helpful actually I see several errors.

I would copy and paste all those commands there are multiple mistakes, look closer, copy and paste those commands from the link to a gedit text editor in menu-accessories-text editor put on a thumb so you get them correct.

I realise you ran the commands again but I think it is important that you get them correct and get no errors for it to work. You had multiple errors while trying the commands, you corrected. Hard to say but I have found Linux in general to be quite sensitive to commands coded correctly and in the order they should be, with no errors.

It may be that you need to get into XP and the boot.ini and remove the extra stuff in that boot section. You can get in by that XP cd /fixmbr again, reboot to XP and edit the stuff out look at what I posted as extra and what it should be in post #14, then run the purge grub as you have but making sure the commands are correct.

---

### Post by wilee-nilee on 2011-01-03
So I found this boot.ini MS link so that you can compare yours to it and the extra stuff in your XP boot line from the script. It is instructions for editing the boot.ini.
[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

So here are the extra files not needed highlighted hope this is helpful.
Boot files/dirs: **/ubuntu/winboot/menu.lst** /boot.ini /ntldr
/NTDETECT.COM [B]/ubuntu/winboot/wubildr.mbr
/ubuntu/winboot/wubildr[/B]

I guess if it was me I would run a search for files with ubuntu, wubi, menu.list, wubildr. Winboot is probably good to look for but look closely at any that you find. If you see that any of these are in the boot.ini you just want a comparison with the MS link to see what is supposed to be there.

---

### Post by oldfred on 2011-01-03
I am just about out of ideas, but have a test that I would like you to try.

Your windows install looks like it is about 100GB, and your Ubuntu install is about 200GB. I would like you to use gparted in the liveCD to shrink the Ubuntu install to about 20GB. 

For now just leave the remaining space unallocated. Since you are probably only using 3 or 4GB of the install, the shrink should not take very long. If this happens to work we can make the space a /home partition or a data partition or  a shared NTFS data partiton or some of each. 

You may have to reinstall grub but should not have to after a shrink.

---

### Post by inertself on 2011-01-03
OK, have unknown file system now.  I also moved the partition to the end of the drive, so the free space is in the middle.  Hope this didn't mess anything up, but I am going to re-install grub again and see how it works this time.

---

### Post by inertself on 2011-01-03
Almost did it flawless:

```

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mkdir /mnt/temp
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt/temp
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
root@ubuntu:/# apt-get update
Get:1 http://extras.ubuntu.com maverick Release.gpg [72B]
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en       
Hit http://us.archive.ubuntu.com maverick Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Get:2 http://security.ubuntu.com maverick-security Release.gpg [198B]
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Get:3 http://us.archive.ubuntu.com maverick-updates Release.gpg [198B]
Hit http://extras.ubuntu.com maverick Release  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release                    
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en           
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US        
Get:4 http://security.ubuntu.com maverick-security Release [27.2kB]                        
Hit http://extras.ubuntu.com maverick/main Sources                                                 
Get:5 http://us.archive.ubuntu.com maverick-updates Release [31.4kB]         
Hit http://extras.ubuntu.com maverick/main i386 Packages                             
Hit http://us.archive.ubuntu.com maverick/main Sources                               
Hit http://us.archive.ubuntu.com maverick/restricted Sources
Hit http://us.archive.ubuntu.com maverick/universe Sources
Hit http://us.archive.ubuntu.com maverick/multiverse Sources
Hit http://us.archive.ubuntu.com maverick/main i386 Packages
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages
Get:6 http://security.ubuntu.com maverick-security/main Sources [16.9kB]
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages  
Get:7 http://us.archive.ubuntu.com maverick-updates/main Sources [69.2kB]
Get:8 http://security.ubuntu.com maverick-security/restricted Sources [14B]
Get:9 http://security.ubuntu.com maverick-security/universe Sources [6,300B]
Get:10 http://security.ubuntu.com maverick-security/multiverse Sources [649B]
Get:11 http://security.ubuntu.com maverick-security/main i386 Packages [54.2kB]
Get:12 http://us.archive.ubuntu.com maverick-updates/restricted Sources [14B]          
Get:13 http://us.archive.ubuntu.com maverick-updates/universe Sources [21.4kB]
Get:14 http://us.archive.ubuntu.com maverick-updates/multiverse Sources [1,068B]       
Get:15 http://us.archive.ubuntu.com maverick-updates/main i386 Packages [189kB]   
Get:16 http://security.ubuntu.com maverick-security/restricted i386 Packages [14B]
Get:17 http://security.ubuntu.com maverick-security/universe i386 Packages [22.7kB]
Get:18 http://security.ubuntu.com maverick-security/multiverse i386 Packages [1,655B]  
Get:19 http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages [14B]
Get:20 http://us.archive.ubuntu.com maverick-updates/universe i386 Packages [71.1kB]
Get:21 http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages [2,522B]
Fetched 516kB in 2s (234kB/s)                            
Reading package lists... Done
root@ubuntu:/# apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
The following packages will be REMOVED:
  grub-common* grub-pc*
0 upgraded, 0 newly installed, 2 to remove and 202 not upgraded.
After this operation, 5,804kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 119498 files and directories currently installed.)
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
root@ubuntu:/# apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following NEW packages will be installed:
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 202 not upgraded.
Need to get 0B/2,204kB of archives.
After this operation, 5,804kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 119219 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.98+20100804-5ubuntu3_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.98+20100804-5ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
Setting up grub-common (1.98+20100804-5ubuntu3) ...
Setting up grub-pc (1.98+20100804-5ubuntu3) ...

Creating config file /etc/default/grub with new version
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ for i in /dev/pts /dev /proc /sys /boot / : do sudo umount /mnt/temp$i ; done
bash: syntax error near unexpected token `done'
ubuntu@ubuntu:~$ for i in /dev/pts /dev /proc /sys /boot / : do sudo umount /mnt/temp$i ;  done
bash: syntax error near unexpected token `done'
ubuntu@ubuntu:~$ for i in /dev/pts /dev /proc /sys /boot / ; do sudo umount /mnt/temp$i ;  done
umount: /mnt/temp/boot: not mounted
ubuntu@ubuntu:~$ 


```

No go, still the same as when I first re-partitioned.  error: unknown filesystem.  Grub rescue prompt

When I type ls in the rescue prompt it still says (hd0) (hd0,msdos2) (hd0,msdos1)

---

### Post by wilee-nilee on 2011-01-03
> **inertself said:**
> OK, have unknown file system now.  I also moved the partition to the end of the drive, so the free space is in the middle.  Hope this didn't mess anything up, but I am going to re-install grub again and see how it works this time.

Actually oldfred was looking for you to shrink it to the front to the left. There are limitations to some bios of 137 gigs, at least that what I think they were doing.

Since oldfred didn't comment on the commands it is probably okay the commands.

Just out of curiosity is this a western digital HD?

If your shrunk the front of Ubuntu to the right you would have to reinstall grub to the mbr probably.

---

### Post by inertself on 2011-01-04
I'm not sure, I got it over a year ago and it was the biggest hard drive I could find for this older dell.  I'm going to just resize the windows partition and rewrite the mbr to make it useable and ditch ubuntu for now.  I really need this computer to just work and it was probably not smart making it into a dual boot machine in the first place.

---

### Post by wilee-nilee on 2011-01-04
> **inertself said:**
> I'm not sure, I got it over a year ago and it was the biggest hard drive I could find for this older dell.  I'm going to just resize the windows partition and rewrite the mbr to make it useable and ditch ubuntu for now.  I really need this computer to just work and it was probably not smart making it into a dual boot machine in the first place.

I understand, it may be as simple though as having the Ubuntu below the 137 gig mark in its size ending and the rest as home for it and or a shared ntfs. This is just future information, but the old in the dell mention makes me suspect a bios limitation. There might be a switch in the bios for more I don't know really.

---

### Post by inertself on 2011-01-04
I really like ubuntu and open source.  Maybe once I upgrade to a better computer I can mess with this one some more.  Thanks guys for your help, it's working ok in windows now.  Gparted wouldn't let me use the whole drive for the single partition, but it's close (298Gb).   Not sure where the other 22 gigs went..  but anyway it's working fine in windows for now.

Thanks guys for your help, really great community here.  I will be sure to chime in from time to time as I still have dual boot on my HP laptop and most of my friends computers as well.  As far as the wubi should I be worried about that still?  

Again, you guys are the best =D>, if I had more patience I would get this but now is not the time.

Tobey

---

### Post by inertself on 2011-01-04
> **wilee-nilee said:**
> I understand, it may be as simple though as having the Ubuntu below the 137 gig mark in its size ending and the rest as home for it and or a shared ntfs. This is just future information, but the old in the dell mention makes me suspect a bios limitation. There might be a switch in the bios for more I don't know really.


OK I'll keep this in mind for future reference, seems to me it probably is a western digtital hard drive.  I got it from fleabay and looked at a new listing with the same exact title and it doesn't have a brand name so I'm not sure without pulling it and taking a look.  I really just need this to feed my CNC machine text files with G-code, and my CNC machine is 20 years old.  I just picked up an ancient laptop that has 97mb of ram and a 4 gig hard drive, and I'm thinking I can use that to feed the text files and then try to get the CAD software licenses transferred to a better machine, but thats something for later.  Anyway I'm back up and running for now and it has the old com port that I need so I'm happy :)

---

### Post by wilee-nilee on 2011-01-04
> **inertself said:**
> I really like ubuntu and open source.  Maybe once I upgrade to a better computer I can mess with this one some more.  Thanks guys for your help, it's working ok in windows now.  Gparted wouldn't let me use the whole drive for the single partition, but it's close (298Gb).   Not sure where the other 22 gigs went..  but anyway it's working fine in windows for now.

Thanks guys for your help, really great community here.  I will be sure to chime in from time to time as I still have dual boot on my HP laptop and most of my friends computers as well.  As far as the wubi should I be worried about that still?  

Again, you guys are the best =D>, if I had more patience I would get this but now is not the time.

Tobey

The HD is listed as 320gigs but in the real world it is 298. The way manufacturers count the size and an actual use amount is different, my 320 external is only 298.

Seems like a scam but its not, its legal.

You showed a lot of patience here but it does get frustrating I know.:)

---

### Post by wilee-nilee on 2011-01-04
> **inertself said:**
> OK I'll keep this in mind for future reference, seems to me it probably is a western digtital hard drive.  I got it from fleabay and looked at a new listing with the same exact title and it doesn't have a brand name so I'm not sure without pulling it and taking a look.  I really just need this to feed my CNC machine text files with G-code, and my CNC machine is 20 years old.  I just picked up an ancient laptop that has 97mb of ram and a 4 gig hard drive, and I'm thinking I can use that to feed the text files and then try to get the CAD software licenses transferred to a better machine, but thats something for later.  Anyway I'm back up and running for now and it has the old com port that I need so I'm happy :)

I just noticed this post regarding the western digital. Some came with firmware built in called smartware, I was helping another earlier today on the IRC and we did a fresh install partitioned correctly, just 10.10 every time previously 4 installs the 5th was the one I helped with would boot in no problem once then throw up errors that are mentioned on a sourceforge wiki. None of the fixes worked. So after looking at the web a bit it seems that in some models that have this firmware, you have to upgrade the firmware then hide it from a MS set up, some program I'm not sure.

---

### Post by oldfred on 2011-01-04
No, the test was to try to get it inside the 137GB and perhaps a smaller root partition. We have seen a few with very large root partitions 1 or 2TB have issues, but this is smaller.

I never move a partition's start unless I can do nothing else. I will shrink or expand, or even delete & recreate. Moving it right will almost alway force you to do a grub reinstall.

---

### Post by inertself on 2011-01-07
Oh I gotcha.  It worked fine with 9.10, maybe this is something new?  Sorry for the slow response.  Again, you guys are the bomb.

---

### Post by inertself on 2011-01-07
> **wilee-nilee said:**
> The HD is listed as 320gigs but in the real world it is 298. The way manufacturers count the size and an actual use amount is different, my 320 external is only 298.

Seems like a scam but its not, its legal.

You showed a lot of patience here but it does get frustrating I know.:)

This must be the difference between a bit and a byte?  or something along those lines.

---

### Post by hawkmage on 2011-01-07
It has nothing to do with bits and bytes.  Drive manufactures conceder a gigabyte to be 1,000,000,000 bytes and not (1024 * 1024 * 1024) 1,073,741,824 bytes like the rest of us.  (320 * 1,000,000,000) / 1,073,741,824 = 298.023224

---

### Post by BigMoose on 2011-01-19
Hi All,

I know I am coming late to this party, but since I have a similar issue and the OP no longer is using it I would like to hijack this thread a bit. I don't have as much knowledge about Linux though so be gentle. I have a different thread that I have tried things with but am willing to see if you guys can help. Here it is:

[http://ubuntuforums.org/showthread.php?t=1669321&page=4](http://ubuntuforums.org/showthread.php?t=1669321&page=4)

---

### Post by BigMoose on 2011-01-19
Hi All,

I know I am coming late to this party, but since I have a similar issue and the OP no longer is using it I would like to hijack this thread a bit. I don't have as much knowledge about Linux though so be gentle. I have a different thread that I have tried things with but am willing to see if you guys can help. Here it is:

[http://ubuntuforums.org/showthread.php?t=1669321&page=4](http://ubuntuforums.org/showthread.php?t=1669321&page=4)

---

### Post by BigMoose on 2011-01-19
Hi All,

I know I am coming late to this party, but since I have a similar issue and the OP no longer is using it I would like to hijack this thread a bit. I don't have as much knowledge about Linux though so be gentle. I have a different thread that I have tried things with but am willing to see if you guys can help. Here it is:

[http://ubuntuforums.org/showthread.php?t=1669321&page=4](http://ubuntuforums.org/showthread.php?t=1669321&page=4)

---

### Post by BigMoose on 2011-01-19
Hi All,

I know I am coming late to this party, but since I have a similar issue and the OP no longer is using it I would like to hijack this thread a bit. I don't have as much knowledge about Linux though so be gentle. I have a different thread that I have tried things with but am willing to see if you guys can help. Here it is:

[http://ubuntuforums.org/showthread.php?t=1669321&page=4](http://ubuntuforums.org/showthread.php?t=1669321&page=4)

---

