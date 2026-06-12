---
title: "Grub2 not booting Windows"
date: 2010-12-05
forum: General Help
---

### Post by TheRaiderNation on 2010-12-05
So to make things short, here's my situation:
I was having the "no module found" problem, because dell software kept on  messing with the MBR
So I restored the MBR using Windows recovery and deleted the dell software
Re-installed ubuntu 10.10 off the liveCD
~Then I had problems getting GRUB2 boot menu to show at boot, but i fixed that~
Now I'm having the problem where whenever I try to boot into windows 7 through GRUB2 instead of booting windows I just get:
"bootmgr is missing"

Note: I can still boot into Ubunutu 10.10 just fine.

---

### Post by wilee-nilee on 2010-12-05
Was it the dell data safe that you removed? What did you remove?

Also do this, so from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

What has probably happened is you removed a partition that had part of the boot in it, this is fixable so post the script this will confirm this and other pertinent info.

---

### Post by TheRaiderNation on 2010-12-05
Yea, I removed all the Datasafe software. And okay, I'll do that and get back to you

---

### Post by wilee-nilee on 2010-12-05
> **TheRaiderNation said:**
> Yea, I removed all the Datasafe software. And okay, I'll do that and get back to you

cool the script will be the key.

---

### Post by TheRaiderNation on 2010-12-05
Here's the result of the boot info script:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   584,178,351   553,376,432   7 HPFS/NTFS
/dev/sda4         584,179,712   625,141,759    40,962,048  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        143EF1893EF163E0                       ntfs       RECOVERY                      
/dev/sda3        AC16F4E916F4B584                       ntfs       OS                            
/dev/sda4        f16d0dcc-d0f2-41aa-92b2-73ec9d76c2ec   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro,commit=600)


=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=================== sda3: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

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
search --no-floppy --fs-uuid --set f16d0dcc-d0f2-41aa-92b2-73ec9d76c2ec
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set f16d0dcc-d0f2-41aa-92b2-73ec9d76c2ec
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
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set f16d0dcc-d0f2-41aa-92b2-73ec9d76c2ec
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f16d0dcc-d0f2-41aa-92b2-73ec9d76c2ec ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set f16d0dcc-d0f2-41aa-92b2-73ec9d76c2ec
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f16d0dcc-d0f2-41aa-92b2-73ec9d76c2ec ro single 
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
    search --no-floppy --fs-uuid --set f16d0dcc-d0f2-41aa-92b2-73ec9d76c2ec
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set f16d0dcc-d0f2-41aa-92b2-73ec9d76c2ec
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Microsoft Windows 7" {
insmod ntfs
set root=(hd0,3)
search --no-floppy --fs-uuid --set 76484BEE484BABA5
drivemap -s (hd0) ${root}
chainloader +1
}
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
UUID=f16d0dcc-d0f2-41aa-92b2-73ec9d76c2ec /               ext4    errors=remount-ro 0       1

=================== sda4: Location of files loaded by Grub: ===================


 312.1GB: boot/grub/core.img
 305.9GB: boot/grub/grub.cfg
 306.4GB: boot/initrd.img-2.6.35-22-generic
 312.1GB: boot/vmlinuz-2.6.35-22-generic
 306.4GB: initrd.img
 312.1GB: vmlinuz
```

---

### Post by wilee-nilee on 2010-12-05
sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD **/boot/grub/core.img**

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe **/boot/grub/core.img**



First you have grub in these windows partitions, the boot partition. You also don't have the boot flag set on sda2 to make it active.

So to clean out grub this link works quite well.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You can use the Ubuntu Live cd and gparted to set the sda2 partition with the boot flag, just right click it and manage flags. Personally just for caution I turn off the swap partition with any changes it is a right click as well.

I have to look through the script some more but these are deal breakers but fixable.

---

### Post by TheRaiderNation on 2010-12-05
Alright, thanks

Also could you elaborate on:
> You can use the Ubuntu Live cd and gparted to set the sda2 partition  with the boot flag, just right click it and manage flags. Personally  just for caution I turn off the swap partition with any changes it is a  right click as well.
I' a  little lost on what you meant by that

---

### Post by wilee-nilee on 2010-12-05
> **TheRaiderNation said:**
> Alright, thanks

Also could you elaborate on:

I' a  little lost on what you meant by that

No problem here is a screen shot. So I right clicked on the sda1 W7 partition and the pointer is at where want to open (manage flags) just click the next open window as boot you will see it when you get there.
[ATTACH]177535[/ATTACH]

I would do this first before the testdisk, to get grub out of the NTFS partitions

This can also be fixed with a install or recovery disc is this vista?

---

### Post by TheRaiderNation on 2010-12-05
Alright, so I just enabled the bootflag on my win7 os partition, should I try to boot into windows 7 now? Or still go through testdisk before I try to boot into windows?

---

### Post by wilee-nilee on 2010-12-05
> **TheRaiderNation said:**
> Alright, so I just enabled the bootflag on my win7 os partition, should I try to boot into windows 7 now? Or still go through testdisk before I try to boot into windows?

Grub will have to be cleaned out windows wont boot I'm quite sure.

Even after getting it cleaned out I suspect we will have to reload the grub bootlaoder to the mbr if the history of this dell data safe history is the same.

So run the testdisk follow the instructions, you have to have the universal repository open to get downloaded to the live cd I believe. In software sources I believe there is a click for opening this repo. You may have to right click the main menu then edit then admin to click on the software sources to see it in the same admin where gparted would be.

You can see if it boots correctly after the cleanup, if it doesn't just run the script again so we can see whats been cleaned out and where to go from that point.

Generally when we have given this link and grub was in two partitions like yours is it gets cleaned up, but as I said there are other ways but testdisk seems to work quite well. You might notice that the author of the script and this link are the same.

---

### Post by TheRaiderNation on 2010-12-05
Okay, so I got testdisk, and was following the instructions got to screen six but there was no option for BackupBS

So i'm guessing I'm going to have to use win7 to recover the MBR, then boot from Ubuntu live CD and reinstall grub/grub2 to sda3 (which is my windows7 OS partition)

---

### Post by wilee-nilee on 2010-12-05
> **TheRaiderNation said:**
> Okay, so I got testdisk, and was following the instructions got to screen six but there was no option for BackupBS

So i'm guessing I'm going to have to use win7 to recover the MBR, then boot from Ubuntu live CD and **reinstall grub/grub2 to sda3** (which is my windows7 OS partition)

Okay so I have seen this no BackupBS posted when people have used testdisk, but like maybe 1 out a 100. So where are you at now? and post another bootscript.

Also your description highlighted is backwards we are trying to remove it, this might just be fast typing; lets make sure we are on the same page. Grub should only show in two place the mbr and the Linux install partition.

It is easy for a word or sentence to be misinterpreted so I'm just trying to make sure we are together here.;)

---

### Post by TheRaiderNation on 2010-12-05
Ah, okay, so I want to move Grub to Linux, and take it out of Win7, I guess I was in the mindset that I needed to install Grub to the Win partition to override the Win bootloader, but I do that when grub installs to the MBR, right?

And here's the new results.txt:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3    *     30,801,920   584,178,351   553,376,432   7 HPFS/NTFS
/dev/sda4         584,179,712   625,141,759    40,962,048  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        143EF1893EF163E0                       ntfs       RECOVERY                      
/dev/sda3        AC16F4E916F4B584                       ntfs       OS                            
/dev/sda4        f16d0dcc-d0f2-41aa-92b2-73ec9d76c2ec   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro,commit=0)


=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=================== sda3: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

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
search --no-floppy --fs-uuid --set f16d0dcc-d0f2-41aa-92b2-73ec9d76c2ec
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set f16d0dcc-d0f2-41aa-92b2-73ec9d76c2ec
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
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set f16d0dcc-d0f2-41aa-92b2-73ec9d76c2ec
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f16d0dcc-d0f2-41aa-92b2-73ec9d76c2ec ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set f16d0dcc-d0f2-41aa-92b2-73ec9d76c2ec
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f16d0dcc-d0f2-41aa-92b2-73ec9d76c2ec ro single 
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
    search --no-floppy --fs-uuid --set f16d0dcc-d0f2-41aa-92b2-73ec9d76c2ec
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set f16d0dcc-d0f2-41aa-92b2-73ec9d76c2ec
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Microsoft Windows 7" {
insmod ntfs
set root=(hd0,3)
search --no-floppy --fs-uuid --set 76484BEE484BABA5
drivemap -s (hd0) ${root}
chainloader +1
}
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
UUID=f16d0dcc-d0f2-41aa-92b2-73ec9d76c2ec /               ext4    errors=remount-ro 0       1

=================== sda4: Location of files loaded by Grub: ===================


 312.1GB: boot/grub/core.img
 305.9GB: boot/grub/grub.cfg
 306.4GB: boot/initrd.img-2.6.35-22-generic
 312.1GB: boot/vmlinuz-2.6.35-22-generic
 306.4GB: initrd.img
 312.1GB: vmlinuz
```

---

### Post by wilee-nilee on 2010-12-05
You have the boot flag on sda3 it should be sda2, set it to sda2 and try testdisk again.

I just ordered a pizza and have to go get it so I may be gone for a 1/2 hour or so so hold on just try this again with the boot flag on the correct partition sda2.

The booting partition will always have these two files at the beginning
Boot files/dirs:    /bootmgr /Boot/BCD=this is in sda2

---

### Post by TheRaiderNation on 2010-12-05
> **wilee-nilee said:**
> You have the boot flag on sda3 it should be sda2, set it to sda2 and try testdisk again.

I just ordered a pizza and have to go get it so I may be gone for a 1/2 hour or so so hold on just try this again with the boot flag on the correct partition sda2.

The booting partition will always have these two files at the beginning
Boot files/dirs:    /bootmgr /Boot/BCD=this is in sda2

Okay, that's fine, appreciate all the help so far, so take your time lol

Anyways, sda2 is my recovery partition, if Grub should be on linux, Shouldn't the boot flag be on sda4 (Ubuntu's partition)? But I'll still give sda2 a shot with testdisk

---

### Post by wilee-nilee on 2010-12-05
> **TheRaiderNation said:**
> Okay, that's fine, appreciate all the help so far, so take your time lol

Anyways, sda2 is my recovery partition, if Grub should be on linux, Shouldn't the boot flag be on sda4 (Ubuntu's partition)? But I'll still give sda2 a shot with testdisk

There may have been the same /bootmgr /Boot/BCD in the sda1. It seems counterintuitive but with sda1 being a firmware dell partition,what we have is that it is doing the voodoo that it does to have that sda2 boot the main os=sda3.

Part of the problems for us is none of us really knows a specific manufacturers schema's, and you did a lot before posting including adding grub to the NTFS=sda2, sda3 partitions. were just the cleanup guys like after a hit.

---

### Post by TheRaiderNation on 2010-12-05
Alright so I assigned the boot flag to sda2,tried testdisk, but same result of no backupBS

---

### Post by wilee-nilee on 2010-12-05
c

---

### Post by wilee-nilee on 2010-12-05
I suspect the script is the same but lets see it again. The problem here is that as I mentioned I wonder if sda1 the firmware partition may have been the original boot. Also I would be surprised if the recovery would be triggered now at all it is hard to say.

With a acer netbook I dual installed and the recovery was in grub with the main OS and worked it is a crap shoot when you start adding a different bootloader as far as interrupting the recovery trigger schema as it would be run without the dual boot.

Are you backed up, did you make a system image of the setup to begin with? Do you have a W7 install disc. I'm only asking this just to know it doesn't mean we will have to even use any of these tools but you should have them none the less.

---

### Post by wilee-nilee on 2010-12-05
If we look at the testdisk link it describes that if you don't see backupBS 

From testdisk page
> If the sixth screen did not have a "BackupBS" tab, it usually means that the original and backup boot sector are identical, and you are probably suffering from a different problem. But it could also mean that your backup boot sector is corrupted, in which case you will of to use "fixboot" from a Windows CD to repair the boot sector.

Here is a recovery disc link if you don't have a recovery or install disc we will need to use one or the other to run some commands in the windows booted disc terminal.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

I know this is kind of overwhelming or it can be, but your W7 is still there it is just getting it bootable.

---

### Post by TheRaiderNation on 2010-12-05
sorryfor the reply time, I'm not at home and my only intenrnet acces is from my phone. Yes I do have the win7 reinstall disk, but I don't have an image. So I'm thinking I should just start fresh? Fix the win7 boot with install disc. Then format the linux partition reinstall ubuntu and install grub to the correct parition, the linux one which is sda4 on my hdd

---

### Post by wilee-nilee on 2010-12-05
> **TheRaiderNation said:**
> sorryfor the reply time, I'm not at home and my only intenrnet acces is from my phone. Yes I do have the win7 reinstall disk, but I don't have an image. So I'm thinking I should just start fresh? Fix the win7 boot with install disc. Then format the linux partition reinstall ubuntu and install grub to the correct parition, the linux one which is sda4 on my hdd

We could probably fixit, but if you have nothing to loose, and a straight install disc, we can replace the W7 setup you have and leave Ubuntu there, and reload grub and you would be set.

We could try some commands from booting the disc that at worse just might make it boot to the recovery and recover, but also might just fix it as well, so that it boots the OS correctly.

So What I'm curious about first is that windows disc if it is a recovery that came with the computer or a full install disc. A full install would be about 2.4 gigs in data size.

Or is this a backup set you made?

You also have the activation key correct, or is the install disc or discs a oem set?

Also grub is only installed to the mbr=sda not a partition.

---

### Post by TheRaiderNation on 2010-12-05
No, I don't really have anything to loseon ubuntus partition. And the win7 disc is the disc that was distributed with my laptop it says on the disc "reinstall dvd". I used it to fix the MBR last time it was messed up

---

### Post by wilee-nilee on 2010-12-05
> **TheRaiderNation said:**
> No, I don't really have anything to loseon ubuntus partition. And the win7 disc is the disc that was distributed with my laptop it says on the disc "reinstall dvd". I used it to fix the MBR last time it was messed up

I think that it is just a recovery disc not a install. If so if you had a full image backup you would use it to reload that. Good news is that if it is a recovery you can run some commands and read my last post as far as the risks.

So follow this command set with using the disc, **if it looks like the W7 link (at the bottom of the commands) **that shows the process of getting to the recovery terminal=command line using the booted recovery disc. You can just download and burn the one I posted, if needed.You will see a command just like the one mentioned in the test disk link. We will start with just a couple and see if that get you booted back straight into windows without grub. WE can install grub back no worries there.;)

The instructions and the W7 forum link help if this is new territory for you.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
```
BootRec.exe /fixmbr
``` 
```
BootRec.exe /FixBoot 
```(#updates PBR partition boot)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Your problems are not with Ubuntu and even if you removed it you would still be in the same place. It is the grub being put into the windows partitions that is the problem.


Edit: I guess it would if possible be helpful to know the data size of that reinstall disc. It is unusual for a straight up W7 install disc to be included, when there is a recovery partition. could this disc be for triggering the recovery as well I wonder.

---

### Post by wilee-nilee on 2010-12-05
To tell you the truth you might want to wait until you can just call the help line with the manufacturers to confirm the boot partition, ie is it sda1 and is it missing the some boot files as such as these.
```
 /bootmgr /Boot/BCD
```

Others helpers might be able to figure this out not really sure.

When you removed the dell data safe how did you do it this is a really important question?

---

### Post by TheRaiderNation on 2010-12-06
Sorry to get back so late, I had a family party and had to go back to college today. Anyways, I removed it using the program uninstall through windows. Also the exact size (I'm pretty sure its a reinstall disc) is 5.7GB

---

### Post by wilee-nilee on 2010-12-06
> **TheRaiderNation said:**
> Sorry to get back so late, I had a family party and had to go back to college today. Anyways, I removed it using the program uninstall through windows. Also the exact size (I'm pretty sure its a reinstall disc) is 5.7GB

Is this the program I'm not familiar with it, as W7 has a backup setup that can copy the whole thing a image of the whole setup.
[http://www.addictivetips.com/windows-tips/backuprestore-windows-uninstall-programs-list/](http://www.addictivetips.com/windows-tips/backuprestore-windows-uninstall-programs-list/)

---

### Post by TheRaiderNation on 2010-12-06
> **wilee-nilee said:**
> Is this the program I'm not familiar with it, as W7 has a backup setup that can copy the whole thing a image of the whole setup.
[http://www.addictivetips.com/windows-tips/backuprestore-windows-uninstall-programs-list/](http://www.addictivetips.com/windows-tips/backuprestore-windows-uninstall-programs-list/)
Are you saying I should use that program to remove datasafe instead of just going to control panel and uninstalling datasafe?

---

### Post by wilee-nilee on 2010-12-06
> **TheRaiderNation said:**
> Are you saying I should use that program to remove datasafe instead of just going to control panel and uninstalling datasafe?

> **TheRaiderNation said:**
> Sorry to get back so late, I had a family party and had to go back to college today. Anyways, I removed it using the program **uninstall** through windows. Also the exact size (I'm pretty sure its a reinstall disc) is 5.7GB

No I was trying to figure out what **uninstall** was as I had never heard of it in regards to backup, this was the closest I could find,I was trying to confirm what you had actually used to generate a disc the size you mentioned.

---

### Post by TheRaiderNation on 2010-12-06
Okay, I figured out a solution, it seems as though I do have to boot into the recovery partition. So in grub I changed the set root from 3 to 2 (changed hd3 to hd2), and it worked. Which I find a bit odd. Why would I have to boot from the recovery partition to get into windows 7?

Also, does this mean if I wanted to triple boot (say to mac osx, along with win7 and ubuntu) I won't be able to? Since I need to boot into recovery in order to boot into win7?

---

### Post by oldfred on 2010-12-06
The default install of win7 creates a separate 100MB boot/recovery partition, so you can encrypt the main windows install. Windows always boot from the partition with the boot flag. Grub does not use the boot flag, but some BIOS require a boot flag on a primary partition (BIOS assumes windows).

You can install into one partition if overwriting XP, Vista or just creating the one install NTFS with boot flag partition yourself.

---

### Post by TheRaiderNation on 2010-12-06
So then could I just assign a bootflag to my win7 partition? Also my recovery partition isn't 100mbs. its 15gbs.

---

### Post by oldfred on 2010-12-06
If your main system partition does not have all the boot files it will not work. If you move boot flag you should be able to repair it.

Perhaps your computer vendor also put the vendor recovery files in the same partition as the windows boot or something got moved around. Usually the vendor recovery just has the two boot files.

---

### Post by TheRaiderNation on 2010-12-06
Okay, so I peeked into my recovery partition and found that there are boot files on the root there, if I copy those files onto the root of the win7 partition and assign a boot flag to the win7 partition, could I then boot from the win7 partition and then free up the recovery partition for use?

Okay, I just re read that and my words are a little cluttered. Basically here's my school of though:
-Copy boot files from hd2 to hd3
-Assign boot flag to hd3

Would that allow me to boot straight to hd3 (win7) instead of having to go through hd2(recovery) first?

---

### Post by oldfred on 2010-12-06
You may still have to run windows repairs, but the repairs usually work as we have had many delete the hidden boot/recovery and have to do what you want. 

The only issue may be the BCD but that may be ok also. I think I saw once that someone did that and it worked.

---

### Post by TheRaiderNation on 2010-12-06
So how can I check/edit my BCD to see if win7 is booting from the recovery, and if it is, how to I change it? Would EasyBCD do the trick?

---

### Post by wilee-nilee on 2010-12-06
x

---

### Post by oldfred on 2010-12-06
I do not know BCD's well as the bootscript does not parse the BCD hive.
You can just copy the files and boot flag over and if it boots that solves the problem. You can use windows to repair the BCD. I think easyBCD is another tool that works.

For any system you have installed in your computer you need to have a repair CD or USB. For windows the windows repair CD and for Linux one or more liveCDs.

Vista & win& use same BCD.
How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
BootRec.exe /RebuildBcd

---

