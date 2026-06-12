---
title: "Upgraded, Dual Boot to Vista no longer working"
date: 2010-04-29
forum: General Help
---

### Post by dysalot on 2010-04-29
NOTE:  I did not actually find a way to solve my problem, but the tips in here are helpful.  Also, it is likely that your problem is similar but to the exact same.



I will try to provide as much detail as possible.  

I upgraded today to 10.04, everything went fine and was working fine.  I went to boot back into Vista via grub2.  I immediatly get the 
PXE-E61 Media Test Failure, check cable
PXE-M0F Exiting PXE ROM

I first checked my boot order, and lan is very last.  Also, through Ubuntu I can view everything on the hard drive so it is not that.  I think it may have to do with during the update process, it asked about grub2 update preferences and asked about different drives and such (I am not exactly sure what it was called).  I didn't select all of the choices, and I believe this may be the cause, as this was the only thing I had control of that I could have screwed up.

Any ideas on how to fix this?

Thanks in advance.

---

### Post by dysalot on 2010-04-30
Just want this to get seen by morning users.

---

### Post by Premium Jersey Milk on 2010-04-30
I don't know how to fix it but I am suffering from a similar problem. During the UPGRADE process I selected to keep the OLD GRUB but I did select all the drives. 

What happens when I choose the windows7/vista loader in GRUB is it goes to a black screen with a blinking underscore in the top left corner.

I'm running grub 1.98 according to the top of my grub menu.

---

### Post by dino99 on 2010-04-30
when you dist-upgrade, if grub1 was installed, you need/must remove it (grub1+grub2=troubles and misconfig)

so, first thing, into synaptic: remove/purge all the grub packages but grub-pc & grub-common (which are grub2)

then into terminal: sudo grub-mkconfig && update-grub

IMPORTANT: if you have multi-boot, take care to not overwrite the windows mbr !!! If you have done it, well you have to reinstall windows bootloader into its partition. Grub2 have to be installed on lucid partition.

---

### Post by Premium Jersey Milk on 2010-04-30
So I just did all that and restarted. Same deal, just gives me the blinking underscore page with vista.

---

### Post by dysalot on 2010-04-30
> **dino99 said:**
> when you dist-upgrade, if grub1 was installed, you need/must remove it (grub1+grub2=troubles and misconfig)

so, first thing, into synaptic: remove/purge all the grub packages but grub-pc & grub-common (which are grub2)

then into terminal: sudo grub-mkconfig && update-grub

IMPORTANT: if you have multi-boot, take care to not overwrite the windows mbr !!! If you have done it, well you have to reinstall windows bootloader into its partition. Grub2 have to be installed on lucid partition.
Thanks, for the help, I did your first step, although I was already running grub2.  I am now going to try to fix the Windows mbr.  I will let you know if this works.

---

### Post by dino99 on 2010-04-30
good luck guys, thats all for today here, see you again on Saturday  ):P

---

### Post by dysalot on 2010-04-30
Okay, I have taken a couple steps back to move maybe a half-step forward.  I reinstalled the Windows mbr, which then deleted grub.  So I went a live cd I had from 9.10 and reinstalled grub.  I am getting the same error.  I have also taken lan off the boot order.

Interestingly I plugged in an ethernet cable after this, and when trying to boot Vista, It connects via the lan, looking for something to boot it.  It (obviously) doesn't find anything and then quits.

---

### Post by oldfred on 2010-04-30
If it is the windows problem it is not fixmbr which overwrites grub in the MBR but fixboot which also has part of the windows boot in the partition boot sector/record.

To see where everything is at:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by dysalot on 2010-04-30
Ok I did that. Also I don't think it helps but at the start of the error its says Geom error, I just want to provide as much info as possible.
Here are the results.
```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=08311bac-dff2-4629-978f-3753aaefc711)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 213545050 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 213574290 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda2 has 192296959 sectors, but according to the info 
                       from fdisk, it has 192308481 sectors.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 213576154 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   195,382,529   192,308,482   7 HPFS/NTFS

/dev/sda2 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   213,262,874   213,260,827   7 HPFS/NTFS
/dev/sdb2         213,262,875   234,436,544    21,173,670   5 Extended
/dev/sdb5         213,262,938   233,440,514    20,177,577  83 Linux
/dev/sdb6         233,440,578   234,436,544       995,967  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mmcblk0p1   2052-2A9E                              vfat       ns&#381;sòâ%UÈ&#8230;d                   
/dev/sda1        84A4EC25A4EC1C04                       ntfs       TOSHIBA SYSTEM VOLUME         
/dev/sda2        F4D6F105D6F0C93E                       ntfs       SQ004242V05                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        38EEE697EEE64D26                       ntfs       Winkler                       
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        08311bac-dff2-4629-978f-3753aaefc711   ext4                                     
/dev/sdb6        4cc2e890-fbf4-4d6a-ac1a-7cb0bdf007fe   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/mmcblk0p1   /media/ns_               vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 08311bac-dff2-4629-978f-3753aaefc711
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 08311bac-dff2-4629-978f-3753aaefc711
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 08311bac-dff2-4629-978f-3753aaefc711
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=08311bac-dff2-4629-978f-3753aaefc711 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 08311bac-dff2-4629-978f-3753aaefc711
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=08311bac-dff2-4629-978f-3753aaefc711 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 08311bac-dff2-4629-978f-3753aaefc711
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=08311bac-dff2-4629-978f-3753aaefc711 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 08311bac-dff2-4629-978f-3753aaefc711
	echo	'Loading Linux 2.6.31-20-generic ...'
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=08311bac-dff2-4629-978f-3753aaefc711 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 08311bac-dff2-4629-978f-3753aaefc711
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 08311bac-dff2-4629-978f-3753aaefc711
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set f4d6f105d6f0c93e
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=08311bac-dff2-4629-978f-3753aaefc711 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=4cc2e890-fbf4-4d6a-ac1a-7cb0bdf007fe none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 109.4GB: boot/grub/core.img
 109.4GB: boot/grub/grub.cfg
 114.9GB: boot/initrd.img-2.6.31-20-generic
 115.7GB: boot/initrd.img-2.6.32-21-generic
 110.2GB: boot/vmlinuz-2.6.31-20-generic
 115.0GB: boot/vmlinuz-2.6.32-21-generic
 115.7GB: initrd.img
 114.9GB: initrd.img.old
 115.0GB: vmlinuz
 110.2GB: vmlinuz.old

```

---

### Post by bwsmith7 on 2010-04-30
I am having the same problem.  I am very new at all of this and not very tech-savvy.  How do I reinstall the Windows mbr?  I use my Windows 7 more than Ubuntu, and I am really stressing out about losing it.  Thanks for any help.

---

### Post by dysalot on 2010-04-30
> **bwsmith7 said:**
> I am having the same problem.  I am very new at all of this and not very tech-savvy.  How do I reinstall the Windows mbr?  I use my Windows 7 more than Ubuntu, and I am really stressing out about losing it.  Thanks for any help.
Well reinstalling windows mbr, didn't help me.  It only erased grub and I got the same errors, but with no way of getting my computer to any OS at all until I put in an old Ubuntu live cd, and went to the test desktop.
But I followed this site:  [http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/]("http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/")

It should be similar for windows 7.

I am still stuck at square 1, that only served me as a distractor, but I may have done something wrong. Personally I couldn't get /fixboot to work, only /fixmbr.

---

### Post by oldfred on 2010-04-30
You need to fixboot as grub is installed to the windows boot sector. You can also use testdisk to repair from the backupBS.

Instructions are here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

/dev/mmcblk0p1
Are you running raid or was this drive ever a raid drive? Or other special config?

---

### Post by dysalot on 2010-04-30
> **oldfred said:**
> You need to fixboot as grub is installed to the windows boot sector. You can also use testdisk to repair from the backupBS.

Instructions are here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

/dev/mmcblk0p1
Are you running raid or was this drive ever a raid drive? Or other special config?

Thanks for the help I'm off to do that now.  I thought that was the problem especially after looking at the results.  I tried fixboot earlier and it didn't work hopefully I will be more successful.

Also, I don't believe the drive was ever set up as a RAID drive.  The computer is 4 years old now, so I don't remember everything I have done to it, but I don't believe it ever had any special configuration.  I guess initially the second hard drive was setup to backup the first, but I got rid of that quickly for the space. 

By the way thanks again, and I will post my results. fingers crossed.

---

### Post by dysalot on 2010-04-30
I tried testdisk, and couldn't get that to work, infact it removed the listing for Vista in Grub all together.  Will try the Fix boot in a little bit.

---

### Post by wilee-nilee on 2010-04-30
> **dysalot said:**
> I tried testdisk, and couldn't get that to work, infact it removed the listing for Vista in Grub all together.  Will try the Fix boot in a little bit.

Be careful that you know what you doing. oldfred and a couple of others who are very good at this sort of thing are online right now, so chill a bit and get some solid advice and give descriptions of exactly what you have done, rather then this didn't work.

---

### Post by oldfred on 2010-04-30
I think fixboot will do it but I will post all the windows commands just in case.

Vista or 7 repair
Comments by others:
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)

---

### Post by dysalot on 2010-04-30
Sorry for the delay I had to help my brother out.  When I try bootrec.exe/FixBoot  it returns with "Parameter is incorrect"  but I will try again with these instructions.  I have done bootrec.exe/fixmbr  earlier, and it did delete grub like you said, and I had to go reinstall grub.

quick update:
the repair keeps saying "Could not detect a problem"
chkdsk/r says "This is NTFS | Cannot lock current drive | windows cannot run disk checking on this volume because it is write protected"

---

### Post by ...acid on 2010-04-30
Hey there guys/gals.  I'm experiencing the same issue.  I've been reading up on other random other threads and this appears to be a common issue.  Quite interesting....  

This isn't my brightest moment...installing Ubuntu 10.04 during finals week, nuking my Windows partition.  I should have uploaded my schoolwork to my email or something.

---

### Post by oldfred on 2010-05-01
More info on chkdsk

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

With the XP chkdsk you had to specify a drive c: . Are you some how running the chkdsk on the CD?

---

### Post by dysalot on 2010-05-01
Ok, I'll give some updates.  Grub is no longer listing Windows Vista as mentioned earlier.  I can try to boot windows Vista through changing the boot order to hdd0 going first then hdd1 (allowing the vista hdd to boot first) (I don't think this is a big problem).

I ran /fixmbr again, and then reinstalled grub only choosing sdb2 (I think), I know I didn't choose sda which is where Vista is.

I was not specifying a hard drive when running chkdsk /r, but will try that next.

When running the recovery cd for vista, it no longer lists my c: hard drive when repairing. I have run the boot info script again and these are the updated results:

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 213545050 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 213574290 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Mounting failed:
Failed to read last sector (192308481): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
Failed to read last sector (192308481): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 213576154 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   195,382,529   192,308,482   7 HPFS/NTFS

/dev/sda2 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   213,262,874   213,260,827   7 HPFS/NTFS
/dev/sdb2         213,262,875   234,436,544    21,173,670   5 Extended
/dev/sdb5         213,262,938   233,440,514    20,177,577  83 Linux
/dev/sdb6         233,440,578   234,436,544       995,967  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mmcblk0p1   2052-2A9E                              vfat       nsŽsòâ%UÈ&#133;d                   
/dev/sda1        84A4EC25A4EC1C04                       ntfs       TOSHIBA SYSTEM VOLUME         
/dev/sda2        F4D6F105D6F0C93E                       ntfs       SQ004242V05                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        38EEE697EEE64D26                       ntfs       Winkler                       
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        08311bac-dff2-4629-978f-3753aaefc711   ext4                                     
/dev/sdb6        4cc2e890-fbf4-4d6a-ac1a-7cb0bdf007fe   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/mmcblk0p1   /media/ns_               vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /media/cdrom0            udf        (ro,nosuid,nodev,utf8,user=jared)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 08311bac-dff2-4629-978f-3753aaefc711
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=08311bac-dff2-4629-978f-3753aaefc711 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 08311bac-dff2-4629-978f-3753aaefc711
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=08311bac-dff2-4629-978f-3753aaefc711 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 08311bac-dff2-4629-978f-3753aaefc711
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=08311bac-dff2-4629-978f-3753aaefc711 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 08311bac-dff2-4629-978f-3753aaefc711
	echo	'Loading Linux 2.6.31-20-generic ...'
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=08311bac-dff2-4629-978f-3753aaefc711 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 08311bac-dff2-4629-978f-3753aaefc711
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 08311bac-dff2-4629-978f-3753aaefc711
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=08311bac-dff2-4629-978f-3753aaefc711 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=4cc2e890-fbf4-4d6a-ac1a-7cb0bdf007fe none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 109.8GB: boot/grub/core.img
 111.6GB: boot/grub/grub.cfg
 114.9GB: boot/initrd.img-2.6.31-20-generic
 115.7GB: boot/initrd.img-2.6.32-21-generic
 110.2GB: boot/vmlinuz-2.6.31-20-generic
 115.0GB: boot/vmlinuz-2.6.32-21-generic
 115.7GB: initrd.img
 114.9GB: initrd.img.old
 115.0GB: vmlinuz
 110.2GB: vmlinuz.old
```

---

### Post by oldfred on 2010-05-01
If you are not running raid, run these commands. Drives save old raid metadata that confuses things.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings

---

### Post by dysalot on 2010-05-01
I rand dmraid and it said "no raid disks and with names: "/dev/sda"" it said the same for sdb.

---

### Post by dino99 on 2010-05-01
have you try: sudo grub-mkconfig && update-grub

windows is not chainloaded as you can boot it if you change hdd order

---

### Post by oldfred on 2010-05-01
You now have a partition table problem. Usually test disk fixes that.
/dev/sda2 ends after the last sector of /dev/sda

I would try gparted right click and check. Or we can run fdisk or sfdisk to see if that repairs it.

---

### Post by dysalot on 2010-05-01
I checked with gparted and it says the c: drive is completely unallocated. I want to make sure I dont screw up (more than I already have).  How do I go about fixing the partitions?

---

### Post by oldfred on 2010-05-01
Messing with partition tables is one of the more risky things you can do. Make sure you have good backups and repair CDs ( i like to have several) just in case.

This reorders partitions but should reset things since it writes the partition table. # are comments just enter letters.


You can reorder the partition with fdisk:
sudo fdisk /dev/sda
x  # enter expert mode
f  # fix  partition table
r  # return
p  # to print
v  # to verify partition 
#if ok
w  #  write the changes to disk

Reordering the partition table requires reinstall grub.

Even more advanced:
Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

From above post you should backup current table before hand so you can go back if necessary.
sudo sfdisk -d /dev/sda > PT.txt

---

### Post by dysalot on 2010-05-01
Ok I spent the last period of time backing up sda to an external hard drive.  I started the fdisk and when I got to command f it responded "Nothing to do. Ordering is correct already."  I went through with the other commands but nothing was changed.

I ran fdisk and gparted (again) and wanted to provide more info.  In gparted it says that the whole drive is unallocaed and that the partition cannot exist outside the drive.  See below

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6bba44a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       12162    96154241    7  HPFS/NTFS
jared@Jared-laptop:~$ gksu gparted /dev/sda
======================
libparted : 2.2
======================
Can't have a partition outside the disk!

```

---

### Post by jdjenkins on 2010-05-02
I have the same problem with XP; I did an update of grub to grub2, and (probably stupidly!!) wrote grub2 to all partitions. So, I can still see XP in the grub menu, but I get the black screen and white flashing ">"  cursor. The only thing it seems to respond to is ctrl+alt+delete :confused:

So, does this mean I have a MBR problem? Is it possible to still manually boot XP via some grub command?

thanks in advance,

Jon.

ps - here's fdisk -l and grub.cfg

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xede55a04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1034     8305573+  12  Compaq diagnostics
/dev/sda2   *        1035        7113    48829567+   7  HPFS/NTFS
/dev/sda3            7114       12161    40548060    f  W95 Ext'd (LBA)
/dev/sda5            7114       10631    28258303+   7  HPFS/NTFS
/dev/sda6           10632       12090    11719386   83  Linux
/dev/sda7           12091       12161      570276   82  Linux swap / Solaris
------------------------------------

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set df3215e4-bcfe-478b-8ba4-8b4a06099407
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set df3215e4-bcfe-478b-8ba4-8b4a06099407
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set df3215e4-bcfe-478b-8ba4-8b4a06099407
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=df3215e4-bcfe-478b-8ba4-8b4a06099407 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set df3215e4-bcfe-478b-8ba4-8b4a06099407
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=df3215e4-bcfe-478b-8ba4-8b4a06099407 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set df3215e4-bcfe-478b-8ba4-8b4a06099407
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=df3215e4-bcfe-478b-8ba4-8b4a06099407 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set df3215e4-bcfe-478b-8ba4-8b4a06099407
    echo    'Loading Linux 2.6.31-15-generic ...'
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=df3215e4-bcfe-478b-8ba4-8b4a06099407 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-15-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set df3215e4-bcfe-478b-8ba4-8b4a06099407
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set df3215e4-bcfe-478b-8ba4-8b4a06099407
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9eccddf0ccddc327
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows XP Media Center Edition (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 4c54a5a254a58ef0
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

Just rebuilt boot.ini in the windows recovery console. Then ran update-grub; the last section
of grub.cfg now reads:

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9eccddf0ccddc327
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 4c54a5a254a58ef0
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

---

### Post by jdjenkins on 2010-05-02
I can now get into Windows using info from here:
 
[http://www.tinyempire.com/shortnotes/files/ntldr_missing.htm](http://www.tinyempire.com/shortnotes/files/ntldr_missing.htm)
 
I still need to figure out how to fix the boot sequence, but at least I can get into XP and alter stuff from there more easily if necessary,
 
Jon.

---

### Post by dysalot on 2010-05-02
Hey could you put all of those results inside brackets that say [ code] [ /code]  (delete the space inside the [].

---

### Post by oldfred on 2010-05-02
Could you post the PT.txt

From above post you should backup current table before hand so you can go back if necessary.
sudo sfdisk -d /dev/sda > PT.txt

Testdisk also repairs partitions tables and I would suggest reviewing those instructions.
enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

### Post by dysalot on 2010-05-02
My hard drive has died for all intents and purposed.  I needed more space, and managed to get the files off of it before it died.  It wont even let me format the drive.  My roommate has a copy of windows 7 he hasn't used so I am going to go that route.

---

### Post by bwsmith7 on 2010-05-02
Sorry to hear that, dysalot.  I am a newbie and afraid to try any of these solutions until someone identifies one that has been tested a few times and works. I can't afford to lose all the data on my Windows partition.  

My brother was about to start dual-booting Linux, but after this fiasco, he has changed his mind.  I may go back to straight Windows as well.  Perhaps more testing needs to be done in the future before upgrades are handed out.  For new users especially, stuff like this is a disaster.

---

### Post by bcbc on 2010-05-02
> **jdjenkins said:**
> I can now get into Windows using info from here:
 
[http://www.tinyempire.com/shortnotes/files/ntldr_missing.htm](http://www.tinyempire.com/shortnotes/files/ntldr_missing.htm)
 
I still need to figure out how to fix the boot sequence, but at least I can get into XP and alter stuff from there more easily if necessary,
 
Jon.
Here is a how to for the diagnosis and fix for a damaged boot sector: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by bcbc on 2010-05-02
> **bwsmith7 said:**
> Sorry to hear that, dysalot.  I am a newbie and afraid to try any of these solutions until someone identifies one that has been tested a few times and works. I can't afford to lose all the data on my Windows partition.  

My brother was about to start dual-booting Linux, but after this fiasco, he has changed his mind.  I may go back to straight Windows as well.  Perhaps more testing needs to be done in the future before upgrades are handed out.  For new users especially, stuff like this is a disaster.

I couldn't agree more. 

In the meantime, get an external hard drive. Boot from the live CD and mount your windows partition. Then copy everything before you try and fix it.

---

### Post by dysalot on 2010-05-02
It wasn't that painful.  I needed a larger hard drive anyway, and I will continue to dual-boot.  It's unfortunate that I had this problem, but I don't hold any grudges.  I also thank everyone who helped.

---

### Post by jdjenkins on 2010-05-03
Just to say my problem was fixed using FIXBOOT with the XP recovery system,

thanks,

Jon.

---

### Post by bwsmith7 on 2010-05-05
I finally got my windows 7 back by following these instructions from this post: [http://ubuntuforums.org/showpost.php?p=9243314&postcount=32](http://ubuntuforums.org/showpost.php?p=9243314&postcount=32)

Here are the instructions, courtesy of oldfred:

> You will need to boot with your  Vista/Windows 7 installation disk. Hit Enter at the language selection  prompt then hit "R" to get to the repair section. You can then select  the automatic boot repair tool, but it  often will not do any good. Then select the command prompt (console) and  type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot  record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot  
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd


You may want to run the fixMBR so you can directly boot windows to  know it works, then you can reinstall grub2 and run the sudo update-grub  to make sure it sees the windows.

I have no idea how to get Ubuntu back.  Hopefully someone comes up with a relatively easy way for new users to get everything back to normal.  Thanks for the help!

---

### Post by Kesselkopf on 2010-05-15
Hi,

Just reading your difficulties with dual booting.

I had similar problems after installation re booting into Vista. What it turned out to be in my case was when installing Ubuntu 10.04 I chose the boot loader not to be on /dev/sda and the boot symptoms for Vista was similar to yours.

I downloaded Win boot disk from Microsoft and got Vista going again using the R repair option on boot up. Then did a clean reinstall of Ubuntu 10.04 leaving the bootloader location as default. All turned out ok and is working well. 
If you have a seperate /home partition then doing a clean install while leaving the /home directory intact will let you keep what's already in the /home directory.

I haven't tried updating from Grub to Grub2 on any machine installation. When I previously upgraded from 9.04 to 9.10 I declined the offer to update to Grub2 as I new Grub was working well. 

For 10.04 install I let it carry on with Grub2 as it was default anyway and my machine dual boots just great. 

This is a laptop with just one hard drive.

Hope something here can help you out. It's great when the dual booting works. Reason for dual boot is that I can run itunes!!

---

