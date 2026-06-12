---
title: "booting straight to memtest"
date: 2010-10-29
forum: General Help
---

### Post by dfeg on 2010-10-29
Hi
 
I ran some updates using synaptic and when i rebooted the next day it went straight to memtest.
 
I've accessed the grub menu and there are only 2 options both of which are memtest.
 
I've tried following every thread i can find on the subject including [http://ubuntuforums.org/showthread.php?t=1202799&page=2](http://ubuntuforums.org/showthread.php?t=1202799&page=2) but i can't seem to fix the problem.
 
Any help would be greatly appreciated.
 
Damien

---

### Post by ajgreeny on 2010-10-29
Which version of Ubuntu and which grub; legacy grub or grub2?

If it is grub2 on Ubuntu 9.10 or later, you may be able to restore grub with the live CD, and that should get you back to an OS again.

Have a look at [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) but make sure you follow the various version options on that page, dependent on the grub version you have, and then try booting again.

It will also be helpful to download and run the Boot-info-script as shown in my signature line.  It will give a lot of detailed information about your system and the boot management.

---

### Post by aeiah on 2010-10-29
perhaps check out supergrub. its a grub livecd and it'll let you boot into ubuntu, and also allow you to fix it. you may find it easier to just boot into ubuntu with the disk and from there try to restore grub

---

### Post by dfeg on 2010-10-29
Sorry for the lack of information

I'm running 10.04 which would mean that i'm also using grub2

I've used the startup disk to launch ubuntu and get to terminal. I tried to follow that thread [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) but when i type in
sudo grub
i get the reply
sudo: grub: command not found

I've run the boot info script 
and it came up with the following results file 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

/dev/sda1    *          2,048   224,827,391   224,825,344  83 Linux
/dev/sda2         224,829,438   234,440,703     9,611,266   5 Extended
/dev/sda5         224,829,440   234,440,703     9,611,264  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   234,438,655   234,436,608   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        15fb6270-5a57-4769-8f78-b1bfeb76c2dd   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        da36d029-8ecc-461d-815b-c0bf1794cea3   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        30F42A0EF429D6BE                       ntfs       DATAPART1                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/15fb6270-5a57-4769-8f78-b1bfeb76c2dd ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 15fb6270-5a57-4769-8f78-b1bfeb76c2dd
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 15fb6270-5a57-4769-8f78-b1bfeb76c2dd
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 15fb6270-5a57-4769-8f78-b1bfeb76c2dd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 15fb6270-5a57-4769-8f78-b1bfeb76c2dd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
/dev/sda5       none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  65.0GB: boot/grub/core.img
   8.8GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  d8 1e b5 95 38 b5 74 d1  dc af 65 24 8a 0d b1 46  |....8.t...e$...F|
00000010  72 0f 18 19 e9 50 19 95  89 50 38 1f dd e9 5c b3  |r....P...P8...\.|
00000020  e6 d7 53 68 45 3b 22 40  c8 37 05 38 c6 01 fa 55  |..ShE;"@.7.8...U|
00000030  98 de 45 18 18 1b ba 7c  a4 71 59 73 59 d9 95 2a  |..E....|.qYsY..*|
00000040  6a 2e e5 a0 5b 71 6c 63  20 0c f3 53 91 86 c8 61  |j...[qlc ..S...a|
00000050  cf f7 79 e2 b7 75 a3 17  ee 23 19 45 3b 59 10 ba  |..y..u...#.E;Y..|
00000060  e7 80 58 86 e3 39 e7 34  d9 13 21 78 04 30 38 3d  |..X..9.4..!x.08=|
00000070  c1 a8 97 35 4b 4a c3 4f  96 f6 63 42 86 52 a1 88  |...5KJ.O..cB.R..|
00000080  fe 2e 4e 0d 21 8c 61 b8  62 38 e7 23 81 4e 70 a8  |..N.!.a.b8.#.Np.|
00000090  de ac a5 37 16 e2 c9 23  89 42 fc c5 93 b9 2d d4  |...7...#.B....-.|
000000a0  53 96 03 27 cc 80 ec c9  e7 18 18 aa a4 9f c4 53  |S..'...........S|
000000b0  6a cb 95 16 7c b5 d9 82  40 3b 89 e4 e7 d6 9a b0  |j...|...@;......|
000000c0  92 43 63 3d c0 39 cd 37  56 50 bb 5d 4c dc 2f 7b  |.Cc=.9.7VP.]L./{|
000000d0  3d 49 fc b2 f8 56 f6 6e  98 c5 5e 9a cd 5a 38 d8  |=I...V.n..^..Z8.|
000000e0  71 8c 1e 79 39 af 4f 29  94 a5 3d 65 74 79 79 85  |q..y9.O)..=etyy.|
000000f0  05 ec f9 9a d4 cd 95 fc  a3 b4 f2 c3 24 12 b9 e7  |............$...|
00000100  fc f3 4c 32 ef 0a ce 57  68 04 1c 1f bc 39 ad 33  |..L2...Wh....9.3|
00000110  3c 45 48 54 e4 4c cf 05  85 8f 2a 72 20 44 52 c3  |<EHT.L....*r DR.|
00000120  18 19 24 73 92 0d 4b f6  7d c5 94 05 07 3c fc b5  |..$s..K.}....<..|
00000130  e6 c6 73 6b df 3d 1f 67  4d 26 99 18 b5 24 93 9c  |..sk.=.gM&...$..|
00000140  60 9d b9 00 e4 f3 fe 7f  2a 9b cd 10 2e 58 07 63  |`.......*....X.c|
00000150  9c 15 c7 27 f9 e6 ae 9d  7a 94 da 94 64 64 e8 c6  |...'....z...dd..|
00000160  50 b3 64 7f da 88 02 02  ca 00 f9 5b 23 38 3f d6  |P.d........[#8?.|
00000170  ab cb 7f 0b b1 cb 2b 8c  74 5e 05 7a 74 f3 17 51  |......+.t^.zt..Q|
00000180  72 b6 73 fd 41 29 73 58  ca 95 a3 24 15 43 96 6c  |r.s.A)sX...$.C.l|
00000190  8c 63 e6 1f 4a bd 05 dc  51 6d 2a 88 49 27 3b 78  |.c..J...Qm*.I';x|
000001a0  db fe 7a d6 50 c5 ba 75  9a 46 d5 70 bc f1 46 9a  |..z.P..u.F.p..F.|
000001b0  5e 44 14 6d 19 27 86 e7  24 9a 9e 3b b8 58 00 fe  |^D.m.'..$..;.X..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 92 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```Thanks again

---

### Post by dfeg on 2010-10-29
sorry more information that might help. my grub version

ubuntu@ubuntu:~$ grub-install -v
grub-install (GNU GRUB 1.98-1ubuntu5)

---

### Post by Quackers on 2010-10-29
I've only read the first bit of that guide, but it was written in 2006 and I would presume refers to grub, rather than grub2.
Here is one by drs305 which refers to grub2

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Rubi1200 on 2010-10-29
Not sure what went wrong as a result of the updates you did, but there is definitely a problem:

> ### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###
This is where your Ubuntu install should show up, but it is empty.

> sda1: Location of files loaded by Grub:
> 65.0GB: boot/grub/core.img
   8.8GB: boot/grub/grub.cfg
This is fine, except that you are missing the following files:
> boot/initrd.img-2.6.xx-xx-generic
boot/vmlinuz-2.6.xx-xx-generic
initrd.img
vmlinuz

I suggest you chroot into the system and purge then reinstall GRUB:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Obviously, replace the partition numbering with your specifics.

If you have any questions, feel free to ask.

---

### Post by dfeg on 2010-10-29
I've tried following that thread through a few times but it doesn't fix the problem. There are a few errors as i go through it. Here is a copy from terminal I hope it helps

> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mkdir /mnt/temp
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/temp
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
root@ubuntu:/# apt-get update
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid Release.gpg
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/restricted Translation-en_US
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid Release
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/main Packages
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/restricted Packages
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/main Packages
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/restricted Packages
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Get:1 [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny Release.gpg [1,033B]                      
Ign [http://ftp.debian.org](http://ftp.debian.org) etch Release.gpg                                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg [307B]                        
Ign [http://ftp.debian.org/](http://ftp.debian.org/) etch/main Translation-en_US                         
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://ppa.launchpad.net/gilir/ubuntu/](http://ppa.launchpad.net/gilir/ubuntu/) hardy/main Translation-en_US        
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]                   
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Ign [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) lenny/main Translation-en_US              
Ign [http://ppa.launchpad.net/gilir/ubuntu/](http://ppa.launchpad.net/gilir/ubuntu/) hardy/universe Translation-en_US    
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US                
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US            
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu/](http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ftp.debian.org](http://ftp.debian.org) etch Release                                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release                                 
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main Translation-en_US
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [46.7kB]                          
Get:5 [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny Release [73.8kB]                          
Ign [http://ftp.debian.org](http://ftp.debian.org) etch/main Packages                                   
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://ftp.debian.org](http://ftp.debian.org) etch/main Packages                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny Release                                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Err [http://ftp.debian.org](http://ftp.debian.org) etch/main Packages                                   
  404  Not Found
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Packages                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages                          
Hit [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Sources                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Packages                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/universe Packages                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Packages         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Packages   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Packages     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Sources          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release.gpg               
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) lucid-getdeb/apps Translation-en_US
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) lucid-getdeb/games Translation-en_US
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Sources              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/universe Packages        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/universe Packages  
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release       
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Packages                       
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/games Packages                      
Fetched 1,540B in 7s (197B/s)                                                  
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 665F9AEFE1098513
W: GPG error: [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9AA38DCD55BE302B NO_PUBKEY 4D270D06F42584E6
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://ftp.debian.org/dists/etch/main/binary-i386/Packages.gz](http://ftp.debian.org/dists/etch/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
root@ubuntu:/# apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 nvidia-settings paprefs wisotool wwwconfig-common
  libmcrypt4 libjs-mootools linux-headers-2.6.32-21-generic libt1-5 winetricks
  ttf-mscorefonts-installer ttf-symbol-replacement os-prober wine1.2-gecko
  pulseaudio-module-zeroconf libmpg123-0 javascript-common libgconfmm-2.6-1c2
  dbconfig-common winbind gnome-exe-thumbnailer
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  grub-common* grub-pc*
0 upgraded, 0 newly installed, 2 to remove and 13 not upgraded.
1 not fully installed or removed.
After this operation, 6,603kB disk space will be freed.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 274718 files and directories currently installed.)
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for install-info ...
root@ubuntu:/# apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 nvidia-settings paprefs wisotool wwwconfig-common
  libmcrypt4 libjs-mootools linux-headers-2.6.32-21-generic libt1-5 winetricks
  ttf-mscorefonts-installer ttf-symbol-replacement wine1.2-gecko
  pulseaudio-module-zeroconf libmpg123-0 javascript-common libgconfmm-2.6-1c2
  dbconfig-common winbind gnome-exe-thumbnailer
Use 'apt-get autoremove' to remove them.
Suggested packages:
  multiboot-doc grub-emu desktop-base
The following NEW packages will be installed:
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 13 not upgraded.
Need to get 0B/2,112kB of archives.
After this operation, 6,603kB of additional disk space will be used.
Preconfiguring packages ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Selecting previously deselected package grub-common.
(Reading database ... 274444 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.98-1ubuntu7_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.98-1ubuntu7_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up grub-common (1.98-1ubuntu7) ...

Setting up grub-pc (1.98-1ubuntu7) ...

Creating config file /etc/default/grub with new version
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
Failure to communicate with kernel device-mapper driver.
grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub-common is already the newest version.
grub-pc is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 nvidia-settings paprefs wisotool wwwconfig-common
  libmcrypt4 libjs-mootools linux-headers-2.6.32-21-generic libt1-5 winetricks
  ttf-mscorefonts-installer ttf-symbol-replacement wine1.2-gecko
  pulseaudio-module-zeroconf libmpg123-0 javascript-common libgconfmm-2.6-1c2
  dbconfig-common winbind gnome-exe-thumbnailer
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up grub-pc (1.98-1ubuntu7) ...
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
Failure to communicate with kernel device-mapper driver.
grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ for i in /dev/pts /dev /proc /sys / ; do sudo umount /mnt/temp$i ; done
umount: /mnt/temp/dev/pts: not mounted
umount: /mnt/temp/dev: not mounted
umount: /mnt/temp/proc: not mounted
umount: /mnt/temp/sys: not mounted
ubuntu@ubuntu:~$ 


---

### Post by Quackers on 2010-10-29
You missed the third command out

```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done

```

---

### Post by drs305 on 2010-10-29
First, don't reboot. You have removed grub2 but not yet reinstalled it.

You didn't follow the mounting procedure in the chroot guide. You mounted the Ubuntu partition but not all the filesystems necessary (including /dev/pts).

If you are still booted, you need to unmount /dev/sda1 and start the process over. Make sure you mount /dev, /dev/pts, /proc and /sys, then chroot in and install grub-common and grub-pc.

---

### Post by dfeg on 2010-10-29
First of all thanks for your help & patients so far. I'm still fairly new to ubuntu but loving it.

I've went through the post again and mounted all of the drives mentioned, but unfortunately it still hasn't fixed the issue. When i restart it still goes straight to memtest and if I restart with shift down to go to the grub menu there are still only 2 options both of which are memtest.

Here is a copy of terminal from when i went through the post again.
> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mkdir /mnt/temp 
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/temp
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
root@ubuntu:/# apt-get update
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid Release.gpg
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/restricted Translation-en_US
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid Release
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/main Packages
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/restricted Packages
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/main Packages
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/restricted Packages
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) lucid/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg [307B]                        
Ign [http://ppa.launchpad.net/gilir/ubuntu/](http://ppa.launchpad.net/gilir/ubuntu/) hardy/main Translation-en_US        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://ppa.launchpad.net/gilir/ubuntu/](http://ppa.launchpad.net/gilir/ubuntu/) hardy/universe Translation-en_US    
Ign [http://ftp.debian.org](http://ftp.debian.org) etch Release.gpg                                     
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://ftp.debian.org/](http://ftp.debian.org/) etch/main Translation-en_US                         
Get:3 [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny Release.gpg [1,033B]                      
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US                
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) lenny/main Translation-en_US              
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu/](http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu/) lucid/main Translation-en_US
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Ign [http://ftp.debian.org](http://ftp.debian.org) etch Release                                         
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]                     
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main Translation-en_US
Get:5 [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny Release [73.8kB]                          
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [46.7kB]                          
Ign [http://ftp.debian.org](http://ftp.debian.org) etch/main Packages                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release                                
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Ign [http://ftp.debian.org](http://ftp.debian.org) etch/main Packages                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages                          
Hit [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release.gpg                     
Err [http://ftp.debian.org](http://ftp.debian.org) etch/main Packages                                   
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/universe Packages                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release.gpg               
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) lucid-getdeb/apps Translation-en_US
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) lucid-getdeb/games Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/universe Packages        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/universe Packages                        
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Packages                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Sources                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Packages                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Sources           
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Packages                       
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/games Packages                      
Fetched 1,540B in 10s (140B/s)                                                 
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9AA38DCD55BE302B NO_PUBKEY 4D270D06F42584E6
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 665F9AEFE1098513
W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://ftp.debian.org/dists/etch/main/binary-i386/Packages.gz](http://ftp.debian.org/dists/etch/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
root@ubuntu:/# apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 nvidia-settings paprefs wisotool wwwconfig-common
  libmcrypt4 libjs-mootools linux-headers-2.6.32-21-generic libt1-5 winetricks
  ttf-mscorefonts-installer ttf-symbol-replacement os-prober wine1.2-gecko
  pulseaudio-module-zeroconf libmpg123-0 javascript-common libgconfmm-2.6-1c2
  dbconfig-common winbind gnome-exe-thumbnailer
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  grub-common* grub-pc*
0 upgraded, 0 newly installed, 2 to remove and 13 not upgraded.
After this operation, 6,603kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 274718 files and directories currently installed.)
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for install-info ...
root@ubuntu:/# apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 nvidia-settings paprefs wisotool wwwconfig-common
  libmcrypt4 libjs-mootools linux-headers-2.6.32-21-generic libt1-5 winetricks
  ttf-mscorefonts-installer ttf-symbol-replacement wine1.2-gecko
  pulseaudio-module-zeroconf libmpg123-0 javascript-common libgconfmm-2.6-1c2
  dbconfig-common winbind gnome-exe-thumbnailer
Use 'apt-get autoremove' to remove them.
Suggested packages:
  multiboot-doc grub-emu desktop-base
The following NEW packages will be installed:
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 13 not upgraded.
Need to get 0B/2,112kB of archives.
After this operation, 6,603kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 274444 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.98-1ubuntu7_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.98-1ubuntu7_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Setting up grub-common (1.98-1ubuntu7) ...

Setting up grub-pc (1.98-1ubuntu7) ...

Creating config file /etc/default/grub with new version
Installation finished. No error reported.
Generating grub.cfg ...
Found memtest86+ image: /boot/memtest86+.bin
done

root@ubuntu:/# update-grub
Generating grub.cfg ...
Found memtest86+ image: /boot/memtest86+.bin
done
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ for i in /dev/pts /dev /proc /sys / ; do sudo umount /mnt/temp$i ; done
ubuntu@ubuntu:~$ 


---

### Post by drs305 on 2010-10-29
Ok, nicely done. You have reinstalled Grub but it is still not finding your kernels.

If you open a browser in your Ubuntu partition's /boot folder you should find a vmlinuz-2.6.32-XX file and an initrd.img-2.6.32-XX. To search your real Ubuntu partition, mount it and then take a look with a file browser or the following 'ls' command:

```
sudo mount /dev/sda1 /mnt
ls /mnt/boot/*2.6-*
```

If you don't have a vmlinuz and initrd.img file listed, you will need to install the kernel. To do this, chroot into your Ubuntu installation as you did earlier. 

Once at the 'root' prompt, run:
```
sudo apt-get install linux-image
sudo update-grub
```

Exit the chroot by typing "exit", then run the "ls" command as above once more and see if the vmlinuz kernel and initrd.img files are now in /mnt/boot.

---

### Post by dfeg on 2010-10-30
OK I've done that and we've stopped booting to memtest but we're not getting into ubuntu yet.

When I hold down shift on boot up to go to grub there are now 2 entries for ubuntu. The default one takes me to a blank black screen with just a flashing underscore on it  _

The second one is recovery which goes so far and then stops when it says

Begin: Waiting for root file system .....

Here is a copy of my last terminal session, I got a little lost at the start but i think i've mounted the drives correctly.
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ ls /mnt/boot/*2.6-*
ls: cannot access /mnt/boot/*2.6-*: No such file or directory
ubuntu@ubuntu:~$ chroot /mnt/boot
chroot: cannot change root directory to /mnt/boot: Operation not permitted
ubuntu@ubuntu:~$ sudo mkdir /mnt/temp 
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
mount: mount point /mnt/temp/dev does not exist
mount: mount point /mnt/temp/dev/pts does not exist
mount: mount point /mnt/temp/proc does not exist
mount: mount point /mnt/temp/sys does not exist
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/temp
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
root@ubuntu:/# sudo apt-get install linux-image
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 nvidia-settings paprefs wisotool wwwconfig-common
  libmcrypt4 libjs-mootools linux-headers-2.6.32-21-generic libt1-5 winetricks
  ttf-mscorefonts-installer ttf-symbol-replacement wine1.2-gecko
  pulseaudio-module-zeroconf libmpg123-0 javascript-common libgconfmm-2.6-1c2
  dbconfig-common winbind gnome-exe-thumbnailer
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-2.6.32-25-generic linux-image-generic wireless-crda
Suggested packages:
  fdutils linux-doc-2.6.32 linux-source-2.6.32 linux-tools
The following NEW packages will be installed:
  linux-image linux-image-2.6.32-25-generic linux-image-generic wireless-crda
0 upgraded, 4 newly installed, 0 to remove and 13 not upgraded.
Need to get 31.5MB of archives.
After this operation, 99.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main wireless-crda 1.12 [14.9kB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-image-2.6.32-25-generic 2.6.32-25.45 [31.5MB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-image-generic 2.6.32.25.27 [4,120B]
Get:4 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-image 2.6.32.25.27 [4,106B]
Fetched 31.5MB in 2h 36min 58s (3,348B/s)                                      
Selecting previously deselected package wireless-crda.
(Reading database ... 274720 files and directories currently installed.)
Unpacking wireless-crda (from .../wireless-crda_1.12_i386.deb) ...
Selecting previously deselected package linux-image-2.6.32-25-generic.
Unpacking linux-image-2.6.32-25-generic (from .../linux-image-2.6.32-25-generic_2.6.32-25.45_i386.deb) ...
Done.
Selecting previously deselected package linux-image-generic.
Unpacking linux-image-generic (from .../linux-image-generic_2.6.32.25.27_i386.deb) ...
Selecting previously deselected package linux-image.
Unpacking linux-image (from .../linux-image_2.6.32.25.27_i386.deb) ...
Processing triggers for man-db ...
Setting up wireless-crda (1.12) ...
Setting up linux-image-2.6.32-25-generic (2.6.32-25.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic
dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.
dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.
cp: cannot stat `/lib/udev/hotplug.functions': No such file or directory
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-25-generic /boot/vmlinuz-2.6.32-25-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-25-generic /boot/vmlinuz-2.6.32-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.32-25-generic /boot/vmlinuz-2.6.32-25-generic

Setting up linux-image-generic (2.6.32.25.27) ...
Setting up linux-image (2.6.32.25.27) ...
root@ubuntu:/# sudo update-grub
sudo: unable to resolve host ubuntu
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found memtest86+ image: /boot/memtest86+.bin
done
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ ls /mnt/boot/*2.6-*
ls: cannot access /mnt/boot/*2.6-*: No such file or directory
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: /dev/sda1 already mounted or /mnt busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt
ubuntu@ubuntu:~$ ls /mnt/boot/*2.6*
/mnt/boot/abi-2.6.32-25-generic         /mnt/boot/System.map-2.6.32-25-generic
/mnt/boot/config-2.6.32-25-generic      /mnt/boot/vmcoreinfo-2.6.32-25-generic
/mnt/boot/initrd.img-2.6.32-25-generic  /mnt/boot/vmlinuz-2.6.32-25-generic
ubuntu@ubuntu:~$ for i in /dev/pts /dev /proc /sys / ; do sudo umount /mnt/temp$i ; done
ubuntu@ubuntu:~$ 

```

---

### Post by dfeg on 2010-10-30
I've run the boot info script again to give a little more information
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

/dev/sda1    *          2,048   224,827,391   224,825,344  83 Linux
/dev/sda2         224,829,438   234,440,703     9,611,266   5 Extended
/dev/sda5         224,829,440   234,440,703     9,611,264  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   234,438,655   234,436,608   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        15fb6270-5a57-4769-8f78-b1bfeb76c2dd   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        da36d029-8ecc-461d-815b-c0bf1794cea3   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        30F42A0EF429D6BE                       ntfs       DATAPART1                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/DATAPART1         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 15fb6270-5a57-4769-8f78-b1bfeb76c2dd
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 15fb6270-5a57-4769-8f78-b1bfeb76c2dd
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 15fb6270-5a57-4769-8f78-b1bfeb76c2dd
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=15fb6270-5a57-4769-8f78-b1bfeb76c2dd ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 15fb6270-5a57-4769-8f78-b1bfeb76c2dd
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=15fb6270-5a57-4769-8f78-b1bfeb76c2dd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 15fb6270-5a57-4769-8f78-b1bfeb76c2dd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 15fb6270-5a57-4769-8f78-b1bfeb76c2dd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
/dev/sda5       none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  64.6GB: boot/grub/core.img
  47.4GB: boot/grub/grub.cfg
  77.2GB: boot/initrd.img-2.6.32-25-generic
  77.2GB: boot/vmlinuz-2.6.32-25-generic
  77.2GB: initrd.img
  77.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  d8 1e b5 95 38 b5 74 d1  dc af 65 24 8a 0d b1 46  |....8.t...e$...F|
00000010  72 0f 18 19 e9 50 19 95  89 50 38 1f dd e9 5c b3  |r....P...P8...\.|
00000020  e6 d7 53 68 45 3b 22 40  c8 37 05 38 c6 01 fa 55  |..ShE;"@.7.8...U|
00000030  98 de 45 18 18 1b ba 7c  a4 71 59 73 59 d9 95 2a  |..E....|.qYsY..*|
00000040  6a 2e e5 a0 5b 71 6c 63  20 0c f3 53 91 86 c8 61  |j...[qlc ..S...a|
00000050  cf f7 79 e2 b7 75 a3 17  ee 23 19 45 3b 59 10 ba  |..y..u...#.E;Y..|
00000060  e7 80 58 86 e3 39 e7 34  d9 13 21 78 04 30 38 3d  |..X..9.4..!x.08=|
00000070  c1 a8 97 35 4b 4a c3 4f  96 f6 63 42 86 52 a1 88  |...5KJ.O..cB.R..|
00000080  fe 2e 4e 0d 21 8c 61 b8  62 38 e7 23 81 4e 70 a8  |..N.!.a.b8.#.Np.|
00000090  de ac a5 37 16 e2 c9 23  89 42 fc c5 93 b9 2d d4  |...7...#.B....-.|
000000a0  53 96 03 27 cc 80 ec c9  e7 18 18 aa a4 9f c4 53  |S..'...........S|
000000b0  6a cb 95 16 7c b5 d9 82  40 3b 89 e4 e7 d6 9a b0  |j...|...@;......|
000000c0  92 43 63 3d c0 39 cd 37  56 50 bb 5d 4c dc 2f 7b  |.Cc=.9.7VP.]L./{|
000000d0  3d 49 fc b2 f8 56 f6 6e  98 c5 5e 9a cd 5a 38 d8  |=I...V.n..^..Z8.|
000000e0  71 8c 1e 79 39 af 4f 29  94 a5 3d 65 74 79 79 85  |q..y9.O)..=etyy.|
000000f0  05 ec f9 9a d4 cd 95 fc  a3 b4 f2 c3 24 12 b9 e7  |............$...|
00000100  fc f3 4c 32 ef 0a ce 57  68 04 1c 1f bc 39 ad 33  |..L2...Wh....9.3|
00000110  3c 45 48 54 e4 4c cf 05  85 8f 2a 72 20 44 52 c3  |<EHT.L....*r DR.|
00000120  18 19 24 73 92 0d 4b f6  7d c5 94 05 07 3c fc b5  |..$s..K.}....<..|
00000130  e6 c6 73 6b df 3d 1f 67  4d 26 99 18 b5 24 93 9c  |..sk.=.gM&...$..|
00000140  60 9d b9 00 e4 f3 fe 7f  2a 9b cd 10 2e 58 07 63  |`.......*....X.c|
00000150  9c 15 c7 27 f9 e6 ae 9d  7a 94 da 94 64 64 e8 c6  |...'....z...dd..|
00000160  50 b3 64 7f da 88 02 02  ca 00 f9 5b 23 38 3f d6  |P.d........[#8?.|
00000170  ab cb 7f 0b b1 cb 2b 8c  74 5e 05 7a 74 f3 17 51  |......+.t^.zt..Q|
00000180  72 b6 73 fd 41 29 73 58  ca 95 a3 24 15 43 96 6c  |r.s.A)sX...$.C.l|
00000190  8c 63 e6 1f 4a bd 05 dc  51 6d 2a 88 49 27 3b 78  |.c..J...Qm*.I';x|
000001a0  db fe 7a d6 50 c5 ba 75  9a 46 d5 70 bc f1 46 9a  |..z.P..u.F.p..F.|
000001b0  5e 44 14 6d 19 27 86 e7  24 9a 9e 3b b8 58 00 fe  |^D.m.'..$..;.X..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 92 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by drs305 on 2010-10-30
Thanks for providing the terminal screen. It appears you were able to run the chroot. There were two instances where a command didn't initially work because you used "sudo", which isn't used in a *chroot* environment. It seems to have run regardless so although it introduces a bit of uncertainty for now we'll assume the commands ran.

You might try modifying the kernel options when you see the boot menu. It's possible it's a video problem. When the menu appears, highlight the first entry and press "e", which will open the entry for editing.

On the linux line, try removing the "quiet splash" and adding "nomodeset", so the line looks like this:
> linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=15fb6270-5a57-4769-8f78-b1bfeb76c2dd ro  [COLOR="Red"]nomodeset[/COLOR]

Make the change and while still in the edit mode, press CTRL-x to boot.

This may let you boot if it's a video problem. If it boots, you will have to add the correct video driver as the change you make in the menu is not persistent.

Note: For the results.txt, I changed the "QUOTE" tags to "CODE" tags, which you generate with the # icon. Hope you don't mind, but it makes for easier window management.

---

### Post by dfeg on 2010-10-30
I changed the linux line to nomodeset . After pressing CTRL+x it started to boot and stopped at 
> Begin: Waiting for root file system......



Thanks for the code tip. I see what you mean about windows management.

---

