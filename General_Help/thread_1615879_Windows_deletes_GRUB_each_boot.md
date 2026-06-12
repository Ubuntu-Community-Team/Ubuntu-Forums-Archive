---
title: "Windows deletes GRUB each boot"
date: 2010-11-07
forum: General Help
---

### Post by dwigyit on 2010-11-07
Each time I boot into Windows 7 on my dual-boot setup (the other OS being Ubuntu Maverick), the computer is no longer able to boot. I can use Windows fine that once, but after shutting down and restarting it simply loops during boot in the pattern OEM screen, power off, power on, OEM screen, power off, power on... you get the idea.

I have read that this is due to Windows (or a program inside Windows) "fixing" the Master boot record (MBR) each time it loads - and in doing so, deleting GRUB. Thing is: on my other laptop the exact same dual-boot setup works fine. My problem laptop is a Samsung R780. My guess is that it's a specific program on my laptop, as oppose to Windows in general, which is doing it, so I was hoping that you could help me either identify the problem program or secure the MBR against Windows writing to it (if that is possible).

I can, of course, fix GRUB each individual time it is destroyed by installing it again using the Ubuntu live CD, but this is obviously not a permenant solution as, upon the next boot of Windows, it is destroyed again.

I appreciate that this problem is one with Windows, not Ubuntu - but I doubt that the Windows forum will have many people using GRUB who can help me.

---

### Post by rohan_m on 2010-11-07
Are you using Wubi? If so, are you selecting the first option when the GRUB boot menu appears? (after the dual booting menu appears)

---

### Post by dwigyit on 2010-11-07
No, there's no WUBI, it's a true dual-boot. 

The point is that the boot menu never appears because the MBR is disrupted - GRUB never loads properly, it just crashes and reboots after the OEM screen. The only way to solve it that I can see would be to either find and remove the offending Windows application (which I what I am asking for help with), or to put GRUB onto another device (such as a USB stick) which would have to be in my computer permenantly. I'd really rather choose the former - fix the problem instead of just working around it. And I know that the problem can be fixed because my other Windows 7 laptop works perfectly and I can boot to either Windows or Ubuntu with no trouble.

---

### Post by sikander3786 on 2010-11-07
Please reinstall Grub one more time onto the MBR of your internal HDD and post the output of bootinfoscript. It would be interesting to see what is happening. Script and instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

If you want to go the other way, EasyBCD is a Windows based bootloader which can boot many OS including Ubuntu.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

Another choice may be the Super Grub disc. I think it also can be run from the USB drive(??).

And you can also install Grub on another drive but it would not be the perfect solution.

---

### Post by Quackers on 2010-11-07
Also check that your anti-virus isn't checking for root-kits in the MBR. That can quarantine some of grubs MBR entry.

---

### Post by dwigyit on 2010-11-07
I'll give EasyBCD a go, thankyou :)

But before I can do that, I need to get Windows to output to the working HDMI screen as opposed to the broken laptop one which it uses at the moment. The FN+F4 key doesn't do it - has anyone got any ideas? It did used to switch over automatically one a HDMI cable was plugged in.

Thing is - I'm not even sure if Windows is reaching the logon screen, as it never plays the sound and the image (or what I can see of it on the broken screen) never changes when I press enter and type my password.

As for the boot script - I've read the page and don't fully understand how to use it.

---

### Post by sikander3786 on 2010-11-07
Not sure about switching monitor on Windows 7. Some one else needs to answer that.

For bootinfoscript, simply download it to your desktop from a Live CD and in terminal type,

```
sudo bash ~/Desktop/boot_info_script*.sh
```

Just replace * with the appropriate file name which you will see when you download it.

Result.txt will be generated on your desktop, copy/paste from that and post it here.

As Quackers suggested, it might well be the antivirus program but you need to boot into Windows to check that.

---

### Post by wilee-nilee on 2010-11-07
easybcd is a okay way to go, but you seem to be the only one with this model having a problem, so I don't think another bootloader is going to fix this.
[http://www.funzt.info/?p=590](http://www.funzt.info/?p=590)

---

### Post by dwigyit on 2010-11-07
Perhaps it isn't OEM software then, but I don't know of any software on my computer which I have installed which would have any reason to be playing around with the MBR. 

There's a chance that I may have installed Avast!, but after looking in Program Files (using Ubuntu), there's no Avast folder - so I guess it isn't that. I'd have no issue with just reinstalling Windows if it came to it, but the laptop wasn't supplied with a recovery CD. Would my product key on the sticker on my laptop work with any Windows 7 disc?

And I uploaded the results of the boot script - does it have to be run immediately after reinstalling GRUB or can it be run anytime - because I have booted Ubuntu twice since reinstalling GRUB when I made this version.

---

### Post by sikander3786 on 2010-11-07
**dwigyit's** Results.txt

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    31,459,327    31,457,280  27 Hidden HPFS/NTFS
/dev/sda2    *     31,459,328    31,664,127       204,800  82 Linux swap / Solaris
/dev/sda3          31,664,128   664,883,199   633,219,072   7 HPFS/NTFS
/dev/sda4         664,883,200   976,771,071   311,887,872  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7E804FBB804F7923                       ntfs       RECOVERY                      
/dev/sda2        dfbf595c-a670-4469-9cf6-2ef72aa7c814   swap                                     
/dev/sda3        26AC520DAC51D83F                       ntfs                                     
/dev/sda4        1caaa02f-f16c-4844-be26-ef4b1d756f64   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /media/26AC520DAC51D83F  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 1caaa02f-f16c-4844-be26-ef4b1d756f64
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 1caaa02f-f16c-4844-be26-ef4b1d756f64
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
play 480 440 1
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 1caaa02f-f16c-4844-be26-ef4b1d756f64
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=1caaa02f-f16c-4844-be26-ef4b1d756f64 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 1caaa02f-f16c-4844-be26-ef4b1d756f64
    echo    'Loading Linux 2.6.35-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=1caaa02f-f16c-4844-be26-ef4b1d756f64 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 1caaa02f-f16c-4844-be26-ef4b1d756f64
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 1caaa02f-f16c-4844-be26-ef4b1d756f64
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7e804fbb804f7923
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

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=1caaa02f-f16c-4844-be26-ef4b1d756f64 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=dfbf595c-a670-4469-9cf6-2ef72aa7c814 none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


 422.1GB: boot/grub/core.img
 437.3GB: boot/grub/grub.cfg
 341.3GB: boot/initrd.img-2.6.35-22-generic-pae
 422.1GB: boot/vmlinuz-2.6.35-22-generic-pae
 341.3GB: initrd.img
 422.1GB: vmlinuz
```


Swap as a primary partition and before Windows partition, doesn't sound good at all.

And boot flag on sda2 which is a Linux partition doesn't sound good either.

I would wait for wilee-nilee's/some other suggestions on this.

---

### Post by Quackers on 2010-11-07
Your boot script in code tags 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    31,459,327    31,457,280  27 Hidden HPFS/NTFS
/dev/sda2    *     31,459,328    31,664,127       204,800  82 Linux swap / Solaris
/dev/sda3          31,664,128   664,883,199   633,219,072   7 HPFS/NTFS
/dev/sda4         664,883,200   976,771,071   311,887,872  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7E804FBB804F7923                       ntfs       RECOVERY                      
/dev/sda2        dfbf595c-a670-4469-9cf6-2ef72aa7c814   swap                                     
/dev/sda3        26AC520DAC51D83F                       ntfs                                     
/dev/sda4        1caaa02f-f16c-4844-be26-ef4b1d756f64   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /media/26AC520DAC51D83F  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 1caaa02f-f16c-4844-be26-ef4b1d756f64
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 1caaa02f-f16c-4844-be26-ef4b1d756f64
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
play 480 440 1
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 1caaa02f-f16c-4844-be26-ef4b1d756f64
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=1caaa02f-f16c-4844-be26-ef4b1d756f64 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 1caaa02f-f16c-4844-be26-ef4b1d756f64
	echo	'Loading Linux 2.6.35-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=1caaa02f-f16c-4844-be26-ef4b1d756f64 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 1caaa02f-f16c-4844-be26-ef4b1d756f64
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 1caaa02f-f16c-4844-be26-ef4b1d756f64
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7e804fbb804f7923
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

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=1caaa02f-f16c-4844-be26-ef4b1d756f64 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=dfbf595c-a670-4469-9cf6-2ef72aa7c814 none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


 422.1GB: boot/grub/core.img
 437.3GB: boot/grub/grub.cfg
 341.3GB: boot/initrd.img-2.6.35-22-generic-pae
 422.1GB: boot/vmlinuz-2.6.35-22-generic-pae
 341.3GB: initrd.img
 422.1GB: vmlinuz
```

According to that your boot flag is set on sda2, which is a Linux swap partition. Linux doesn't use boot flags, Windows does. Your first Windows boot partition is sda1 and this is where the boot flag would normally be. I don't know why Windows is booting, as far as I can see, it shouldn't be booting at all.

---

### Post by dwigyit on 2010-11-07
sda1 isn't Windows, sda3 is. sda1 is recovery according to Disk Utility.

Does this mean that it will boot fine until Windows is loaded in GRUB? If so, it actually explains a lot - from why there's no logon sound to why the HDMI output isn't activating automatically to why the bottom-right corner of my screen (which actually still works) doesn't change colour after a fair boot time in Windows (unfortunatly I can't see any errors because of the smashed screen). Can I change boot flags somehow to fix the Windows boot?

Does this help at all with the problem of GRUB being deleted upon Windows boot, or will I have to find a way to use the newly discovered recovery partition to reinstall Windows then stick GRUB back on at the end with the live CD?

---

### Post by coffeecat on 2010-11-07
> **dwigyit said:**
> I have read that this is due to Windows (or a program inside Windows) "fixing" the Master boot record (MBR) each time it loads

Could this be your problem?

Link 1: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

Link 2: [http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable]("http://www.chiark.greenend.org.uk/ucgi/%7Ecjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable")

Link 3: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)

---

### Post by Quackers on 2010-11-07
> **dwigyit said:**
> sda1 isn't Windows, sda3 is. sda1 is recovery according to Disk Utility.

Does this mean that it will boot fine until Windows is loaded in GRUB? If so, it actually explains a lot - from why there's no logon sound to why the HDMI output isn't activating automatically to why the bottom-right corner of my screen (which actually still works) doesn't change colour after a fair boot time in Windows (unfortunatly I can't see any errors because of the smashed screen). Can I change boot flags somehow to fix the Windows boot?

Does this help at all with the problem of GRUB being deleted upon Windows boot?

sda1 may well be your recovery partition, but Windows 7 likes to use 2 partitions nowadys and sda1 contains the first 2 Windows boot files and would normally be marked as active (with the boot flag). It is possible to change the boot flag position with GParted and it may be worth a try. But have a look at coffeecat's links first.
Nice find coffeecat!

---

### Post by wilee-nilee on 2010-11-07
We need to see the latest script as of now, but as the other two mention the bootflag should be on sda1. This can be done with gparted just right click on sad1 with it unmounted and all MS unmounted and the manage flags and tick boot for that partition.

The swap may be a problem hard to say here, for me but the way it is all arranged is unusual.

---

### Post by dwigyit on 2010-11-07
> Could this be your problem?

Link 1: [http://sourceforge.net/apps/mediawik..._Writes_To_MBR](http://sourceforge.net/apps/mediawik..._Writes_To_MBR)

Link 2: [http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable)

Link 3: [https://bugs.launchpad.net/ubuntu/+s...b2/+bug/441941](https://bugs.launchpad.net/ubuntu/+s...b2/+bug/441941) I've read the SourceForge one already, which was the inspiration for what you quoted. I tried solution 3 but got errors, and it's the same thing which was discouraged by wilee-nilee. I don't fully understand the method used in solution 1 so I thought it would be best to ask here. Solution 2, they said, is unlikely to work and it would mean I can't use the features of GRUB 2, and solution 4 requires another HDD or a permenant memory stick, which I don't have.

---

### Post by dwigyit on 2010-11-07
Now that I think about it; if Windows wasn't booting properly, how could it be disabling GRUB?

And might it be a good idea to just buy an external HDD, back up everything, and reinstall Windows from the recovery partition and then reinstall Ubuntu? That would fix all the partition system messups, wouldn't it?

---

### Post by efflandt on 2010-11-07
Not sure what type of computer you have mfr/model, but I had the same issue with a Dell.  In any case, some Windows programs write to a part of the mbr that they "think" is not used, and that steps on grub2 which is larger than DOS/Win mbr.

So in my case I installed grub on sda4 which is the primary partition that I am using for 64-bit 10.10. That works fine regardless of any bitching and moaning grub2 does if you try to install it there.

From live system on install CD (or USB):
[FONT=monospace]
[/FONT]```
sudo mount /dev/sda4 /mnt

sudo grub-install --force --root-directory=/mnt/ /dev/sda4
(if it complains, ignore that)
```Then use a Win7 system disk to restore the mbr with: **bootrec /FixMbr**

Although, if sda2 was something important for Windows, you might see if the Windows DVD can actually fix it so Windows can boot on its own at this point.

Then boot the install CD live, use gparted to **mark sda4 as the boot partition**.  Reboot to Ubuntu and run: **sudo update-grub**

Works for me (without any swap).  Although, the boot info script does not properly interpret where core.img is in the first part when grub2 is on a partition.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda4 and 
                       looks at sector 1879003944 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              81,920    24,743,935    24,662,016   7 HPFS/NTFS
/dev/sda3          24,743,936 1,748,717,567 1,723,973,632   7 HPFS/NTFS
/dev/sda4    *  1,748,717,568 1,953,523,711   204,806,144  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        EED2-7775                              vfat                                     
/dev/sda2        E6CAD622CAD5EF35                       ntfs       RECOVERY                      
/dev/sda3        6440DA0C40D9E538                       ntfs       OS                            
/dev/sda4        b0236a24-e5cf-4942-9e65-0b427ca1267a   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set default="${saved_entry}"
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
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set b0236a24-e5cf-4942-9e65-0b427ca1267a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set b0236a24-e5cf-4942-9e65-0b427ca1267a
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
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set b0236a24-e5cf-4942-9e65-0b427ca1267a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b0236a24-e5cf-4942-9e65-0b427ca1267a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set b0236a24-e5cf-4942-9e65-0b427ca1267a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b0236a24-e5cf-4942-9e65-0b427ca1267a ro single 
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
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set b0236a24-e5cf-4942-9e65-0b427ca1267a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set b0236a24-e5cf-4942-9e65-0b427ca1267a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    savedefault
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set e6cad622cad5ef35
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

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=b0236a24-e5cf-4942-9e65-0b427ca1267a /               ext4    errors=remount-ro 0       1

=================== sda4: Location of files loaded by Grub: ===================


 962.0GB: boot/grub/core.img
 953.7GB: boot/grub/grub.cfg
 897.8GB: boot/initrd.img-2.6.35-22-generic
 896.4GB: boot/vmlinuz-2.6.35-22-generic
 897.8GB: initrd.img
 896.4GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde
```

---

### Post by dwigyit on 2010-11-07
I can't use Win7 recovery disks - they don't use dual-screen by default as the Ubuntu ones do, and they don't respond to keyboard commands to change monitor. This means I can't actually see anything as my laptop main screen is smashed. :D

---

### Post by dwigyit on 2010-11-08
If I just reinstall a fresh copy of Windows over the whole disk and then shrink the partition and stick Linux and some swap space in the rest of it, will that make a better partition arrangement? And advice on which order to put things etc?

---

### Post by sikander3786 on 2010-11-08
> **dwigyit said:**
> If I just reinstall a fresh copy of Windows over the whole disk and then shrink the partition and stick Linux and some swap space in the rest of it, will that make a better partition arrangement? And advice on which order to put things etc?
In my opinion, instead of shrinking the Windows partition after a fresh install, it would be just better to create the necessary partitions and then install Windows. If you've got no important data, you can just delete all the partitions from Windows installer, keep the recovery partition if you want to.

Create the C: partition for Windows (whichever size you can afford). Create a data partition formatted NTFS if you want to share data between Windows and Ubuntu (optional) and leave all other space unallocated. Don't create a partition in that space and later from Ubuntu installer, you can just choose "Use the largest continuous free space" and it will automatically create the necessary partition i.e, '/' and swap partitions in the correct order.

So my partition table would look something like

[primary]
sda1: Recovery partition
sda2: Windows partition
sda3: Data partition (NTFS)
[/primary]

[extended/logical]
sda5: Ubuntu '/' partition
sda6: Swap partition
[/extended/logical]

If you want to, you can have a separate /home partition but you'll need to choose manual partitioning from Ubuntu installer and do the partitioning yourself.

---

### Post by dwigyit on 2010-11-09
The windows installer didn't seem to give me any options for making partitions smaller than the whole free space, so I just installed it over everything except for recovery. I will try to reproduce the layout you gave me tomorrow with the Windows partition editor - assuming there is one. I seem to remember it vaguely. Then I'll install Ubuntu. Will it work?

---

### Post by wilee-nilee on 2010-11-09
> **dwigyit said:**
> The windows installer didn't seem to give me any options for making partitions smaller than the whole free space, so I just installed it over everything except for recovery. I will try to reproduce the layout you gave me tomorrow with the Windows partition editor - assuming there is one. I seem to remember it vaguely. Then I'll install Ubuntu. Will it work?

If you are just going to install Ubuntu or another Linux OS, use the W7 disk manager to shrink W7, **but not for any Linux partitions.**

You would use gparted on the live install disc to build your partitions. Make sure you make a extended partition to begin with then put the others inside for the Linux install.

---

