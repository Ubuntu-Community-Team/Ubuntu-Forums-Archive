---
title: "grub2 boot problem"
date: 2010-05-10
forum: General Help
---

### Post by raxvan on 2010-05-10
Hello,
I have updated to ubuntu 10 and with it the new version of grub.
My windows is not booting up , when i select windows xp from the menu i get a black screen and nothing ever happens, no errors , no mesages.
I found this problem a lot on the internet but i no solution yet.

Please help , i'm in urgent need of windows.


Thanks.

---

### Post by P4man on 2010-05-10
post the output of the bootinfo script, that will help the grub experts troubleshoot your problem. How to get and run bootinfo, see here:
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by dino99 on 2010-05-10
the menu.lst and grub ( = grub1=grub-legacy) have to be removed first

try: sudo grub-mkconfig && update-grub

[http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by wilee-nilee on 2010-05-10
the suggestion by dino99 wont hurt anything, but post that boot script if it doesn't fix the problem. Paste it to a reply highlight the text and click on the # in the reply gui.

---

### Post by raxvan on 2010-05-10
I made a fresh new install of grub following the post:
[http://ubuntuforums.org/showthread.php?p=9257870#post9257870]("http://ubuntuforums.org/showthread.php?p=9261910#post9261910")
After the install i checked for menu.lst and i didn't fount it.

Now the simptoms are different:
when i select windows from the menu and press enter , grub just starts again and the menu apperars again.


Here is my boot info script:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 176660923 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 176571603 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda6 and 
                       looks at sector 176571603 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda6 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    49,158,899    49,158,837   7 HPFS/NTFS
/dev/sda2          49,158,900   312,576,704   263,417,805   f W95 Ext d (LBA)
/dev/sda5          49,158,963    53,255,474     4,096,512   7 HPFS/NTFS
/dev/sda6          53,255,538   176,136,659   122,881,122   7 HPFS/NTFS
/dev/sda7         176,136,723   306,921,824   130,785,102  83 Linux
/dev/sda8         306,921,888   312,576,704     5,654,817  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DC9CB5E99CB5BE78                       ntfs       win                           
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1A4031DD4031BFF5                       ntfs       Tiny                          
/dev/sda6        C868C6E968C6D57A                       ntfs       D1                            
/dev/sda7        5001034b-7309-42df-a831-500b77abae19   ext4                                     
/dev/sda8        ccc9f4cc-a39c-4adf-bd01-fe8a1e7ffcc2   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /media/Tiny              fuseblk    (rw,nosuid,nodev,allow_other,blksize=2048)
/dev/sda1        /media/win               fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6        /media/D1                fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
redirect=usebiossettings 
redirectbaudrate= 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer 

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 5001034b-7309-42df-a831-500b77abae19
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 5001034b-7309-42df-a831-500b77abae19
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
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 5001034b-7309-42df-a831-500b77abae19
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=5001034b-7309-42df-a831-500b77abae19 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 5001034b-7309-42df-a831-500b77abae19
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=5001034b-7309-42df-a831-500b77abae19 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 5001034b-7309-42df-a831-500b77abae19
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=5001034b-7309-42df-a831-500b77abae19 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 5001034b-7309-42df-a831-500b77abae19
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=5001034b-7309-42df-a831-500b77abae19 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 5001034b-7309-42df-a831-500b77abae19
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 5001034b-7309-42df-a831-500b77abae19
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set dc9cb5e99cb5be78
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda7 :
UUID=5001034b-7309-42df-a831-500b77abae19 / ext4 errors=remount-ro 0 1
# Entry for /dev/sda8 :
UUID=ccc9f4cc-a39c-4adf-bd01-fe8a1e7ffcc2 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda5 /media/Tiny ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/win ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda6 /media/D1 ntfs-3g rw,suid,dev,exec,auto,user,async,locale=en_US.UTF-8 0 0

=================== sda7: Location of files loaded by Grub: ===================


  90.4GB: boot/grub/core.img
  93.5GB: boot/grub/grub.cfg
 117.0GB: boot/initrd.img-2.6.31-21-generic
 127.6GB: boot/initrd.img-2.6.32-22-generic
 143.9GB: boot/vmlinuz-2.6.31-21-generic
 102.6GB: boot/vmlinuz-2.6.32-22-generic
 127.6GB: initrd.img
 117.0GB: initrd.img.old
 102.6GB: vmlinuz
 143.9GB: vmlinuz.old

```

---

### Post by dino99 on 2010-05-10
as you can see:

/dev/sda1    *             63    49,158,899    49,158,837   7 HPFS/NTFS
/dev/sda2          49,158,900   312,576,704   263,417,805   f W95 Ext d (LBA)
/dev/sda5          49,158,963    53,255,474     4,096,512   7 HPFS/NTFS
/dev/sda6          53,255,538   176,136,659   122,881,122   7 HPFS/NTFS
/dev/sda7         176,136,723   306,921,824   130,785,102  83 Linux
/dev/sda8         306,921,888   312,576,704     5,654,817  82 Linux swap / Solaris

sda1 is bootable but not sda7, so my post #3 was giving the way to follow, dont complaint because you have chosen something else

---

### Post by raxvan on 2010-05-10
sorry o forgot to mention , i also tried
```

sudo grub-mkconfig 
sudo update-grub

```
still the same rezult.

---

### Post by wilee-nilee on 2010-05-10
> **dino99 said:**
> as you can see:

/dev/sda1    *             63    49,158,899    49,158,837   7 HPFS/NTFS
/dev/sda2          49,158,900   312,576,704   263,417,805   f W95 Ext d (LBA)
/dev/sda5          49,158,963    53,255,474     4,096,512   7 HPFS/NTFS
/dev/sda6          53,255,538   176,136,659   122,881,122   7 HPFS/NTFS
/dev/sda7         176,136,723   306,921,824   130,785,102  83 Linux
/dev/sda8         306,921,888   312,576,704     5,654,817  82 Linux swap / Solaris

sda1 is bootable but not sda7, so my post #3 was giving the way to follow, dont complaint because you have chosen something else

Do you not see grub in the ntfs partition? ;) Grub is getting thrown off by this I suspect.

Op I think that you should wait for some advise by the great helpers on the forum I suspect a testdisc solution will fix this but just wait for more help.

---

### Post by oldfred on 2010-05-10
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You can also use windows cd/dvd to repair with fixboot command. Instructions are slightly different for XP and vista/7 but you want to get into the repair console and go to command line. If you also run fixmbr you will be able to directly boot windows, but will have to reinstall grub or grub2 to the MBR or drives Master Boot Record to boot Ubuntu.

XP:
FIXBOOT C:

Vista/7
BootRec.exe /FixBoot #updates PBR or partition boot sector

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Boot flag is used by windows and is not used by Ubuntu/grub. Some BIOS require a boot flag (active partition as they assume windows) on a primary partition.

---

