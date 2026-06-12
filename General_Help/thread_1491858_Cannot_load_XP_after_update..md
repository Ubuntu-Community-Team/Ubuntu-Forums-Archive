---
title: "Cannot load XP after update."
date: 2010-05-24
forum: General Help
---

### Post by YoJembo on 2010-05-24
Could someone please advise me or point me to the right thread.

I allowed the UNR on my wife's Asus 1000H netbook to update to 10.04 and even updated since but the GRUB menu screen just keeps reloading itself if I select  XP. We still need XP... at least for the time being. We can access the NTFS partitions still.

Now if I download UNR and do a clean install will that fix it? 

Should I just remove the HDD and reformat it completely on another computer and reinstall both OSs?

Should I reinstall UNR 9.10? (I've heard there are power consumption problems with 10.04 anyway.)

Any other suggestions?

Thanks in advance.

---

### Post by wilee-nilee on 2010-05-24
When you upgraded were you given a prompt on where to install grub and did you install anywhere other then in sda if this computer has only one hard drive.

---

### Post by arrange on 2010-05-24
The output of [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/") (if you don't know how to run the script, [look here]("http://bootinfoscript.sourceforge.net/")) would help.

---

### Post by wilee-nilee on 2010-05-24
> **arrange said:**
> The output of [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/") (if you don't know how to run the script, [look here]("http://bootinfoscript.sourceforge.net/")) would help.

Good call I would have requested the same sooner or later.;)

---

### Post by YoJembo on 2010-05-24
> **wilee-nilee said:**
> When you upgraded were you given a prompt on where to install grub and did you install anywhere other then in sda if this computer has only one hard drive.

Well it was stated when in doubt just select them all, and GRUB seemed to only post that partition as having an OP too. 

So if I run GRUB in UNR can I fix that?

Yeah, I should have mentioned that I'm quite a Ubuntu/Linux noob. :)

---

### Post by arrange on 2010-05-24
If that is the case, you're not an "innocent bystander" anymore :))

This is an unfortunate "bug" IMO, see for example
[http://ubuntuforums.org/showthread.php?t=1490480](http://ubuntuforums.org/showthread.php?t=1490480)

But to be sure, provide the output of the script if you can.

---

### Post by wilee-nilee on 2010-05-24
> **arrange said:**
> If that is the case, you're not an "innocent bystander" anymore :))

This is an unfortunate "bug" IMO, see for example
[http://ubuntuforums.org/showthread.php?t=1490480](http://ubuntuforums.org/showthread.php?t=1490480)

But to be sure, provide the output of the script if you can.

That is a good link, post the script as suggested. A reinstall or reloading grub will not fix it if you put grub in the windows partition but testdisk should. Just post the script and arrange will direct you.

---

### Post by veggen on 2010-05-24
There was a thread couple of days back with the same issue. The guy solved it by restoring Windows' bootloader trough it's recovery mode and then reinstalled GRUB through Ubuntu Live CD. Try searching yourself if you need more info, I couldn't find it for some reason (it's marked as SOLVED).

---

### Post by wilee-nilee on 2010-05-24
> **veggen said:**
> There was a thread couple of days back with the same issue. The guy solved it by restoring Windows' bootloader trough it's recovery mode and then reinstalled GRUB through Ubuntu Live CD. Try searching yourself if you need more info, I couldn't find it for some reason (it's marked as SOLVED).

That is an option if recovery is possible, if your talking about using a install disc this is a netbook and I doubt the OP has a install disc. I don't think the recovery disc from neosmart will do it. If it is just that grub is in the windows boot then testdisk or lilo is the best fix.

---

### Post by YoJembo on 2010-05-24
> **arrange said:**
> If that is the case, you're not an "innocent bystander" anymore :))

This is an unfortunate "bug" IMO, see for example
[http://ubuntuforums.org/showthread.php?t=1490480](http://ubuntuforums.org/showthread.php?t=1490480)

But to be sure, provide the output of the script if you can.

Heh.:)

Thanks, here it is:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 54879452 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 54860356 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 54860332 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 54879452 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    54,572,804    54,572,742   7 HPFS/NTFS
/dev/sda2          83,859,300   156,216,059    72,356,760   7 HPFS/NTFS
/dev/sda3         156,216,060   156,296,384        80,325  ef EFI (FAT-12/16/32)
/dev/sda4          54,572,805    83,859,299    29,286,495   5 Extended
/dev/sda5          54,572,868    82,525,904    27,953,037  83 Linux
/dev/sda6          82,525,968    83,859,299     1,333,332  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000 MB, 1000341504 bytes
255 heads, 63 sectors/track, 121 cylinders, total 1953792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     1,953,791     1,953,729   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        30001C24001BEF98                       ntfs       System eee                    
/dev/sda2        741887D718879730                       ntfs       Data eee                      
/dev/sda4: PTTYPE="dos" 
/dev/sda5        ef6da83d-0064-419b-8b81-8d7152b2df41   ext4                                     
/dev/sda6        2aac9907-290d-4d28-b8b9-976e2952046a   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0065-3916                              vfat       SD CARD                       
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/SD CARD           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

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
search --no-floppy --fs-uuid --set ef6da83d-0064-419b-8b81-8d7152b2df41
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
search --no-floppy --fs-uuid --set ef6da83d-0064-419b-8b81-8d7152b2df41
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ef6da83d-0064-419b-8b81-8d7152b2df41
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=ef6da83d-0064-419b-8b81-8d7152b2df41 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ef6da83d-0064-419b-8b81-8d7152b2df41
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=ef6da83d-0064-419b-8b81-8d7152b2df41 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ef6da83d-0064-419b-8b81-8d7152b2df41
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ef6da83d-0064-419b-8b81-8d7152b2df41 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ef6da83d-0064-419b-8b81-8d7152b2df41
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ef6da83d-0064-419b-8b81-8d7152b2df41 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ef6da83d-0064-419b-8b81-8d7152b2df41
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=ef6da83d-0064-419b-8b81-8d7152b2df41 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ef6da83d-0064-419b-8b81-8d7152b2df41
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=ef6da83d-0064-419b-8b81-8d7152b2df41 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ef6da83d-0064-419b-8b81-8d7152b2df41
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ef6da83d-0064-419b-8b81-8d7152b2df41
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 30001c24001bef98
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=ef6da83d-0064-419b-8b81-8d7152b2df41 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2aac9907-290d-4d28-b8b9-976e2952046a none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  28.0GB: boot/grub/core.img
  28.1GB: boot/grub/grub.cfg
  33.3GB: boot/initrd.img-2.6.31-20-generic
  31.6GB: boot/initrd.img-2.6.32-21-generic
  30.1GB: boot/initrd.img-2.6.32-22-generic
  32.2GB: boot/vmlinuz-2.6.31-20-generic
  32.3GB: boot/vmlinuz-2.6.32-21-generic
  34.4GB: boot/vmlinuz-2.6.32-22-generic
  30.1GB: initrd.img
  31.6GB: initrd.img.old
  34.4GB: vmlinuz
  32.3GB: vmlinuz.old

---

### Post by arrange on 2010-05-24
Yes, you have inadvertently rewritten your ntfs boot sectors, bystander :)
Your best bet would be your win recovery disc and the *fixboot* (not fixmbr) option.
Or you can use *testdisk* to copy a boot sector backup back.
For details see the link I provided. 

[COLOR="Silver"]sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Grub 2
Boot sector info: Grub 2 is installed in the boot sector of sda1 and 
[..]
sda2: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Grub 2
Boot sector info: Grub 2 is installed in the boot sector of sda2 and 
[/COLOR](should say Windows boot sector, not Grub)

For a related bug see f.e.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/545989](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/545989)

---

### Post by YoJembo on 2010-05-30
Thank you all for taking the time to answer me. Sorry it took so long for me to get back to you.

> **arrange said:**
> Yes, you have inadvertently rewritten your ntfs  boot sectors, bystander :)
Your best bet would be your win recovery disc and the *fixboot*  (not fixmbr) option.
Or you can use *testdisk* to copy a boot sector backup back.
For details see the link I provided...[COLOR=Silver]

[/COLOR]...(should say Windows boot sector, not Grub)

For a related bug see f.e.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/545989](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/545989)

@arrange: Not too sure about that. This is a netbook and it only has a recovery disk. Now I don't feel like spending the money on a usb DVD drive I'll have only one use for.

I know how to get XP to install off a USB stick and that's a bit tricky, not sure it will run up *fixboot* that way. Also I know how to reinstall the recovery disk ghost image (or my own) of the OS via a USB stick too. I don't think that will help.

I might try install Win7 on the partition... that seems more straight-forward to do off a USB stick than XP.  It's all set up to go, anyway. Also, if that doesn't fix it,  I should be able to run up it's recovery console and run *fixboot* that way. What do you think?

I'll reinstall UNR 9.10 because of the power drain issues... (unless they are fixed, does anybody know?)

I guess I understand what has happened, I keep rerunning GRUB because it's on all the partitions... so I will only install it on the sda partition in future... thanks for that, that definitely was not clear during the grub upgrade install.

Cheers.

---

