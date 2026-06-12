---
title: "Grub 2 doesn't start  Windows 7 64-bits"
date: 2010-12-27
forum: General Help
---

### Post by nicolaas3 on 2010-12-27
Using Ubuntu 10.4 32-bits, Windows 7 **32-bits (sda) **and Windows 7 **64-bits (sdb)**.  Grub displays  2 menu-entries Windows 7, but both entries start Windows 32-bits (sda).

"sudo update -grub" doesn help. 


 sudo fdisk -ul gives:[INDENT]Schijf /dev/sda: 640.1 GB, 640135028736 bytes
255 koppen, 63 sectoren/spoor, 77825 cilinders, totaal 1250263728 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Schijf-ID: 0x45574557

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *          63   976575284   488287611    7  HPFS/NTFS
/dev/sda2       976575346  1250258624   136841639+   5  Uitgebreid
/dev/sda5       976575348  1230482609   126953631   83  Linux
/dev/sda6      1230482673  1250258624     9887976   82  Linux wisselgeheugen

Schijf /dev/sdb: 640.1 GB, 640135028736 bytes
255 koppen, 63 sectoren/spoor, 77825 cilinders, totaal 1250263728 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Schijf-ID: 0x1e86ee90

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS
Partitie 1 eindigt niet op een cilindergrens.
/dev/sdb2          206848  1250260991   625027072    7  HPFS/NTFS
[/INDENT]Thanks in advance
Nico

---

### Post by Quackers on 2010-12-27
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by nicolaas3 on 2010-12-28
Here you go [Quackers]("http://ubuntuforums.org/member.php?u=369240"), the content of the RESULTS.txt, I hope you can help me.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /ntldr 
                       /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdg1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Schijf /dev/sda: 640.1 GB, 640135028736 bytes
255 koppen, 63 sectoren/spoor, 77825 cilinders, totaal 1250263728 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,575,284   976,575,222   7 HPFS/NTFS
/dev/sda2         976,575,346 1,250,258,624   273,683,279   5 Extended
/dev/sda5         976,575,348 1,230,482,609   253,907,262  83 Linux
/dev/sda6       1,230,482,673 1,250,258,624    19,775,952  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Schijf /dev/sdb: 640.1 GB, 640135028736 bytes
255 koppen, 63 sectoren/spoor, 77825 cilinders, totaal 1250263728 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848 1,250,260,991 1,250,054,144   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Schijf /dev/sdc: 8025 MB, 8025800704 bytes
5 koppen, 32 sectoren/spoor, 97971 cilinders, totaal 15675392 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          8,064    15,675,391    15,667,328   c W95 FAT32 (LBA)


Drive: sdg ___________________ _____________________________________________________

Schijf /dev/sdg: 1000.2 GB, 1000204886016 bytes
255 koppen, 63 sectoren/spoor, 121601 cilinders, totaal 1953525168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F4D8CC52D8CC14B0                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        d435fd5d-c473-431f-ba7c-9e4462be9ee9   ext4                                     
/dev/sda6        143f160c-364f-4862-9643-a2cb1cd944c3   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1240B8A940B894C7                       ntfs       System Reserved               
/dev/sdb2        1C5EBB715EBB4276                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        F694-9CFA                              vfat       KINGSTON                      
/dev/sdc: PTTYPE="dos" 
/dev/sdg1        3678FA5978FA1779                       ntfs       schijf Hend                   
/dev/sdg: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/KINGSTON          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(1)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 

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
search --no-floppy --fs-uuid --set d435fd5d-c473-431f-ba7c-9e4462be9ee9
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
search --no-floppy --fs-uuid --set d435fd5d-c473-431f-ba7c-9e4462be9ee9
set locale_dir=($root)/boot/grub/locale
set lang=nl
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
menuentry 'Ubuntu, met Linux 2.6.32-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d435fd5d-c473-431f-ba7c-9e4462be9ee9
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=d435fd5d-c473-431f-ba7c-9e4462be9ee9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.32-27-generic-pae (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d435fd5d-c473-431f-ba7c-9e4462be9ee9
    echo    'Linux 2.6.32-27-generic-pae laden ...'
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=d435fd5d-c473-431f-ba7c-9e4462be9ee9 ro single 
    echo    'Initiële ramdisk laden ...'
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d435fd5d-c473-431f-ba7c-9e4462be9ee9
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=d435fd5d-c473-431f-ba7c-9e4462be9ee9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.32-26-generic-pae (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d435fd5d-c473-431f-ba7c-9e4462be9ee9
    echo    'Linux 2.6.32-26-generic-pae laden ...'
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=d435fd5d-c473-431f-ba7c-9e4462be9ee9 ro single 
    echo    'Initiële ramdisk laden ...'
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d435fd5d-c473-431f-ba7c-9e4462be9ee9
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=d435fd5d-c473-431f-ba7c-9e4462be9ee9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.32-25-generic-pae (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d435fd5d-c473-431f-ba7c-9e4462be9ee9
    echo    'Linux 2.6.32-25-generic-pae laden ...'
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=d435fd5d-c473-431f-ba7c-9e4462be9ee9 ro single 
    echo    'Initiële ramdisk laden ...'
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d435fd5d-c473-431f-ba7c-9e4462be9ee9
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=d435fd5d-c473-431f-ba7c-9e4462be9ee9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.32-24-generic-pae (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d435fd5d-c473-431f-ba7c-9e4462be9ee9
    echo    'Linux 2.6.32-24-generic-pae laden ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=d435fd5d-c473-431f-ba7c-9e4462be9ee9 ro single 
    echo    'Initiële ramdisk laden ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d435fd5d-c473-431f-ba7c-9e4462be9ee9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d435fd5d-c473-431f-ba7c-9e4462be9ee9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set f4d8cc52d8cc14b0
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 1240b8a940b894c7
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=143f160c-364f-4862-9643-a2cb1cd944c3 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 611.8GB: boot/grub/core.img
 503.0GB: boot/grub/grub.cfg
 612.0GB: boot/initrd.img-2.6.32-24-generic-pae
 611.9GB: boot/initrd.img-2.6.32-25-generic-pae
 612.0GB: boot/initrd.img-2.6.32-26-generic-pae
 613.8GB: boot/initrd.img-2.6.32-27-generic-pae
 611.9GB: boot/vmlinuz-2.6.32-24-generic-pae
 611.9GB: boot/vmlinuz-2.6.32-25-generic-pae
 611.9GB: boot/vmlinuz-2.6.32-26-generic-pae
 612.3GB: boot/vmlinuz-2.6.32-27-generic-pae
 613.8GB: initrd.img
 612.0GB: initrd.img.old
 612.3GB: vmlinuz
 611.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf 
```

---

### Post by oldfred on 2010-12-28
Your sda1 shows remnants of XP and grub4dos. But they should just need housecleaning, but do not control boot.

Windows combines all of its boots into one, since it can only boot one partition. 

Discusses Vista but 7 is the same.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

You may be able to edit the bcd of each windows install to get it to only see the one install. Normally you can do it by installing one windows, then moving the boot flag to another NTFS partition and installing the second. With two drives you have to tell windows not to look for additional copies of windows.

---

### Post by nicolaas3 on 2011-01-04
It seems to me a Windows problem. Probably this gives me the right information. It will take me some time to figure out whether it solves my problem or not. So I will mark this thread as Solved .

Thanks oldfred

---

