---
title: "Target filesystem doesn't have /sbin/init"
date: 2011-09-01
forum: General Help
---

### Post by ShwetaRuhela on 2011-09-01
Hi,

I am working in Ubuntu 10.04 LTS.
Due to some bad command my file system has corrupted.

Now i am getting screen while booting as...

Target filesystems doesn't have /sbin/init
run-init: /etc/init: Permission denied
[ 1.356276] kernel panic - not syncing Attempted to kill init!

Now I tried to use USB drive with Ubuntu version 10.10 Marv as live CD.
Followed commands...

>fdisk -l
>sudo e2fsck -f -y -v /dev/sda5 
  
/dev/sda5 is device file for linux partition in my system.

But this doesn't solve my purpose.

Plz help me what should i do?

I have also run the command to upgrade GRUB2 as...

>sudo mount /dev/sda5 /mnt
>sudo grub_install --root-directory=/mnt /dev/sda

then reboot the system

Help me how i can recover my ubuntu 10.04?

Regards,
Shweta

---

### Post by Rubi1200 on 2011-09-02
Hi and welcome to the forums :-)

Please post the results of the boot info script so we can get a better idea of what is happening.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by ShwetaRuhela on 2011-09-03
```

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for (,msdos5)/boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  _____ _____ _ _ | _ |___ ___ 
                       ___ ___ | _ |___ ___ |_|___ ___| |_ | | _| .'| . | . | 
                       | __| _| . | | | -_| _| _| |__|__|_| |__,|_ |___| |__| 
                       |_| |___|_| |___|___|_| |___| |___| Arago Project 
                       [http://arago-project.org](http://arago-project.org) Arago 2010.12
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>..............0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1423512 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   245,759,999   245,553,152   7 NTFS / exFAT / HPFS
/dev/sda3         245,760,000   293,686,697    47,926,698   7 NTFS / exFAT / HPFS
/dev/sda4         293,687,294   488,396,799   194,709,506   5 Extended
/dev/sda5         293,687,296   480,387,071   186,699,776  83 Linux
/dev/sda6         480,389,120   488,396,799     8,007,680  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4041 MB, 4041211904 bytes
125 heads, 62 sectors/track, 1018 cylinders, total 7892992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     7,889,499     7,889,438   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       4840a680-d672-4cb9-b44d-c1f5bbd9bbb3   ext3       
/dev/sda1        D6B29EBAB29E9F15                       ntfs       System Reserved
/dev/sda2        3010A4AC10A47A8C                       ntfs       
/dev/sda3        C26698B56698ABA3                       ntfs       
/dev/sda5        eefffb30-61c0-4a14-ad69-6b564f2b10d8   ext4       
/dev/sda6        5eb25b51-183f-4eff-88a8-e354c3eb982a   swap       
/dev/sdb1        7FF4-9F9B                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
search --no-floppy --fs-uuid --set eefffb30-61c0-4a14-ad69-6b564f2b10d8
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
search --no-floppy --fs-uuid --set eefffb30-61c0-4a14-ad69-6b564f2b10d8
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set eefffb30-61c0-4a14-ad69-6b564f2b10d8
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=eefffb30-61c0-4a14-ad69-6b564f2b10d8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set eefffb30-61c0-4a14-ad69-6b564f2b10d8
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=eefffb30-61c0-4a14-ad69-6b564f2b10d8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set eefffb30-61c0-4a14-ad69-6b564f2b10d8
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=eefffb30-61c0-4a14-ad69-6b564f2b10d8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set eefffb30-61c0-4a14-ad69-6b564f2b10d8
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=eefffb30-61c0-4a14-ad69-6b564f2b10d8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set eefffb30-61c0-4a14-ad69-6b564f2b10d8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set eefffb30-61c0-4a14-ad69-6b564f2b10d8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d6b29ebab29e9f15
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# stock fstab - you probably want to override this with a machine specific one

rootfs               /                    auto       defaults              1  1
proc                 /proc                proc       defaults              0  0
devpts               /dev/pts             devpts     mode=0620,gid=5       0  0
usbfs                /proc/bus/usb        usbfs      defaults              0  0
tmpfs                /var/volatile        tmpfs      defaults,size=16M     0  0
tmpfs                /dev/shm             tmpfs      mode=0777             0  0
tmpfs                /media/ram           tmpfs      defaults,size=16M     0  0

# uncomment this if your device has a SD/MMC/Transflash slot
#/dev/mmcblk0p1       /media/card          auto       defaults,sync,noauto  0  0

--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 190.185783386 = 204.210429952  boot/grub/core.img                             1
 142.274677277 = 152.766271488  boot/grub/grub.cfg                             2
 190.193279266 = 204.218478592  boot/initrd.img-2.6.32-21-generic              1
 190.298431396 = 204.331384832  boot/initrd.img-2.6.32-26-generic              1
 190.172206879 = 204.195852288  boot/vmlinuz-2.6.32-21-generic                 1
 190.197040558 = 204.222517248  boot/vmlinuz-2.6.32-26-generic                 1
 190.298431396 = 204.331384832  initrd.img                                     1
 190.193279266 = 204.218478592  initrd.img.old                                 1
 190.197040558 = 204.222517248  vmlinuz                                        1
 190.172206879 = 204.195852288  vmlinuz.old                                    1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v3.xx)

====================================================================================
Thanks for reply

Wish you to have clue for what cause problem "Kernel Panic"

Regards,
Shweta

---

### Post by ShwetaRuhela on 2011-09-03
Hi,

Via Live USB boot option i observe that /sbin/init file properties showing type broken with file size 0.

What i can do next to restore /sbin/init.

Plz guide me

Regards,
Shweta

---

### Post by Rubi1200 on 2011-09-03
Hi.
according to the results of the script you have something called arago installed on sda5?

I don't see where Ubuntu 10.04 is located.

Please provide more information.

Thanks.

---

### Post by ShwetaRuhela on 2011-09-05
Hi,

Yes right!

I was working on TI OMAP3 SDK thats why Arago has taken place of Ubuntu by mistake.

Output screen of ubuntu version commands...
------------------------------------------------------------------------------------------
>cat /etc/lab_release

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

--------------------------------------------------------------------------------------------
>cat /etc/issue

|  _  |___ ___ ___ ___   |  _  |___ ___  |_|___ ___| |_ 
|     |  _| .'| . | . |  |   __|  _| . | | | -_|  _|  _|
|__|__|_| |__,|_  |___|  |__|  |_| |___|_| |___|___|_|  
              |___|                    |___|            

Arago Project [http://arago-project.org](http://arago-project.org) \n \l

Arago 2010.12 \n \l

-----------------------------------------------------------------------------------------------

Now help me how i can restore ubuntu 10.04.1 LTS

Thanks

Regards,
Shweta

---

### Post by ShwetaRuhela on 2011-09-07
Can anybody help me for my running problem?

I wish to have some trick i can play with to recover my Ubuntu 10.04 LTS 
from this "General Help" discussion forum.

Thank you

Regards,
Shweta

---

