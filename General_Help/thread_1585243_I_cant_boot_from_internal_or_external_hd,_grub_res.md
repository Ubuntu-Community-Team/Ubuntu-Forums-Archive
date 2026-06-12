---
title: "I cant boot from internal or external hd, grub rescue."
date: 2010-09-30
forum: General Help
---

### Post by bosco88 on 2010-09-30
My first problem. I cant boot from my External HD with ubuntu installed.
I get this message:
     error: file not found. grub rescue>
In an attempt to fix this problem, I tried using the following sudo command:
     sudo mount /dev/sda5 /mnt
sda5 does not exist, I tried 4, then 3, then 2, and it worked, but that was a partition of my internal HD containing windows 7. I also typed in:
     sudo grub-install --root directory=/mnt /dev/sda
not I get the following error when I try to boot from my internal HD:
     error: no such device: 57288a24-5d12-4fb1-b27e-eb09a1f9b7c6. grub rescue>

Is there a way to get grub to boot into windows 7 again?

When I type:
     sudo fdisk -l
I receive a list of my drives and their partitions, This is my assumption as to what drive is which:
[LEFT]
     /dev/sda1 = Vista loader, for Windows 7
     /dev/sda2 = Windows 7 (At least I hope its still there.)

     /dev/sdb1 = Bootable Flash Drive.

     /dev/sdc1 = External HD.

The text from the terminal is as follows:
_____
     Disk /dev/sda: 320.1 GB, 320072933376 bytes
     255 heads, 63 sectors/track, 38913 cylinders
     Units = cylinders of 16065 * 512 = 8225280 bytes
     Sector size (logical/physical): 512 bytes / 512 bytes
     I/O size (minimum/optimal): 512 bytes / 512 bytes
     Disk identifier: 0x8da4c52c

          Device, Boot, Start, End, Blocks, Id, System.
     /dev/sda1, 1, 1355, 10877952, 27, Unknown.
     /dev/sda2 *, , 1355, 38914, 301961224, 7, HPFS/NTFS. (The commands changed this from FAT32)

     Disk /dev/sda: 8054 MB, 8054636032 bytes
     8 heads, 32 sectors/track, 61451 cylinders
     Units = cylinders of 256 * 512 = 131072 bytes
     Sector size (logical/physical): 512 bytes / 512 bytes
     I/O size (minimum/optimal): 512 bytes / 512 bytes
     Disk identifier:0x00000000

          Device, Boot, Start, End, Blocks, Id, System.
     /dev/sdb1, *, 1, 61452, 7865839+, b, W95 FAT32.

     Disk /dev/sda: 250.1 GB, 250059350016 bytes
      255 heads, 63 sectors/track, 30401 cylinders
      Units = cylinders of 16065 * 512 =8225280 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes
      Disk identifier:0x0000a613a

          Device, Boot, Start, End, Blocks, Id, System.
     /dev/sdc1, *, 1, 30402, 244197376, 83, Linux.
_____

Eventually I would like to fix the error I get when I boot from the external, I would like to to boot to ubuntu, but for now I am concerned with getting my internal HD to boot windows 7. Thanks for reading about my problems, I would appreciate any knowledge or help anyone would be. I have been searching the forums here, which is where I originally found the terminal commands to begin with. I think sda5 is where linux was installed in the example I found, and didn't realize it.
[/LEFT]

---

### Post by drs305 on 2010-09-30
bosco88, Welcome to the Ubuntu forums.  :-)

Please run *meierfra's* boot info script. It will give us the information we need to see how your system is set up and how to make Grub behave as you wish.

[_http://bootinfoscript.sourceforge.net/_]("http://bootinfoscript.sourceforge.net/")

Copy the contents into a new post, highlight it, then press the # icon in the post's menubar to put it between 'code' tags.

---

### Post by bosco88 on 2010-09-30
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    21,757,951    21,755,904  27 Hidden HPFS/NTFS
/dev/sda2    *     21,757,952   625,140,399   603,382,448   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8054 MB, 8054636032 bytes
8 heads, 32 sectors/track, 61451 cylinders, total 15731711 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32    15,731,710    15,731,679   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048   488,396,799   488,394,752  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        E06A7B896A7B5AEC                       ntfs       Recovery                      
/dev/sda2        E6AA0188AA015709                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3464-21A3                              vfat       ELAWRENCE7                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        57288a24-5d12-4fb1-b27e-eb09a1f9b7c6   ext3                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/57288a24-5d12-4fb1-b27e-eb09a1f9b7c6 ext3       (rw,nosuid,nodev,uhelper=udisks)


=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 57288a24-5d12-4fb1-b27e-eb09a1f9b7c6
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 57288a24-5d12-4fb1-b27e-eb09a1f9b7c6
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 57288a24-5d12-4fb1-b27e-eb09a1f9b7c6
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=57288a24-5d12-4fb1-b27e-eb09a1f9b7c6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 57288a24-5d12-4fb1-b27e-eb09a1f9b7c6
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=57288a24-5d12-4fb1-b27e-eb09a1f9b7c6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 57288a24-5d12-4fb1-b27e-eb09a1f9b7c6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 57288a24-5d12-4fb1-b27e-eb09a1f9b7c6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e06a7b896a7b5aec
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e6aa0188aa015709
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext3    errors=remount-ro 0       1

=================== sdc1: Location of files loaded by Grub: ===================


 137.4GB: boot/grub/core.img
 137.5GB: boot/grub/grub.cfg
 137.4GB: boot/initrd.img-2.6.32-24-generic
 137.5GB: boot/vmlinuz-2.6.32-24-generic
 137.4GB: initrd.img
 137.5GB: vmlinuz
```

---

### Post by psusi on 2010-09-30
You should have stopped when you realized you had the windows partition mounted instead of the Ubuntu one.  You need to repeat that process but use sdc1 instead of sda1.  That will install grub on the external drive.  Then you should be able to direct your bios to boot from the external drive and load Ubuntu.  To get windows working again, you will need to boot the windows install cd, go to the recovery console, and run the FIXMBR command.

---

### Post by oldfred on 2010-09-30
To be able to boot windows when the external is not installed you want the widnows boot loader in the MBR of sda. You want grub in the MBR of sdc. And the BIOS set to boot the external first so you can boot either windows or Ubuntu when the external is plugged in. 

The USB 8GB flash becoming becoming sdb may confuse grub. I had that issue and had to use e on the menu and change the settings slightly sometimes.

You also have a window issue in sda2 as you have a grub directory inside windows. Windows does not know the difference between capitals and small letters where linux does. You need to delete the /boot/grub folder and be sure not to modify the /Boot folder as that has the windows BCD.

```
    Boot files/dirs:   /bootmgr [COLOR=Red]/Boot/BCD[/COLOR] /Windows/System32/winload.exe 
                      [COLOR=Red] /boot/grub/core.img[/COLOR]

```

---

### Post by bosco88 on 2010-09-30
> **oldfred said:**
> To be able to boot windows when the external is not installed you want the widnows boot loader in the MBR of sda. You want grub in the MBR of sdc. And the BIOS set to boot the external first so you can boot either windows or Ubuntu when the external is plugged in. 

The USB 8GB flash becoming becoming sdb may confuse grub. I had that issue and had to use e on the menu and change the settings slightly sometimes.

You also have a window issue in sda2 as you have a grub directory inside windows. Windows does not know the difference between capitals and small letters where linux does. You need to delete the /boot/grub folder and be sure not to modify the /Boot folder as that has the windows BCD.

```
    Boot files/dirs:   /bootmgr [COLOR=Red]/Boot/BCD[/COLOR] /Windows/System32/winload.exe 
                      [COLOR=Red] /boot/grub/core.img[/COLOR]

```

ok, so I need the windows boot loader in the MBR of sda. I need grub in the MBR of sdc. I have the BIOS already set to run from an external drive if present. The purpose of the USB is to boot into ubuntu, I would otherwise only use it to transfer files (It wont be in on a regular startup). So, If I delete /boot/grub folder from sda, MBR will revert back to what it is suppose to be?

Also, I am confused about your code, what do I do with it. I don't want to make the mistake of modifying the /boot folder. Can you explain how to delete the /boot/grub folder from sda?

---

### Post by psusi on 2010-09-30
No, to put the windows MBR back you need to run the FIXMBR command from the windows recovery console.  You should delete the files in boot/grub since they don't belong there since you don't want grub on that disk.  Of course, they don't hurt anything other than wasting some space.

---

### Post by oldfred on 2010-09-30
I saved these windows repair instructions:

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

More info on /Boot vs. /boot. If really concerned change /boot to something else before deleting. Use liveCd to edit.
Also check for /boot/grub in addition to /Boot 
Since ntfs partitions are case insensitive this leads to confusions between "/boot" and the already existing folder "/Boot" 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

---

### Post by bosco88 on 2010-09-30
excellent resources, I feel they are very elementary, and the pictures help to. I need to find the upgrade disk I got to upgrade from vista to windows 7, thats what I used. This disk will work correct? If tonight I am able to find my girlfriends windows 7 upgrade disk, am I able to use that? Do I need my own?

I am excited to try this, Thank you for helping me oldfred and psusi, and thanks also to drs305. When I try the disk out, I will post what happens and label it as SOLVED if all goes well. Wish me luck, thanks again!

---

### Post by oldfred on 2010-09-30
Often the recovery disk from the computer vendor just erases the drive and reimages it as the day you purchased it.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by bosco88 on 2010-09-30
oldfred this is amazing, I am glad I explained what I was going to do before I did it, because this is exactly what I need. I tried both the upgrade disks I have available. The article speaks the truth " it's damn-decent of Microsoft to make this available to Windows' users  who might not be capable of creating such a thing on their own." I do appreciate this. I will let you know how this goes when I try.

---

### Post by bosco88 on 2010-10-02
Each of the examples oldfred gives assume I am able to choose an operating system from the get go. However, I do not have an operating system to choose, it is blank. There is an option to load a driver, I attempted to use the driver from this link:
 
[http://esupport.sony.com/US/perl/swu-download.pl?mdl=VGNFW465J&upd_id=3666&os_id=34](http://esupport.sony.com/US/perl/swu-download.pl?mdl=VGNFW465J&upd_id=3666&os_id=34)
 
Called INDOTH-15336800-64.EXE (Intel® SATA Non-RAID Driver)
 
I am using a Sony VAIO computer, so I typed in my model number on Sony's site and found the Hard Disk Driver, like it asks for. I am asuming thats what I downloaded above.
 
When I try to use this driver it gives the message "The specified location does not containinformation about your hardware."
 
Regardless of this, I have been attempting to run the commands oldfred gave me. The process takes a little over an hour, specifically, 'ChkDsk C: /r /f' takes a little over an hour.
 
The last command I run, 'BootRec.exe /RebuildBcd' asks me:
 
"Add installation to Boot list?" Yes, No, All?
 
When I say Yes, it says "The requested system device cannot be found."
 
Are these related problems? Any suggestions as to what I should do now?

---

### Post by oldfred on 2010-10-03
Did you delete the /boot folder, windows will remain confused as long as it sees /Boot & /boot as they are the same and impossible to create in windows.

Generally any driver from a vendors site is for windows.

---

