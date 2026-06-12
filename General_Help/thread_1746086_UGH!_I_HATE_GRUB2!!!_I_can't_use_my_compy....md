---
title: "UGH! I HATE GRUB2!!! I can't use my compy..."
date: 2011-05-01
forum: General Help
---

### Post by squareff255 on 2011-05-01
Right now I'm using an Ubuntu 10.04 livecd. Anyway, I've installed Windows7 (I KNOW, but I need it for my video editing) and Ubuntu 10.04 and when I boot up, I get the grub command-line interface. :-/

I have 2 hard drives in my computer right now: my old one (with XP and Ubuntu 10.04 32-bit) and my new one (Windows 7 64-bit and Ubuntu 10.04 64-bit). I'm just trying to get Grub to make a menu of both hard drives combined (which it was doing last week before I wiped my new hard drive to make space for freakin' Windows 7) but I don't know how! I don't really know the inner workings of the computer's boot process. I have an OKAY understanding, but I don't know if Grub needs to be installed on a certain hard drive to map out BOTH or if it even matters which hard drive Grub's installed on. 

Okay, so when the command line interface comes up, I went exploring through the partition and discovered that I was in my new Ubuntu 10.04 64-bit OS, so I guess I can assume that Grub's root directory is /dev/sdb...? I know that the NEW hard drive is /dev/sdb. But I discovered that there is no grub.cfg ANYWHERE! So that would explain why I don't get a menu, BUT when I try to run commands like:
```
sudo update-grub2
```it just says:
```
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
```So, I've looked at this other thread: [http://ubuntuforums.org/showthread.php?p=10095234](http://ubuntuforums.org/showthread.php?p=10095234) where apparently he had the same problem, but then he doesn't say how he fixed it. He just says
```

Yeti,

I got in, thanks a bunch.

Best,

Dave

```And I tried the things he tried but I still don't have a grub.cfg file and it still keeps telling me &quot;/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).&quot; 

Anyway, CAN SOMEONE HELP ME!? 

Thanks in advance!

---

### Post by Rubi1200 on 2011-05-01
Hi,
we need to see what is going on with your setup in order to help you. So, the best advice I can give right now is to do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by squareff255 on 2011-05-01
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on boot drive #1 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   207,158,174   207,158,112   7 HPFS/NTFS
/dev/sda2         207,159,294   625,141,759   417,982,466   5 Extended
/dev/sda5         207,159,296   214,984,703     7,825,408  82 Linux swap / Solaris
/dev/sda6         214,986,752   429,828,095   214,841,344  83 Linux
/dev/sda7         429,830,144   617,107,455   187,277,312  83 Linux
/dev/sda8         617,109,504   625,141,759     8,032,256  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   836,231,444   836,024,597   7 HPFS/NTFS
/dev/sdb3         836,233,214 1,953,523,711 1,117,290,498   5 Extended
/dev/sdb5         836,233,216 1,918,439,423 1,082,206,208  83 Linux
/dev/sdb6       1,918,441,472 1,953,523,711    35,082,240  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,465,144,064 1,465,144,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4AA46907A468F6BB                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        4e4aba14-42e5-436b-a22b-1daf8e827562   swap                                     
/dev/sda6        6f7f228f-0f3f-446e-8d99-aa8e249f09bb   ext4                                     
/dev/sda7        79197049-988c-4659-9380-8e6e8885aad8   ext4                                     
/dev/sda8        f056a404-7364-40bb-8672-017708910ed9   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6A3E86E23E86A723                       ntfs       System Reserved               
/dev/sdb2        E26A89336A89060F                       ntfs                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        4127f3e2-dd2b-4168-832e-019a6538bf1c   ext4                                     
/dev/sdb6        06e480c0-86be-4ce2-bde3-cc14459b9974   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        1406D03006D01498                       ntfs                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/stage2

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 6f7f228f-0f3f-446e-8d99-aa8e249f09bb
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
search --no-floppy --fs-uuid --set 6f7f228f-0f3f-446e-8d99-aa8e249f09bb
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
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 6f7f228f-0f3f-446e-8d99-aa8e249f09bb
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=6f7f228f-0f3f-446e-8d99-aa8e249f09bb ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 6f7f228f-0f3f-446e-8d99-aa8e249f09bb
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=6f7f228f-0f3f-446e-8d99-aa8e249f09bb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 6f7f228f-0f3f-446e-8d99-aa8e249f09bb
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=6f7f228f-0f3f-446e-8d99-aa8e249f09bb ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 6f7f228f-0f3f-446e-8d99-aa8e249f09bb
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=6f7f228f-0f3f-446e-8d99-aa8e249f09bb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 6f7f228f-0f3f-446e-8d99-aa8e249f09bb
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=6f7f228f-0f3f-446e-8d99-aa8e249f09bb ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 6f7f228f-0f3f-446e-8d99-aa8e249f09bb
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=6f7f228f-0f3f-446e-8d99-aa8e249f09bb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 6f7f228f-0f3f-446e-8d99-aa8e249f09bb
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=6f7f228f-0f3f-446e-8d99-aa8e249f09bb ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 6f7f228f-0f3f-446e-8d99-aa8e249f09bb
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=6f7f228f-0f3f-446e-8d99-aa8e249f09bb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 6f7f228f-0f3f-446e-8d99-aa8e249f09bb
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6f7f228f-0f3f-446e-8d99-aa8e249f09bb ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 6f7f228f-0f3f-446e-8d99-aa8e249f09bb
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6f7f228f-0f3f-446e-8d99-aa8e249f09bb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 6f7f228f-0f3f-446e-8d99-aa8e249f09bb
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=6f7f228f-0f3f-446e-8d99-aa8e249f09bb ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 6f7f228f-0f3f-446e-8d99-aa8e249f09bb
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=6f7f228f-0f3f-446e-8d99-aa8e249f09bb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 6f7f228f-0f3f-446e-8d99-aa8e249f09bb
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=6f7f228f-0f3f-446e-8d99-aa8e249f09bb ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 6f7f228f-0f3f-446e-8d99-aa8e249f09bb
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=6f7f228f-0f3f-446e-8d99-aa8e249f09bb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 6f7f228f-0f3f-446e-8d99-aa8e249f09bb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 6f7f228f-0f3f-446e-8d99-aa8e249f09bb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4aa46907a468f6bb
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 79197049-988c-4659-9380-8e6e8885aad8
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=79197049-988c-4659-9380-8e6e8885aad8 ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 79197049-988c-4659-9380-8e6e8885aad8
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=79197049-988c-4659-9380-8e6e8885aad8 ro single
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 79197049-988c-4659-9380-8e6e8885aad8
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=79197049-988c-4659-9380-8e6e8885aad8 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 79197049-988c-4659-9380-8e6e8885aad8
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=79197049-988c-4659-9380-8e6e8885aad8 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
# Commented out by Dropbox
# UUID=6f7f228f-0f3f-446e-8d99-aa8e249f09bb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4e4aba14-42e5-436b-a22b-1daf8e827562 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=6f7f228f-0f3f-446e-8d99-aa8e249f09bb / ext4 errors=remount-ro,user_xattr 0 1

=================== sda6: Location of files loaded by Grub: ===================


 144.5GB: boot/grub/core.img
 161.7GB: boot/grub/grub.cfg
 144.5GB: boot/grub/stage2
 144.5GB: boot/initrd.img-2.6.32-21-generic
 144.7GB: boot/initrd.img-2.6.32-23-generic
 144.7GB: boot/initrd.img-2.6.32-24-generic
 144.7GB: boot/initrd.img-2.6.32-25-generic
 145.1GB: boot/initrd.img-2.6.32-26-generic
 145.1GB: boot/initrd.img-2.6.32-28-generic
 145.1GB: boot/initrd.img-2.6.32-29-generic
 110.2GB: boot/vmlinuz-2.6.32-21-generic
 144.5GB: boot/vmlinuz-2.6.32-23-generic
 144.7GB: boot/vmlinuz-2.6.32-24-generic
 144.7GB: boot/vmlinuz-2.6.32-25-generic
 145.1GB: boot/vmlinuz-2.6.32-26-generic
 145.1GB: boot/vmlinuz-2.6.32-28-generic
 144.9GB: boot/vmlinuz-2.6.32-29-generic
 145.1GB: initrd.img
 145.1GB: initrd.img.old
 144.9GB: vmlinuz
 145.1GB: vmlinuz.old

=================== sdb5: Location of files loaded by Grub: ===================


 885.7GB: boot/grub/core.img
 885.7GB: boot/initrd.img-2.6.32-28-generic
 885.6GB: boot/initrd.img-2.6.32-29-generic
 885.7GB: boot/initrd.img-2.6.32-30-generic
 885.7GB: boot/initrd.img-2.6.32-31-generic
 885.7GB: boot/vmlinuz-2.6.32-28-generic
 885.7GB: boot/vmlinuz-2.6.32-29-generic
 885.7GB: boot/vmlinuz-2.6.32-30-generic
 885.7GB: boot/vmlinuz-2.6.32-31-generic
 885.7GB: initrd.img
 885.7GB: initrd.img.old
 885.7GB: vmlinuz
 885.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  63 f2 6e 7a b7 67 be 6c  cc b9 15 bc cc 71 b0 a6  |c.nz.g.l.....q..|
00000010  ff b2 11 d1 b9 ee e1 64  88 df ce a0 05 a0 80 0a  |.......d........|
00000020  40 05 c0 0c 55 fd 0a 00  38 e6 fe c4 50 e5 01 51  |@...U...8...P..Q|
00000030  cd f6 f0 07 a0 80 0c 60  0e fe 8a ff a7 6e 23 b8  |.......`.....n#.|
00000040  b2 a8 73 c0 b6 da 0b 43  f2 c6 9f 2d 8d 45 f7 a0  |..s....C...-.E..|
00000050  40 02 b1 2e 00 7c 00 df  e0 5e c5 c7 73 96 c0 c5  |@....|...^..s...|
00000060  6f e6 18 20 01 58 03 72  30 03 90 06 5f 02 7e 2e  |o.. .X.r0..._.~.|
00000070  18 4e 86 a0 ca 83 5b fa  2c 00 ec 10 00 ec 00 b4  |.N....[.,.......|
00000080  01 80 b4 e4 01 97 d7 0c  a4 d9 d3 ec f1 91 be 14  |................|
00000090  08 00 a8 08 1f 9e 00 f4  01 96 00 09 3d dd de 4d  |............=..M|
000000a0  89 3c f3 64 85 1c 5b 71  71 ef c0 be ae 47 c8 8d  |.<.d..[qq....G..|
000000b0  cf d3 cc 3d a8 ff 32 80  3b fb a8 18 ca 83 db a7  |...=..2.;.......|
000000c0  ec e7 08 c0 03 fe ea 64  39 46 d6 d3 fe e9 e4 5a  |.......d9F.....Z|
000000d0  41 d5 32 17 68 43 74 80  1b f1 fd 00 73 a4 e1 1d  |A.2.hCt.....s...|
000000e0  3e 75 95 07 2b 54 83 d8  55 b5 a8 be 9c 08 1f 90  |>u..+T..U.......|
000000f0  00 b6 80 2d 12 f9 0a e3  15 1b ea 90 8d 9b dc 91  |...-............|
00000100  be 24 45 04 00 4c 00 46  45 96 bb a4 be ad 84 01  |.$E..L.FE.......|
00000110  50 20 03 48 03 7d d9 bf  71 79 d6 0e 87 b1 23 8a  |P .H.}..qy....#.|
00000120  43 db b3 5d 76 d6 a3 fa  db bf 82 92 2c b6 84 37  |C..]v.......,..7|
00000130  8f 00 70 08 00 55 f7 00  72 57 5c 57 71 46 e9 4d  |..p..U..rW\WqF.M|
00000140  f9 c0 01 d0 20 01 60 03  cf f2 5a e9 de cf de b7  |.... .`...Z.....|
00000150  83 76 71 c4 4c c9 81 0d  94 d6 cb 3a 53 da 8b f4  |.vq.L......:S...|
00000160  4f b0 20 03 e7 db 9e 81  0b fd be e4 ee c0 05 05  |O. .............|
00000170  c5 6f 60 00 46 08 00 7a  20 10 00 b3 2f 5d 72 01  |.o`.F..z .../]r.|
00000180  5c 7f ee c2 ce 6f c8 fa  fc b5 bd 48 01 88 01 60  |\....o.....H...`|
00000190  03 e0 04 f9 40 0f e9 33  8a 8d d0 f7 68 7a 34 72  |....@..3....hz4r|
000001a0  44 9e 47 35 1f f4 28 01  af 11 ca 31 be d1 f7 10  |D.G5..(....1....|
000001b0  4f e5 69 71 bf 3d 80 10  ff 28 01 bf 3e c2 00 fe  |O.iq.=...(..>...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 68 77 00 00 fe  |...........hw...|
000001d0  ff ff 05 fe ff ff 02 68  77 00 00 40 ce 0c 00 00  |.......hw..@....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

Thanks. :)

---

### Post by oldfred on 2011-05-01
Your install in sdb5 does not look complete and then the grub2 cannot boot as there is no  grub.cfg nor fstab. Not sure if you can chroot into it and complete it or what happened.

Your install in sda6 looks ok, but has no menu.lst but you have grub legacy in the MBR. It looks like it had grub2, but you tried some old instructions on repairs and installed grub legacy.

It may work just to install grub2 to the MBR of sda to use sda6.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda6 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda6 if not correct:
sudo fdisk -l
#confirm that linux is sda6
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

That should find the windows installs.

---

### Post by squareff255 on 2011-05-01
Your install in sdb5 does not look complete and then the grub2 cannot boot as there is no grub.cfg nor fstab. Not sure if you can chroot into it and complete it or what happened.

Your install in sda6 looks ok, but has no menu.lst but you have grub legacy in the MBR. It looks like it had grub2, but you tried some old instructions on repairs and installed grub legacy.

It may work just to install grub2 to the MBR of sda to use sda6.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Gr...ing%20GRUB%202](https://help.ubuntu.com/community/Gr...ing%20GRUB%202)

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda6 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda6 if not correct:
sudo fdisk -l
#confirm that linux is sda6
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

That should find the windows installs.


Okay! So, I followed your link ```
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
http://ubuntuforums.org/showthread.php?t=1014708
``` and did what it said and when I rebooted I got a menu! Exciting, however, it was my OLD menu, so I could access my old ubuntu partition and my windows xp, SO, I loaded my old ubuntu and then from the terminal, I installed grub2 and ran ```
sudo update-grub2
``` and it said THIS:
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-29-generic
Found initrd image: /boot/initrd.img-2.6.32-29-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
Found Windows 7 (loader) on /dev/sdb1
Found Debian GNU/Linux () on /dev/sdb5
done

```
Exciting! So I thought I had done it, but when I rebooted, it was still my old menu... I just looked at the grub.cfg file and I found windows 7 and everything, but it still presents me with the old menu... I'm so confused... :-/

---

### Post by squareff255 on 2011-05-01
SOOOOOOO, new update. I was on my grub menu (which is still my OLD one with my old ubuntu partition and windows xp) and I pressed "c" to go to command-line interface. Then I typed ```
configfile /boot/grub/grub.cfg
```and it went to the new menu! So I tried Windows 7 and it works! My new ubuntu partition, however, does not. When I select it, it simply loads my old one... weird, because it says "/dev/sdb5" next to it, and my old one is /dev/sda6. Anyway, so I guess I'll have to reinstall or something unless someone knows how to fix that... but right now I'd like to know if anyone knows why whenever I reboot, it reverts to the old menu and why I have to go to the CLI and type ```
configfile /boot/grub/grub.cfg
```to get the new one... :-/

---

### Post by oldfred on 2011-05-01
Because you had old grub & grub2 mixed up, it it updating old grub's menu.lst but booting grub2 or vice versa?

Best to uninstall both grub & grub2 and cleanly reinstall just grub2. Note that while both are deleted you cannot reboot and you need working Internet to reinstall grub2.

See notes in instructions on skipping chroot part.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

You may be able to chroot into your other install in sdb5 (from your sda6 install, liveCD not required) and repair it. But I do not know if repairs will recreate fstab which looks like it is missing. If that is all that is missing we can rebuild one.

Use chroot from above grub instructions and then run these updates:

#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

You may also want to houseclean kernels so menus are not so long. We normally suggest keeping current & one older one that works just in case.

Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
HOWTO: Remove Older Kernels via GUI Tweak
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)
A easy way to remove the amount of kernels is to install Ubuntu tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

