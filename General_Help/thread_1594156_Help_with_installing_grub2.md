---
title: "Help with installing grub2"
date: 2010-10-12
forum: General Help
---

### Post by apena81 on 2010-10-12
I have two hard drives. One SATA with windows xp and one IDE hard drive as a slave (cd-rom as master) with ntfs storage and half as ubuntu 10.10

I got the live cd to boot with the "nomodeset" option on and installed ubuntu 10.10.
When i restarted my system, i changed the boot priority for my 2nd drive, the ide to boot first. When it booted i got to a screen that said some like error sil: only 3/4 metadata area found, then went to a black screen and nothing else (i got a no signal from my monitor)

When i load the live cd again and type "sudo mount /dev/sda1 /mnt" then "sudo install-grub --root-directory=/mnt /dev/sda" what  I get this error:

"/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported"


and nothing is done. How can i fix this??

---

### Post by wilee-nilee on 2010-10-12
Try this link for reloading grub2.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by apena81 on 2010-10-12
> **wilee-nilee said:**
> Try this link for reloading grub2.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)


Tried it, when i get to this part:
sudo grub-install --root-directory=/mnt/ /dev/sdX

I get this error:

/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported.

What does it mean?

---

### Post by Rubi1200 on 2010-10-12
Could you please post the results of the boot-script linked at the bottom of my post.

We need to get a better overview of your system before proceeding with possible solutions.

Thanks.

---

### Post by garvinrick4 on 2010-10-12
You have an ide drive with ntfs storage in front part of drive and the Ubuntu in rear and grub cannot find a mbr to reside in because it is in use?

---

### Post by apena81 on 2010-10-14
> **Rubi1200 said:**
> Could you please post the results of the boot-script linked at the bottom of my post.

We need to get a better overview of your system before proceeding with possible solutions.

Thanks.


Thanks

```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /grldr /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    19,535,039    19,534,977  83 Linux
/dev/sda2          26,202,076   234,436,544   208,234,469   f W95 Ext d (LBA)
/dev/sda5          26,202,078   142,978,499   116,776,422   7 HPFS/NTFS
/dev/sda6         142,978,563   234,436,544    91,457,982   7 HPFS/NTFS
/dev/sda3          19,535,040    23,824,394     4,289,355  83 Linux
/dev/sda4          23,824,395    26,202,014     2,377,620  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 100.3 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders, total 195813072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sdb2         102,398,310   195,784,154    93,385,845   f W95 Ext d (LBA)
/dev/sdb5         102,398,373   195,784,154    93,385,782   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002  42 SFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        96eac8da-c69c-4dd3-ab02-171af7dc88c5   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        6a509063-749e-4f00-ada1-e89b9dde4c10   ext4                                     
/dev/sda4        0fc0504b-152b-45f2-87b8-07894713336f   swap                                     
/dev/sda5        0F6088EC908C8239                       ntfs       ProgGames                     
/dev/sda6        C2C4A86AC4A86301                       ntfs       Free Space                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2280EF8880EF6131                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        9C00A37600A35654                       ntfs                                     
/dev/sdb                                                silicon_medley_raid_member                               
/dev/sdc1        3E8488C6848881DF                       ntfs       500GIG                        
/dev/sdc: PTTYPE="dos" 
/dev/sdd                                                isw_raid_member                               
error: and: No such file or directory
error: /dev/mapper//dev/sdd:: No such file or directory
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found
error: discovered: No such file or directory
error: formats: No such file or directory
error: "isw": No such file or directory
error: isw)!: No such file or directory
error: "sil": No such file or directory
error: (using: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/6a509063-749e-4f00-ada1-e89b9dde4c10 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/96eac8da-c69c-4dd3-ab02-171af7dc88c5 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 96eac8da-c69c-4dd3-ab02-171af7dc88c5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 96eac8da-c69c-4dd3-ab02-171af7dc88c5
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 96eac8da-c69c-4dd3-ab02-171af7dc88c5
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=96eac8da-c69c-4dd3-ab02-171af7dc88c5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 96eac8da-c69c-4dd3-ab02-171af7dc88c5
    echo    'Loading Linux 2.6.35-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=96eac8da-c69c-4dd3-ab02-171af7dc88c5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 96eac8da-c69c-4dd3-ab02-171af7dc88c5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 96eac8da-c69c-4dd3-ab02-171af7dc88c5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda3       /home           ext4    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=0fc0504b-152b-45f2-87b8-07894713336f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.5GB: boot/grub/core.img
   2.5GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.35-22-generic-pae
   5.3GB: boot/vmlinuz-2.6.35-22-generic-pae
   1.2GB: initrd.img
   5.3GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional with /3GB" /3GB /noexecute=optin /fastdetect /noexecute=alwaysoff 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 01  |................|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 e6 dd f5 06 00 fe  |................|
000001d0  ff ff 05 fe ff ff e8 dd  f5 06 fd 89 73 05 00 00  |............s...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  00 80 74 bc 00 00 63 bc  00 80 84 bc 00 40 99 bc  |..t...c......@..|
00000010  00 80 97 bc 00 80 71 bc  00 00 45 bc 00 80 40 bc  |......q...E...@.|
00000020  00 00 14 bc 00 00 98 bb  00 00 5a bb 00 00 ec ba  |..........Z.....|
00000030  00 00 54 3b 00 00 be 3b  00 00 89 3b 00 00 b9 3b  |..T;...;...;...;|
00000040  00 00 3b 3c 00 80 5a 3c  00 00 f1 3b 00 00 90 ba  |..;<..Z<...;....|
00000050  00 00 a4 bb 00 00 8d bb  00 00 98 bb 00 00 08 bc  |................|
00000060  00 00 2f bc 00 00 03 bc  00 00 14 bb 00 00 0a 3b  |../............;|
00000070  00 00 86 3b 00 00 ca 3b  00 00 11 3c 00 80 1f 3c  |...;...;...<...<|
00000080  00 80 20 3c 00 80 41 3c  00 00 4b 3c 00 80 00 3c  |.. <..A<..K<...<|
00000090  00 00 6e 3b 00 00 8b 3b  00 00 ba 3b 00 00 ca 3b  |..n;...;...;...;|
000000a0  00 00 01 3c 00 80 14 3c  00 80 16 3c 00 80 38 3c  |...<...<...<..8<|
000000b0  00 80 54 3c 00 80 41 3c  00 00 50 3c 00 80 8e 3c  |..T<..A<..P<...<|
000000c0  00 c0 a4 3c 00 c0 a0 3c  00 c0 a1 3c 00 00 b2 3c  |...<...<...<...<|
000000d0  00 80 c7 3c 00 40 c9 3c  00 00 9f 3c 00 00 56 3c  |...<.@.<...<..V<|
000000e0  00 80 46 3c 00 80 7c 3c  00 80 95 3c 00 00 99 3c  |..F<..|<...<...<|
000000f0  00 c0 82 3c 00 80 56 3c  00 00 6e 3c 00 80 8c 3c  |...<..V<..n<...<|
00000100  00 00 6d 3c 00 80 0f 3c  00 00 dc 3b 00 00 13 3c  |..m<...<...;...<|
00000110  00 80 37 3c 00 80 33 3c  00 80 21 3c 00 80 13 3c  |..7<..3<..!<...<|
00000120  00 00 d7 3b 00 00 6c 3b  00 00 60 3b 00 00 5a 3b  |...;..l;..`;..Z;|
00000130  00 00 b4 3a 00 00 94 3b  00 80 5e 3c 00 00 85 3c  |...:...;..^<...<|
00000140  00 00 1f 3c 00 00 d5 3b  00 00 3c 3c 00 00 88 3c  |...<...;..<<...<|
00000150  00 40 8c 3c 00 00 80 3c  00 00 79 3c 00 40 8a 3c  |.@.<...<..y<.@.<|
00000160  00 80 9d 3c 00 00 a2 3c  00 00 9b 3c 00 c0 9d 3c  |...<...<...<...<|
00000170  00 80 ad 3c 00 00 b8 3c  00 80 b7 3c 00 c0 bc 3c  |...<...<...<...<|
00000180  00 80 c9 3c 00 00 cd 3c  00 00 d2 3c 00 c0 ed 3c  |...<...<...<...<|
00000190  00 80 fb 3c 00 80 d2 3c  00 40 a9 3c 00 00 c4 3c  |...<...<.@.<...<|
000001a0  00 80 f3 3c 00 00 e6 3c  00 80 ae 3c 00 40 90 3c  |...<...<...<.@.<|
000001b0  00 80 8f 3c 00 40 86 3c  00 00 62 3c 00 80 00 fe  |...<.@.<..b<....|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 36 f4 90 05 00 00  |......?...6.....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sde sdf sdg sdh sdd: "sil" and "isw" formats discovered (using isw)! 
=============================== StdErr Messages: ===============================

ERROR: sil: only 3/4 metadata areas found on /dev/sdb, electing...
ERROR: isw: wrong number of devices in RAID set "isw_ceaihabcji_RAID_Volume0" [1/2] on /dev/sdd
ERROR: sil: wrong # of devices in RAID set "sil_agacagbieiae" [1/2] on /dev/sdb
ERROR: removing inconsistent RAID set "sil_agacagbieiae"
ERROR: sil: only 3/4 metadata areas found on /dev/sdb, electing...
ERROR: sil: wrong # of devices in RAID set "sil_agacagbieiae" [1/2] on /dev/sdb
ERROR: only one argument allowed for this option
ERROR: sil: only 3/4 metadata areas found on /dev/sdb, electing...
ERROR: isw: wrong number of devices in RAID set "isw_ceaihabcji_RAID_Volume0" [1/2] on /dev/sdd
ERROR: sil: wrong # of devices in RAID set "sil_agacagbieiae" [1/2] on /dev/sdb
ERROR: removing inconsistent RAID set "sil_agacagbieiae"
ERROR: sil: only 3/4 metadata areas found on /dev/sdb, electing...
ERROR: isw: wrong number of devices in RAID set "isw_ceaihabcji_RAID_Volume0" [1/2] on /dev/sdd
ERROR: sil: wrong # of devices in RAID set "sil_agacagbieiae" [1/2] on /dev/sdb
ERROR: removing inconsistent RAID set "sil_agacagbieiae"
ERROR: sil: only 3/4 metadata areas found on /dev/sdb, electing...
ERROR: sil: wrong # of devices in RAID set "sil_agacagbieiae" [1/2] on /dev/sdb
ERROR: only one argument allowed for this option


```

---

### Post by apena81 on 2010-10-15
I would really love any guidance is to what may be the problem.:confused:

---

### Post by Rubi1200 on 2010-10-15
What is > FlexNetand do you really need it?

Do you have a RAID setup?

The script is reporting errors because RAID metadata has been detected.

---

### Post by apena81 on 2010-10-15
> **Rubi1200 said:**
> What is and do you really need it?

Do you have a RAID setup?

The script is reporting errors because RAID metadata has been detected.

I don't know what flexnet is and yes, i have windows xp on a RAID setup and i have ubuntu installed on an ide hard drive with ntfs storage. 

When i change my boot priority to the ide hard drive, ubuntu doesn't load...my monitor just goes black and nothing happens.

---

### Post by apena81 on 2010-10-18
Anyone else?

:(

---

### Post by sandyd on 2010-10-18
> **apena81 said:**
> Anyone else?

:(
remove adobe flexnet from windows

---

### Post by drs305 on 2010-10-18
I don't know what Flexnet is either but this could be it:
[http://www.flexerasoftware.com/products/flexnet-connect.htm]("http://www.flexerasoftware.com/products/flexnet-connect.htm")

Whatever it is, and I'm assuming it's a Windows thing because Linux normally doesn't install things you know nothing about, it is writing to a section of your drive just past the MBR. My understanding is that Grub uses a small part of this area to store additional data. 

Unfortunately, so do a few other apps and apparently they fight for this same space. 

One solution would be to get rid of the other app or put Grub on another drive's MBR *if this drive is always connected*. 

edit: On further reflection, the following probably wouldn't work unless a boot partition is placed on sdc.
original:
You can still keep the Grub files in your normal Ubuntu installation even if you write Grub to another disks MBR. sdc would be a good candidate if it's always connected since it doesn't have any Windows boot files on it.

---

### Post by apena81 on 2010-10-18
If i install it on sdc, will that precede the grub installation on sda?

Can i install grub on sdc and leave the installation of ubuntu on sda?

Can you help me with what i need to type in the terminal?

Thanks

---

### Post by drs305 on 2010-10-18
> **apena81 said:**
> If i install it on sdc, will that precede the grub installation on sda?

Sorry, but I don't think this proposal will work. I'll have to think on it some more. The real solution is to get rid of Flexnet.

The sdc option might only work if you make a /boot folder on that drive and this is going to lead to complications... :-(

---

### Post by drs305 on 2010-10-19
Here are your options for dealing with an application that writes to the MBR and conflicts with Grub 2:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR")

Option 4 was the one I was trying to remember earlier but couldn't remember the debconf commands.

---

### Post by apena81 on 2010-10-21
My boot drive is sdb with windows, ubuntu is installed on sda1....can't i install grub2 on sdb and have it boot ubuntu on sda1?

---

### Post by drs305 on 2010-10-21
> **apena81 said:**
> My boot drive is sdb with windows, ubuntu is installed on sda1....can't i install grub2 on sdb and have it boot ubuntu on sda1?

Take a look at option 4 from *meierfra's* site:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR")

I have not tried this. You would run the command from a normal boot into Ubuntu. If using a LiveCD, you would need to *chroot* into your Ubuntu partition first. The *chroot* instructions are here:
[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

---

