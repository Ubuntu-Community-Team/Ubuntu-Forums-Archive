---
title: "GRUB2 Boot issues (documentation didn't help)"
date: 2010-12-05
forum: General Help
---

### Post by LustrousWS6 on 2010-12-05
Just some background on the system:
Asus G73, Win7/Ubuntu 10.04 dual boot system
- I updated to GRUB2 and put a graphic in to look pretty lol

It's been working flawlessly for me for about 4 months - only wierd thing was ever since I put a graphic background in for GRUB, when I booted the Ubuntu partition, it would be a purple screen with random discolored pixels at the top of the screen.  After a few seconds, it would show the login prompt, I'd select my user and enter my password and all would be fine.

Yesterday, the computer wouldn't wake from hibernation and I had to do a hard shutdown.  I've only had this happen twice before and both times it would just take a couple minutes longer to boot.  This time, it just stays at the purple screen with pixelation indefinitely.  I'd be fine restoring the partition but I REALLY need a programming project I've been working on for the last month off of this partition.  If someone can show me how to access this partition to just get that file off I'd GREATLY appreciate it.  I read around and found nothing relating to Windows7 accessing Ubuntu partitions - it doesn't even show up under Computer.  I tried recovery mode for Ubuntu but the same purple pixelated screen came up indefinitely.  My Win7 partition still boots flawlessly.

Your time is greatly appreciated and I thank you for any help you can provide.  I'm never messing with GRUB again after this...

---

### Post by LustrousWS6 on 2010-12-05
I just tried using a 10.10 live CD to recover GRUB but after the Ubuntu loading screen finishes (the one with alternating red/white dots to indicate progress), it goes to a white screen with tons of pixelation.   

I'm currently downloading 10.04 to create a live CD and see if that works out any better.

---

### Post by Hippytaff on 2010-12-05
It might be worth posting the results.txt after running this script via a live cd so that people who know much more than me can try to help you rescue your stuff
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Edit -> and welcome to the forums :-)

---

### Post by drs305 on 2010-12-05
Do you get the Grub2 menu before the problems occur? If so, press "e" to edit the menuentry and add "nomodeset" at the end of the "linux" line (right after **quiet splash**). CTRL-x to boot.

If it's a video driver issue this may get you to the Desktop.

---

### Post by Hippytaff on 2010-12-05
> **drs305 said:**
> Do you get the Grub2 menu before the problems occur? If so, press "e" to edit the menuentry and add "nomodeset" at the end of the "linux" line (right after **quiet splash**). CTRL-x to boot.

If it's a video driver issue this may get you to the Desktop.
It's always a nomodset fix when I ask for the results.txt :-s
How do you spot this stuff?

---

### Post by LustrousWS6 on 2010-12-05
> **drs305 said:**
> Do you get the Grub2 menu before the problems occur? If so, press "e" to edit the menuentry and add "nomodeset" at the end of the "linux" line (right after **quiet splash**). CTRL-x to boot.

If it's a video driver issue this may get you to the Desktop.

Yes, the Grub2 menu does show. Problem only occurs after I select Ubuntu or Ubuntu's recovery partition as I described.

I'd love to try either of your suggestions but I'd need a walk-through key by key because the letters on my GRUB menu are black against a mostly black background ](*,).  Hopefully I can get it to boot off the 10.04 liveCD after I'm done downloading it.


I've been trying to use Ex2FSD to access the partitions through Win7 and they mount but it gives me a message to format them before I can access them when I try to look inside (this would defeat the whole purpous). 

Thank you for the warm welcome and your help!

---

### Post by Hippytaff on 2010-12-05
when the grub2 menu comes up press e
the you'll be shown a line, change the 'quiet splash' bit at the end to 'nomeodset;

so it looks thus
```

file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz[COLOR=Red] nomodeset[/COLOR]

```:-)

---

### Post by drs305 on 2010-12-05
If you can't see letters, at the Grub menu press "c".

Then (I hope you are good at touch typing):
```
set color_normal=green/black
```
Press ENTER, then ESC to take you back to the main menu. Press "e" to edit the menuentry to try the 'nomodeset' fix. (No guarantees)

---

### Post by LustrousWS6 on 2010-12-05
YES!  I burnt another copy of the 10.10 liveCD and it worked!  I was able to access my files and copy them to my flash drive.  If you guys are still curious, I'll run that script - right now I'm gonna try the quick fix to see if I can get to the desktop.

---

### Post by Hippytaff on 2010-12-05
the quick nomodest fix should work, then you should be able to download the drivers for your nvidia graphics card in Preferences -> additional drivers

---

### Post by LustrousWS6 on 2010-12-05
> **Hippytaff said:**
> the quick nomodest fix should work, then you should be able to download the drivers for your nvidia graphics card in Preferences -> additional drivers


No joy with the quick fix.

Since I have my files, I'm ready to just install 10.10 over the 10.04 partition.  Any reason I shouldn't?

Here's the RESULTS.txt file:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    40,965,749    40,965,687  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     40,965,752   587,840,751   546,875,000   7 HPFS/NTFS
/dev/sda3         607,373,310   976,773,119   369,399,810   5 Extended
/dev/sda5         952,164,352   976,773,119    24,608,768  82 Linux swap / Solaris
/dev/sda6         607,373,312   656,199,679    48,826,368  83 Linux
/dev/sda4         587,841,536   607,371,263    19,529,728  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3E5F-3A2B                              vfat       RECOVERY                      
/dev/sda2        4ACEFD2ECEFD12C5                       ntfs       OS                            
/dev/sda3: PTTYPE="dos" 
/dev/sda4        44461c25-b14d-4e30-93db-a354afe5b8ae   ext2                                     
/dev/sda5        bcf0d098-e3b4-4241-95f6-eae28d0c06cd   swap                                     
/dev/sda6        c66c9f94-8138-4a53-ad7d-ee9383e12c73   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 44461c25-b14d-4e30-93db-a354afe5b8ae
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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 44461c25-b14d-4e30-93db-a354afe5b8ae
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 44461c25-b14d-4e30-93db-a354afe5b8ae
insmod tga
if background_image /usr/share/images/grub/Plasma-lamp.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 44461c25-b14d-4e30-93db-a354afe5b8ae
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=44461c25-b14d-4e30-93db-a354afe5b8ae ro  splash vga=786  quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 44461c25-b14d-4e30-93db-a354afe5b8ae
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=44461c25-b14d-4e30-93db-a354afe5b8ae ro single  splash vga=786
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 44461c25-b14d-4e30-93db-a354afe5b8ae
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 44461c25-b14d-4e30-93db-a354afe5b8ae
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3e5f-3a2b
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 4acefd2ecefd12c5
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=44461c25-b14d-4e30-93db-a354afe5b8ae /               ext2    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=c66c9f94-8138-4a53-ad7d-ee9383e12c73 /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=bcf0d098-e3b4-4241-95f6-eae28d0c06cd none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


 310.5GB: boot/grub/core.img
 310.6GB: boot/grub/grub.cfg
 310.4GB: boot/initrd.img-2.6.32-24-generic
 310.3GB: boot/vmlinuz-2.6.32-24-generic
 310.4GB: initrd.img
 310.3GB: vmlinuz
```

---

### Post by drs305 on 2010-12-05
If you have saved all your files and have already booted to 10.10 and the display is acceptable, installing it will probably be quicker than trying to troubleshoot what is going wrong with your system.

There may be more things we could try, but if you are not worried about lost files, download limits, customizations, etc reinstalling wouldn't be a bad option.

---

