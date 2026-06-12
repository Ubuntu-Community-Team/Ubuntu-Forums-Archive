---
title: "Possible issue with GRUB"
date: 2010-05-03
forum: General Help
---

### Post by samhippie on 2010-05-03
I dual-boot Windows 7 and Ubuntu. Sometime between 4/18 and a few days ago, something happened with Windows booting up. Ubuntu boots fine, but whenever I try to boot Windows, it just goes to a black screen with a blinking cursor (the command line kind, not a pointer). At first I thought it was Windows, but I have run the repair CD and executed chkdsk /f and chkdsk /r on all partition related to windows. No effect. I ran a system check designed for issues with booting up, and it found no errors. I have looked at my GRUB files, and they all look fine. I am not sure if it is GRUB or Windows. I tried reinstalling the Windows boot-loader, and it had the same effect, the only difference is that it bypassed GRUB. The reason I think it may be GRUB is that the error happened around the same time as me upgrading from Karmic to the Lucid RC. I have posted this on a Windows 7 forum.

---

### Post by itiswhatitis on 2010-05-03
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

The link has instructions for fixing the blinking cursor.

---

### Post by samhippie on 2010-05-04
It didn't work. When I get the blinking cursor, it doesn't reboot; it just stays there. I tried it anyway. When I got to the sixth screen, there was no "BackupBS" tab.

---

### Post by john newbuntu on 2010-05-04
I am assuming that you normally use grub2 for dual booting.  You need to fix windows first.  Once you get that to work, you can re-install grub to the MBR using Ubuntu liveCD.
To fix win-7, have you tried "system repair" and run bootsect or bootrec commands to fix boot partition as well as MBR?  If not, take a look at this:
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Once you win-7 works properly, you will lose grub.  Then follow step 13 from drs305's post to restore grub2 to MBR:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by samhippie on 2010-05-04
> **john newbuntu said:**
> I am assuming that you normally use grub2 for dual booting.  You need to fix windows first.  Once you get that to work, you can re-install grub to the MBR using Ubuntu liveCD.
To fix win-7, have you tried "system repair" and run bootsect or bootrec commands to fix boot partition as well as MBR?  If not, take a look at this:
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Once you win-7 works properly, you will lose grub.  Then follow step 13 from drs305's post to restore grub2 to MBR:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
I have tried something similar, but I will try this.

---

### Post by samhippie on 2010-05-04
It failed. It had the same result as before, but it didn't show the GRUB menu.

---

### Post by samhippie on 2010-05-04
If Windows looks like it's fine, and GRUB looks like it's fine, then it might be my hardware. Could my firmware or BIOS have anything to do with it?
EDIT: I checked to see if there have been any recent updates to my computer (sony vaio) and all of them were before I started having problems.

---

### Post by samhippie on 2010-05-09
Here is a bump. I didn't want this to be just a boring bump, so I attached a copy of my grub.cfg as grub.txt, just in case it is the problem.

---

### Post by samhippie on 2010-05-09
I really hate to do another post, but I just found out a really important piece of information: when I am on the blinking cursor screen, it is still on the BIOS. I know this because I tried pressing ctrl+alt+del and it restarted my computer, which is something only my BIOS does.

---

### Post by samhippie on 2010-05-13
Bump :(

---

### Post by oldfred on 2010-05-13
Post this so we can see if something looks out of place. Besides the testdisk did you run any of the windows repairs?

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by samhippie on 2010-05-14
I've used some of the repair options from a windows repair disk (not installation disk). Bootsect, bootrec, etc.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

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
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 499320215 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 499320343 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

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

/dev/sda1                  63    16,530,884    16,530,822  27 Hidden HPFS/NTFS
/dev/sda2    *     16,530,885    16,739,729       208,845   7 HPFS/NTFS
/dev/sda3          16,781,312   323,500,904   306,719,593   7 HPFS/NTFS
/dev/sda4         323,500,905   625,137,344   301,636,440   5 Extended
/dev/sda5         323,500,968   619,900,154   296,399,187  83 Linux
/dev/sda6         619,900,218   625,137,344     5,237,127  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mmcblk0p1   1E8A-0FDD                              vfat                                     
/dev/sda1        645A82075A81D5E8                       ntfs       Recovery                      
/dev/sda2        0AEA5BF7EA5BDE0F                       ntfs       System Reserved               
/dev/sda3        D0346018346003B6                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        a520357d-4f27-4123-930a-8e67ae80687a   ext4                                     
/dev/sda6        08276287-aec2-41e0-ad36-b79b22e30cc6   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/mmcblk0p1   /media/1E8A-0FDD         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


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
search --no-floppy --fs-uuid --set a520357d-4f27-4123-930a-8e67ae80687a
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
search --no-floppy --fs-uuid --set a520357d-4f27-4123-930a-8e67ae80687a
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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set a520357d-4f27-4123-930a-8e67ae80687a
insmod png
if background_image /usr/share/images/desktop-base/ubuntustudio-olis.png ; then
  set color_normal=black/black
  set color_highlight=light-gray/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a520357d-4f27-4123-930a-8e67ae80687a
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=a520357d-4f27-4123-930a-8e67ae80687a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a520357d-4f27-4123-930a-8e67ae80687a
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=a520357d-4f27-4123-930a-8e67ae80687a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a520357d-4f27-4123-930a-8e67ae80687a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a520357d-4f27-4123-930a-8e67ae80687a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 645a82075a81d5e8
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0aea5bf7ea5bde0f
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
UUID=a520357d-4f27-4123-930a-8e67ae80687a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=08276287-aec2-41e0-ad36-b79b22e30cc6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 165.7GB: boot/grub/core.img
 169.1GB: boot/grub/grub.cfg
 190.5GB: boot/initrd.img-2.6.32-22-generic
 217.3GB: boot/vmlinuz-2.6.32-22-generic
 190.5GB: initrd.img
 217.3GB: vmlinuz
```

---

### Post by oldfred on 2010-05-14
It looks like you must have repaired sda2 which is your boot partition but not sda3 which is your main partition. First try running test disk on the sda3 partition.

---

### Post by samhippie on 2010-05-15
I ran testdisk, and then I repaired it with the Windows 7 repair disk. Still doesn't boot, but it changed my boot_info_script results file.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

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
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 499320343 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

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

/dev/sda1                  63    16,530,884    16,530,822  27 Hidden HPFS/NTFS
/dev/sda2    *     16,530,885    16,739,729       208,845   7 HPFS/NTFS
/dev/sda3          16,781,312   323,500,904   306,719,593   7 HPFS/NTFS
/dev/sda4         323,500,905   625,137,344   301,636,440   5 Extended
/dev/sda5         323,500,968   619,900,154   296,399,187  83 Linux
/dev/sda6         619,900,218   625,137,344     5,237,127  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mmcblk0p1   1E8A-0FDD                              vfat                                     
/dev/sda1        645A82075A81D5E8                       ntfs       Recovery                      
/dev/sda2        0AEA5BF7EA5BDE0F                       ntfs       System Reserved               
/dev/sda3        D0346018346003B6                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        a520357d-4f27-4123-930a-8e67ae80687a   ext4                                     
/dev/sda6        08276287-aec2-41e0-ad36-b79b22e30cc6   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/mmcblk0p1   /media/1E8A-0FDD         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


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
search --no-floppy --fs-uuid --set a520357d-4f27-4123-930a-8e67ae80687a
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
search --no-floppy --fs-uuid --set a520357d-4f27-4123-930a-8e67ae80687a
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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set a520357d-4f27-4123-930a-8e67ae80687a
insmod png
if background_image /usr/share/images/desktop-base/ubuntustudio-olis.png ; then
  set color_normal=black/black
  set color_highlight=light-gray/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a520357d-4f27-4123-930a-8e67ae80687a
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=a520357d-4f27-4123-930a-8e67ae80687a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a520357d-4f27-4123-930a-8e67ae80687a
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=a520357d-4f27-4123-930a-8e67ae80687a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a520357d-4f27-4123-930a-8e67ae80687a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a520357d-4f27-4123-930a-8e67ae80687a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 645a82075a81d5e8
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0aea5bf7ea5bde0f
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
UUID=a520357d-4f27-4123-930a-8e67ae80687a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=08276287-aec2-41e0-ad36-b79b22e30cc6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 166.1GB: boot/grub/core.img
 170.7GB: boot/grub/grub.cfg
 190.5GB: boot/initrd.img-2.6.32-22-generic
 217.3GB: boot/vmlinuz-2.6.32-22-generic
 190.5GB: initrd.img
 217.3GB: vmlinuz
```

---

### Post by oldfred on 2010-05-15
Now it looks correct, but you still cannot boot? I would run the entire set of windows commands to repair and even set windows to boot from the MBR. You then can reinstall grub2 after you get windows to work. Grub will only boot working windows. It seems that windows 7 has more trouble repairing the versions with the separate boot partition.

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

Some advanced BCD rebuild, Vista/7:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)

to reinstall grub2:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Install from LiveCD:
Find linux partition:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by samhippie on 2010-05-15
> **oldfred said:**
> Now it looks correct, but you still cannot boot? I would run the entire set of windows commands to repair and even set windows to boot from the MBR. You then can reinstall grub2 after you get windows to work. Grub will only boot working windows. It seems that windows 7 has more trouble repairing the versions with the separate boot partition.I tried running what you said, but it did not fix my problem; however, it did something unexpected. After "bootrec.exe /scanos" and "bootrec.exe /rebuildbcd" it stated "Total identified Windows installations: 0" as part of the result.

---

### Post by louieb on 2010-05-15
Did you install Ubuntu over another Windows install? MS has a weird way of setting up multi - boot. only one of the installs gets a boot loader. 

Seems your Win7 install is missing  one or more of these 3 files. 
 [COLOR=Red]/bootmgr /Boot/BCD /Windows/System32/winload.exe[/COLOR]

Also not sure which partition holds windows sda1, sda2, and sda3 all have Win7 boot sectors.

The boot flag is on sda2 but its really small - wonder if your install is really in sda3 - my guess. 

Anyway try putting the boot flag on sda3 and try the repair oldfred suggested again.

---

### Post by samhippie on 2010-05-15
> **louieb said:**
> Did you install Ubuntu over another Windows install? MS has a weird way of setting up multi - boot. only one of the installs gets a boot loader. 

Seems your Win7 install is missing  one or more of these 3 files. 
 [COLOR=Red]/bootmgr /Boot/BCD /Windows/System32/winload.exe[/COLOR]

Also not sure which partition holds windows sda1, sda2, and sda3 all have Win7 boot sectors.

The boot flag is on sda2 but its really small - wonder if your install is really in sda3 - my guess. 

Anyway try putting the boot flag on sda3 and try the repair oldfred suggested again.My computer came with Windows 7 on it. I shrunk the main partition (sda3) and installed Ubuntu. If it helps, the problem happened between 4/18 and 2/28, with me upgrading to Lucid RC on 4/22.
Sda1-3 came with my system. Sda1 is a "recovery partition". I think it was put there to compensate for not coming with an install disk. Sda2 is "system reserved". Grub boots to that partition. Sda3 is my main partition. It has my desktop, system32, things like that. 

Where would /bootmgr be? I can't find it, but I may just be looking in the wrong places.

---

### Post by oldfred on 2010-05-16
Clean installs of win7 have a 100MB boot partition your sda2 with 
/bootmgr /Boot/BCD

Then the main install has this:
 /Windows/System32/winload.exe

If installing over Vista or replacing XP in an existing NTFS partition all three files are in the same partition.

We have seen several cases where windows does not seem to repair the version with the separate /boot partition. I think one user did move the boot flag to the main partition and run repairs and it fixed it but then the /boot partition was not used. 

Besides recovery testdisk has the capability to rebuild some of the windows files.
If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by samhippie on 2010-05-16
After moving the boot flag and running all of the Windows repair commands, it still goes to the same screen. When I entered "sudo update-grub" it had two Windows 7 entries: one on sda2 and one on sda3.
After running testdisk, I selected my main Windows partition (sda3) and choose to repair MFT. I got this message: "MFT and MFT mirror are bad. Failed to repair them."
I just looked at my system reserved partition. bootmgr was in the root of the drive. Not sure if it was there before.

---

### Post by oldfred on 2010-05-16
Not looking good. Did you ever boot windows after shrinking its partition? And how did you shrink the partition? Just to know what not to do.

---

### Post by samhippie on 2010-05-16
> **oldfred said:**
> Not looking good. Did you ever boot windows after shrinking its partition? And how did you shrink the partition? Just to know what not to do.Around January I shrank my Windows partition by about sixty gigabytes with Gparted on the Karmic live cd. I installed Karmic there. Windows booted fine after that. I had no problems until April, when I noticed it wouldn't boot. I have since shrank Windows by about 80 gigabytes because I needed more space on Ubuntu, but that didn't change anything. I'll look into getting a Windows install disk to see if a reinstallation helps.
[IMG]http://img706.imageshack.us/img706/1299/051610124900.jpg[/IMG]
Quick question: Is product key on this label the activation key?

---

