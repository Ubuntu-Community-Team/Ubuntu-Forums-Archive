---
title: "problem while installing openSUSE in a quadboot system"
date: 2010-12-29
forum: General Help
---

### Post by rockager on 2010-12-29
i'm trying to install openSUSE along with kubuntu 10.04, fedora 14 and windows 7
i'm at the final stage of installation where the graphical installer is showing the final installation values:
it seems that the openSUSE installer cannot see kubuntu (see values highlighted with red)
How do i add the kubuntu option to it ?( it is located in /dev/sda6)
(the installer has an option to edit the sections)

System
&#8226; Processor: 2x Intel(R) Atom(TM) CPU 230 @ 1.60GHz
&#8226; Main Memory: 1,016 MB
Partitioning
&#8226; Create swap volume /dev/sda7 (1.46 GB)
&#8226; Create root volume /dev/sda8 (11.02 GB) with ext4
&#8226; Create volume /dev/sda9 (16.08 GB) for /home with ext2

Booting
&#8226; Boot Loader Type: GRUB
&#8226; Status Location: /dev/sda2 (extended), 
&#8226; Change Location: 
&#8226; Boot from MBR is disabled (enable)
&#8226; Boot from "/" partition is disabled (enable)
[COLOR=Red]&#8226; Sections:
+ openSUSE 11.3 (default)
+ Fedora (2.6.35.9-64.fc14.i686) (/dev/sda5)
+ Windows
+ Failsafe -- openSUSE 11.3
+ Hard Disk[/COLOR]

Keyboard Layout
&#8226; English (US)

Time Zone
&#8226; Asia / Kolkata - Hardware Clock Set To Local Time 2010-12-29 - 11:21:20

Default Runlevel
&#8226; 5: Full multiuser with network and display manager

---

### Post by dcstar on 2010-12-29
> **rockager said:**
> i'm trying to install openSUSE along with kubuntu 10.04, fedora 14 and windows 7
i'm at the final stage of installation where the graphical installer is showing the final installation values:
it seems that the openSUSE installer cannot see kubuntu (see values highlighted with red)
How do i add the kubuntu option to it ?( it is located in /dev/sda6)
(the installer has an option to edit the sections)
........

Just reinstall Grub and let it boot everything:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Rubi1200 on 2010-12-29
Hi rockager,
did you choose manual partitioning at the relevant stage?

I have heard from other users that there can be problems with the OpenSUSE installer recognizing certain partitions.

Therefore, I advise you to be very careful before proceeding!

---

### Post by garvinrick4 on 2010-12-29
Are you booting from grub2 or grub-legacy in Fedora. If you are booting in grub2 do not
install a grub at all in OpenSuse with the anaconda installer there is a checkmark at grub installation to not install a grub at all.
Boot into your grub2 installation after install and:
```
sudo update-grub
```It will find all your installs and put them in grub config and as menu entries.
#If you are using Fedora's grub legacy as a boot manager Open Suse has grub legacy also which it seems your
attempting to do. Post #2's link is as good as any to understand grub

---

### Post by rockager on 2010-12-29
> did you choose manual partitioning at the relevant stage?


yes, i partitioned my system manually
but it showed all the partitions.

---

### Post by rockager on 2010-12-29
resul.txt after using bot info script:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Acer 3 is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /grub.cfg /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 112394832 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #8 for 
                       /boot/grub/menu.lst.

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 14 (Laughlin) 
                       Kernel on an ()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Welcome to openSUSE 11.3 "Teal" 
                       - Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda9: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    33,559,784    33,559,722   7 HPFS/NTFS
/dev/sda2    *     33,559,846   156,360,644   122,800,799   5 Extended
/dev/sda5          33,559,848    65,015,054    31,455,207  83 Linux
/dev/sda6          65,015,118    96,470,324    31,455,207  83 Linux
/dev/sda7          96,471,040    99,538,943     3,067,904  82 Linux swap / Solaris
/dev/sda8          99,540,992   122,640,383    23,099,392  83 Linux
/dev/sda9         122,642,432   156,358,655    33,716,224  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1907D850054BE693                       ntfs                                     
/dev/sda2: PTTYPE="dos" PART_ENTRY_SCHEME="dos" PART_ENTRY_TYPE="0x5" PART_ENTRY_FLAGS="0x80" PART_ENTRY_NUMBER="2" 
/dev/sda5        22839ebc-fbf6-46fb-b021-c3afdbc89103   ext4       _Fedora-14-i686-              
/dev/sda6        2736f0c9-25d9-4a29-9b28-9afeefa2824f   ext4                                     
/dev/sda7        da2e8e82-0316-463e-b998-0ad545e3e258   swap                                     
/dev/sda8        1a33e163-b9b5-4a75-954b-c7de3450dc90   ext4                                     
/dev/sda9        4fbd89d0-6508-4d62-9905-8b13b8a930f0   ext2                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw)


================================ sda1/grub.cfg: ================================

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
search --no-floppy --fs-uuid --set a2875060-a736-42fe-9d94-d20760dbb53a
if loadfont /share/grub/unicode.pf2 ; then
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 6c863863-5d0b-4966-bee8-ea988c7556da
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
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 6c863863-5d0b-4966-bee8-ea988c7556da
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=6c863863-5d0b-4966-bee8-ea988c7556da ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 6c863863-5d0b-4966-bee8-ea988c7556da
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=6c863863-5d0b-4966-bee8-ea988c7556da ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 6c863863-5d0b-4966-bee8-ea988c7556da
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=6c863863-5d0b-4966-bee8-ea988c7556da ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 6c863863-5d0b-4966-bee8-ea988c7556da
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=6c863863-5d0b-4966-bee8-ea988c7556da ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 6c863863-5d0b-4966-bee8-ea988c7556da
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6c863863-5d0b-4966-bee8-ea988c7556da ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 6c863863-5d0b-4966-bee8-ea988c7556da
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6c863863-5d0b-4966-bee8-ea988c7556da ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 6c863863-5d0b-4966-bee8-ea988c7556da
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 6c863863-5d0b-4966-bee8-ea988c7556da
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1907d850054be693
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###

### END /etc/grub.d/40_custom ###

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: grub.cfg

========================== sda5/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,4)
#          kernel /boot/vmlinuz-version ro root=/dev/sda5
#          initrd /boot/initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,4)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.35.9-64.fc14.i686)
    root (hd0,4)
    kernel /boot/vmlinuz-2.6.35.9-64.fc14.i686 ro root=UUID=22839ebc-fbf6-46fb-b021-c3afdbc89103 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-2.6.35.9-64.fc14.i686.img
title Fedora (2.6.35.6-45.fc14.i686)
    root (hd0,4)
    kernel /boot/vmlinuz-2.6.35.6-45.fc14.i686 ro root=UUID=22839ebc-fbf6-46fb-b021-c3afdbc89103 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-2.6.35.6-45.fc14.i686.img
title Windows
    rootnoverify (hd0,0)
    chainloader +1

=============================== sda5/etc/fstab: ===============================


#
# /etc/fstab
# Created by anaconda on Wed Dec  8 13:24:26 2010
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=22839ebc-fbf6-46fb-b021-c3afdbc89103 /                       ext4    defaults        1 1
UUID=0b79111f-cb14-4a43-b970-d395db20888e swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0

=================== sda5: Location of files loaded by Grub: ===================


  17.3GB: boot/grub/grub.conf
  17.3GB: boot/grub/menu.lst
  18.8GB: boot/grub/stage2
  19.4GB: boot/initramfs-2.6.35.6-45.fc14.i686.img
  22.1GB: boot/initramfs-2.6.35.9-64.fc14.i686.img
  23.3GB: boot/initrd-plymouth.img
  18.4GB: boot/vmlinuz-2.6.35.6-45.fc14.i686
  21.5GB: boot/vmlinuz-2.6.35.9-64.fc14.i686

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
search --no-floppy --fs-uuid --set 2736f0c9-25d9-4a29-9b28-9afeefa2824f
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
search --no-floppy --fs-uuid --set 2736f0c9-25d9-4a29-9b28-9afeefa2824f
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2736f0c9-25d9-4a29-9b28-9afeefa2824f
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=2736f0c9-25d9-4a29-9b28-9afeefa2824f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2736f0c9-25d9-4a29-9b28-9afeefa2824f
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=2736f0c9-25d9-4a29-9b28-9afeefa2824f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2736f0c9-25d9-4a29-9b28-9afeefa2824f
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=2736f0c9-25d9-4a29-9b28-9afeefa2824f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2736f0c9-25d9-4a29-9b28-9afeefa2824f
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=2736f0c9-25d9-4a29-9b28-9afeefa2824f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2736f0c9-25d9-4a29-9b28-9afeefa2824f
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=2736f0c9-25d9-4a29-9b28-9afeefa2824f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2736f0c9-25d9-4a29-9b28-9afeefa2824f
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=2736f0c9-25d9-4a29-9b28-9afeefa2824f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2736f0c9-25d9-4a29-9b28-9afeefa2824f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2736f0c9-25d9-4a29-9b28-9afeefa2824f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1907d850054be693
    chainloader +1
}
menuentry "Fedora (2.6.35.9-64.fc14.i686) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 22839ebc-fbf6-46fb-b021-c3afdbc89103
    linux /boot/vmlinuz-2.6.35.9-64.fc14.i686 ro root=UUID=22839ebc-fbf6-46fb-b021-c3afdbc89103 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-2.6.35.9-64.fc14.i686.img
}
menuentry "Fedora (2.6.35.6-45.fc14.i686) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 22839ebc-fbf6-46fb-b021-c3afdbc89103
    linux /boot/vmlinuz-2.6.35.6-45.fc14.i686 ro root=UUID=22839ebc-fbf6-46fb-b021-c3afdbc89103 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /boot/initramfs-2.6.35.6-45.fc14.i686.img
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
UUID=2736f0c9-25d9-4a29-9b28-9afeefa2824f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=0b79111f-cb14-4a43-b970-d395db20888e none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  40.0GB: boot/grub/core.img
  40.1GB: boot/grub/grub.cfg
  40.0GB: boot/initrd.img-2.6.32-24-generic
  40.5GB: boot/initrd.img-2.6.32-26-generic
  40.5GB: boot/initrd.img-2.6.32-27-generic
  40.4GB: boot/vmlinuz-2.6.32-24-generic
  40.4GB: boot/vmlinuz-2.6.32-26-generic
  40.5GB: boot/vmlinuz-2.6.32-27-generic
  40.5GB: initrd.img
  40.5GB: initrd.img.old
  40.5GB: vmlinuz
  40.4GB: vmlinuz.old

=========================== sda8/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Wed Dec 29 12:08:40 IST 2010
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,7)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.3
    root (hd0,7)
    kernel /boot/vmlinuz-2.6.34.7-0.4-default root=/dev/disk/by-id/ata-SAMSUNG_SP0802N_S00JJ50X528862-part8 resume=/dev/disk/by-id/ata-SAMSUNG_SP0802N_S00JJ50X528862-part7 splash=silent quiet showopts vga=0x31a
    initrd /boot/initrd-2.6.34.7-0.4-default

###Don't change this comment - YaST2 identifier: Original name:  Fedora (2.6.35.9-64.fc14.i686) (/dev/sda5)###
title  Fedora (2.6.35.9-64.fc14.i686) (/dev/sda5)
    root (hd0,4)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows
    rootnoverify (hd0,0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.3
    root (hd0,7)
    kernel /boot/vmlinuz-2.6.34.7-0.4-default root=/dev/disk/by-id/ata-SAMSUNG_SP0802N_S00JJ50X528862-part8 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.34.7-0.4-default

=============================== sda8/etc/fstab: ===============================

/dev/disk/by-id/ata-SAMSUNG_SP0802N_S00JJ50X528862-part7 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-SAMSUNG_SP0802N_S00JJ50X528862-part8 /                    ext4       acl,user_xattr        1 1
/dev/disk/by-id/ata-SAMSUNG_SP0802N_S00JJ50X528862-part9 /home                ext2       acl,user_xattr        1 2
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sda8: Location of files loaded by Grub: ===================


  58.0GB: boot/grub/menu.lst
  57.5GB: boot/grub/stage2
  58.0GB: boot/initrd
  58.0GB: boot/initrd-2.6.34.7-0.4-default
  57.5GB: boot/vmlinuz
  57.5GB: boot/vmlinuz-2.6.34.7-0.4-default
=============================== StdErr Messages: ===============================

  No volume groups found
mdadm: No arrays found in config file or automatically

---

### Post by garvinrick4 on 2010-12-29
# In a live cd
I going to say you have grub-legacy and grub2 all over the installs but not any in the mbr.
I do not no what Acer 3 in MBR of /dev/sda means. Usually there is a grub installed there to boot from. 
Some installs got both installed in same partition it looks like. All a grub is, is a piece of software to be 
installed in the mbr (sda) and looking in a partition for the boot files so as to be a bootable system. 
I would remove all grubs from fedora and openSuse and purge and reinstall grub2 to Ubuntu and then put grub2 into mbr. 
#I can give you a link to use a Live Cd and purge in a chroot command (be in root of install)
#after in root do not to use sudo.
```

[code]yum remove grub grub-common grub-pc
``` (for fedora)above
```
zypper remove grub grub-common grub-pc
``` (for OpenSuse)above
```
apt-get purge grub grub-common grub-pc
``` (for ubuntu)above
```
apt-get install grub-common grub-pc
``` (for ubuntu)above

# chroot into one install at a time and remove grub
In ubuntu you are purging and then reinstalling
To put in mbr using sda6 (ubuntu as residing files)below
```
sudo mount /dev/sda6 /mnt
``````
sudo grub-install --recheck --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
```Those 3 lines above will put grub2 into mbr.
Then boot into Ubuntu
```
sudo update-grub
```## Now take the fedora and openSuse first and remove grubs as stated:
## 3rd is Ubuntu to purge grub2 and reinstall then install grub2 into mbr (sda)
I will give you commands to chroot just change sda# for each install to correct one
for fedora, opensuse and Ubuntu. Chroot into one at a time; below
                       ```
sudo mount /dev/sda6 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```give each of the commands to remove grub as stated above:
```
exit
```                     ```

sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
  
```Put the grub2 in mbr last after removing grubs from fedora and 
opensuse and purging and installing in Ubuntu.
[/code]# Here is a nice link if you are confused

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by rockager on 2011-01-07
> **garvinrick4 said:**
> # In a live cd
I going to say you have grub-legacy and grub2 all over the installs but not any in the mbr.
I do not no what Acer 3 in MBR of /dev/sda means. Usually there is a grub installed there to boot from. 
Some installs got both installed in same partition it looks like. All a grub is, is a piece of software to be 
installed in the mbr (sda) and looking in a partition for the boot files so as to be a bootable system. 
I would remove all grubs from fedora and openSuse and purge and reinstall grub2 to Ubuntu and then put grub2 into mbr. 
#I can give you a link to use a Live Cd and purge in a chroot command (be in root of install)
#after in root do not to use sudo.
```

[code]yum remove grub grub-common grub-pc
``` (for fedora)above
```
zypper remove grub grub-common grub-pc
``` (for OpenSuse)above
```
apt-get purge grub grub-common grub-pc
``` (for ubuntu)above
```
apt-get install grub-common grub-pc
``` (for ubuntu)above

# chroot into one install at a time and remove grub
In ubuntu you are purging and then reinstalling
To put in mbr using sda6 (ubuntu as residing files)below
```
sudo mount /dev/sda6 /mnt
``````
sudo grub-install --recheck --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
```Those 3 lines above will put grub2 into mbr.
Then boot into Ubuntu
```
sudo update-grub
```## Now take the fedora and openSuse first and remove grubs as stated:
## 3rd is Ubuntu to purge grub2 and reinstall then install grub2 into mbr (sda)
I will give you commands to chroot just change sda# for each install to correct one
for fedora, opensuse and Ubuntu. Chroot into one at a time; below
                       ```
sudo mount /dev/sda6 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```give each of the commands to remove grub as stated above:
```
exit
```                     ```

sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
  
```Put the grub2 in mbr last after removing grubs from fedora and 
opensuse and purging and installing in Ubuntu.
[/code]# Here is a nice link if you are confused

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
thanks!!!
it worked!!

---

