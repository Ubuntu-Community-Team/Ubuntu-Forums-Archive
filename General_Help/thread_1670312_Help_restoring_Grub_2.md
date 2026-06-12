---
title: "Help restoring Grub 2"
date: 2011-01-18
forum: General Help
---

### Post by sudoer541 on 2011-01-18
I just re-installed xp and Ubuntu is gone!
I followed this method posted [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") and I am very confused!
I used the copy Grub 2 from the Live CD method. What is the Root directory?

---

### Post by sudoer541 on 2011-01-18
here is what I do:


```
sudo fdisk -l
```I get:


```
Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x01e101e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7296    58605088+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ad8fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9356    75146240   83  Linux
/dev/sdb2            9356        9730     3002369    5  Extended
/dev/sdb5            9356        9730     3002368   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 


```Next, I mount my Ubuntu partition by: 

```
sudo mount /dev/sdb1 /mnt
```I get: 
```
mount: /dev/sdb1 already mounted or /mnt busy
mount: according to mtab, /dev/sdb1 is already mounted on /mnt
```Next:

```
sudo grub-install --root-directory=/mnt/ /dev/sdb1
``` <---- this part really confuses me! what is root directory? Do I leave it as is or I specify the root directory? If I need to specify, where is my root directory?
Anyway, using the above command, I get: 



```
mount: /dev/sdb1 already mounted or /mnt busy
mount: according to mtab, /dev/sdb1 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb1
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.


```
What am I doing wrong?

---

### Post by Quackers on 2011-01-18
the last line should be 
```
sudo grub-install --root-directory=/mnt/ /dev/sdb
``` you don't use the partition (sdb1) you use the mbr (--root-directory) of the hard drive (sdb)

---

### Post by sudoer541 on 2011-01-18
> **Quackers said:**
> the last line should be 
```
sudo grub-install --root-directory=/mnt/ /dev/sdb
``` you don't use the partition (sdb1) you use the mbr (--root-directory) of the hard drive (sdb)

It didn't work. :(


So if I understood correctly, I have to specify the location of the MBR? 
If so, what is the location of the MBR? 

I am very confused!:?:

---

### Post by Quackers on 2011-01-18
Not as such.
Let's start from the beginning.
Do you have a bootable system?
If not, can you boot from the Ubuntu live cd/usb?

In either case please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by okanagansage on 2011-01-18
Total rookie here, but isn't this the Windows partition?:

/dev/sda1    Blocks:58 Gb      System: HPFS/NTSF

---

### Post by Quackers on 2011-01-19
> **okanagansage said:**
> Total rookie here, but isn't this the Windows partition?:

/dev/sda1    Blocks:58 Gb      System: HPFS/NTSF

Errrrm, yes, forgive me for my eyes do not see :-) What a dunce I am!
I will edit the post accordingly!
Thank you okanagansage, for the use of your eyes :wink:

---

### Post by sudoer541 on 2011-01-19
Here are the results from the boot script file:






```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   117,210,239   117,210,177   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   150,294,527   150,292,480  83 Linux
/dev/sdb2         150,296,574   156,301,311     6,004,738   5 Extended
/dev/sdb5         150,296,576   156,301,311     6,004,736  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/sdc: 30.0 GB, 30005821440 bytes
255 heads, 62 sectors/track, 926 cylinders, total 14651280 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63        48,194        48,132   0 Empty
/dev/sdc2              48,195    14,651,278    14,603,084   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        965875DC5875BC15                       ntfs       Windows xp                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        58439c55-794b-4fc3-b9e4-45c525acb079   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        0cf732cb-23ec-4273-881d-b36588483238   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc2        9009-5BDB                              vfat       IPOD                          
/dev/sdc         A88B-3652                              vfat       iPod                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/Windows xp        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/58439c55-794b-4fc3-b9e4-45c525acb079 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc2        /media/IPOD              vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /noguiboot 

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set default="12"
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
search --no-floppy --fs-uuid --set 58439c55-794b-4fc3-b9e4-45c525acb079
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
search --no-floppy --fs-uuid --set 58439c55-794b-4fc3-b9e4-45c525acb079
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=4
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 58439c55-794b-4fc3-b9e4-45c525acb079
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=58439c55-794b-4fc3-b9e4-45c525acb079 ro splash quiet vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 58439c55-794b-4fc3-b9e4-45c525acb079
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=58439c55-794b-4fc3-b9e4-45c525acb079 ro single splash quiet vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 58439c55-794b-4fc3-b9e4-45c525acb079
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=58439c55-794b-4fc3-b9e4-45c525acb079 ro splash quiet vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 58439c55-794b-4fc3-b9e4-45c525acb079
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=58439c55-794b-4fc3-b9e4-45c525acb079 ro single splash quiet vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 58439c55-794b-4fc3-b9e4-45c525acb079
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=58439c55-794b-4fc3-b9e4-45c525acb079 ro splash quiet vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 58439c55-794b-4fc3-b9e4-45c525acb079
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=58439c55-794b-4fc3-b9e4-45c525acb079 ro single splash quiet vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 58439c55-794b-4fc3-b9e4-45c525acb079
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=58439c55-794b-4fc3-b9e4-45c525acb079 ro splash quiet vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 58439c55-794b-4fc3-b9e4-45c525acb079
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=58439c55-794b-4fc3-b9e4-45c525acb079 ro single splash quiet vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 58439c55-794b-4fc3-b9e4-45c525acb079
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=58439c55-794b-4fc3-b9e4-45c525acb079 ro splash quiet vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 58439c55-794b-4fc3-b9e4-45c525acb079
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=58439c55-794b-4fc3-b9e4-45c525acb079 ro single splash quiet vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 58439c55-794b-4fc3-b9e4-45c525acb079
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 58439c55-794b-4fc3-b9e4-45c525acb079
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 965875dc5875bc15
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=58439c55-794b-4fc3-b9e4-45c525acb079 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=0cf732cb-23ec-4273-881d-b36588483238 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
tmpfs /tmp tmpfs noexec,defaults,noatime 0 0
tmpfs /var/tmp tmpfs noexec,defaults,noatime 0 0

=================== sdb1: Location of files loaded by Grub: ===================


  34.5GB: boot/grub/core.img
  34.5GB: boot/grub/grub.cfg
  34.5GB: boot/initrd.img-2.6.32-21-generic
  34.5GB: boot/initrd.img-2.6.32-25-generic
  34.6GB: boot/initrd.img-2.6.32-26-generic
   1.2GB: boot/initrd.img-2.6.32-27-generic
  34.6GB: boot/initrd.img-2.6.32-28-generic
  34.4GB: boot/vmlinuz-2.6.32-21-generic
  34.5GB: boot/vmlinuz-2.6.32-25-generic
  34.5GB: boot/vmlinuz-2.6.32-26-generic
  34.5GB: boot/vmlinuz-2.6.32-27-generic
  34.6GB: boot/vmlinuz-2.6.32-28-generic
  38.7GB: grub/core.img
  34.6GB: initrd.img
   1.2GB: initrd.img.old
  34.6GB: vmlinuz
  34.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 08 08 00 02  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  8f 8f df 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  01 00 29 52 36 8b a8 69  50 6f 64 00 4d 45 20 20  |..)R6..iPod.ME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 08  |{......|.N..V@..|
00000070  cd 13 73 05 b9 ff ff 8a  f1 66 0f b6 c6 40 66 0f  |..s......f...@f.|
00000080  b6 d1 80 e2 3f f7 e2 86  cd c0 ed 06 41 66 0f b7  |....?.......Af..|
00000090  c9 66 f7 e1 66 89 46 f8  83 7e 16 00 75 38 83 7e  |.f..f.F..~..u8.~|
000000a0  2a 00 77 32 66 8b 46 1c  66 83 c0 0c bb 00 80 b9  |*.w2f.F.f.......|
000000b0  01 00 e8 2b 00 e9 48 03  a0 fa 7d b4 7d 8b f0 ac  |...+..H...}.}...|
000000c0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000d0  ee a0 fb 7d eb e5 a0 f9  7d eb e0 98 cd 16 cd 19  |...}....}.......|
000000e0  66 60 66 3b 46 f8 0f 82  4a 00 66 6a 00 66 50 06  |f`f;F...J.fj.fP.|
000000f0  53 66 68 10 00 01 00 80  7e 02 00 0f 85 20 00 b4  |Sfh.....~.... ..|
00000100  41 bb aa 55 8a 56 40 cd  13 0f 82 1c 00 81 fb 55  |A..U.V@........U|
00000110  aa 0f 85 14 00 f6 c1 01  0f 84 0d 00 fe 46 02 b4  |.............F..|
00000120  42 8a 56 40 8b f4 cd 13  b0 f9 66 58 66 58 66 58  |B.V@......fXfXfX|
00000130  66 58 eb 2a 66 33 d2 66  0f b7 4e 18 66 f7 f1 fe  |fX.*f3.f..N.f...|
00000140  c2 8a ca 66 8b d0 66 c1  ea 10 f7 76 1a 86 d6 8a  |...f..f....v....|
00000150  56 40 8a e8 c0 e4 06 0a  cc b8 01 02 cd 13 66 61  |V@............fa|
00000160  0f 82 54 ff 81 c3 00 02  66 40 49 0f 85 71 ff c3  |..T.....f@I..q..|
00000170  4e 54 4c 44 52 20 20 20  20 20 20 00 00 00 00 00  |NTLDR      .....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 41 70  |..............Ap|
000001b0  70 6c 65 20 69 50 6f 64  20 20 20 20 20 20 00 01  |ple iPod      ..|
000001c0  01 00 00 fe 3f 02 3f 00  00 00 04 bc 00 00 00 00  |....?.?.........|
000001d0  01 03 0b fe fe 8f 43 bc  00 00 4c d3 de 00 00 00  |......C...L.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc1

00000000  7b 7b 7e 7e 20 20 2f 2d  2d 2d 2d 2d 5c 20 20 20  |{{~~  /-----\   |
00000010  7b 7b 7e 7e 20 2f 20 20  20 20 20 20 20 5c 20 20  |{{~~ /       \  |
00000020  7b 7b 7e 7e 7c 20 20 20  20 20 20 20 20 20 7c 20  |{{~~|         | |
00000030  7b 7b 7e 7e 7c 20 53 20  54 20 4f 20 50 20 7c 20  |{{~~| S T O P | |
00000040  7b 7b 7e 7e 7c 20 20 20  20 20 20 20 20 20 7c 20  |{{~~|         | |
00000050  7b 7b 7e 7e 20 5c 20 20  20 20 20 20 20 2f 20 20  |{{~~ \       /  |
00000060  7b 7b 7e 7e 20 20 5c 2d  2d 2d 2d 2d 2f 20 20 20  |{{~~  \-----/   |
00000070  43 6f 70 79 72 69 67 68  74 28 43 29 20 32 30 30  |Copyright(C) 200|
00000080  31 20 41 70 70 6c 65 20  43 6f 6d 70 75 74 65 72  |1 Apple Computer|
00000090  2c 20 49 6e 63 2e 2d 2d  2d 2d 2d 2d 2d 2d 2d 2d  |, Inc.----------|
000000a0  2d 2d 2d 2d 2d 2d 2d 2d  2d 2d 2d 2d 2d 2d 2d 2d  |----------------|
*
000000f0  2d 2d 2d 2d 2d 2d 2d 2d  2d 2d 2d 2d 2d 2d 2d 00  |---------------.|
00000100  5d 69 68 5b 00 40 00 00  0c 01 03 00 00 00 00 00  |]ih[.@..........|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200



```

---

### Post by wilee-nilee on 2011-01-19
First make sure the sdb hard drive is the first read in the bios. Boot a live Ubuntu cd and run these two commands.
```
sudo mount /dev/sdb1 /mnt
```
then
```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```

Reboot to Ubuntu and run.
```
sudo update-grub
```

---

### Post by Quackers on 2011-01-19
Wilee-nilee's suggestion is the normal way to do it :-)
For some reason you have an extra boot file in your sdb1 partition (/grub/core.img). I don't know where that came from. It may cause problems, but I'm not sure. We'll have to wait and see :wink:

---

### Post by wilee-nilee on 2011-01-19
> **Quackers said:**
> Wilee-nilee's suggestion is the normal way to do it :-)
For some reason you have an extra boot file in your sdb1 partition (/grub/core.img). I don't know where that came from. It may cause problems, but I'm not sure. We'll have to wait and see :wink:

That came from the sdb1 root install instead of sdb, supposedly doesn't cause problems, never did that myself though.

---

### Post by sudoer541 on 2011-01-20
> **wilee-nilee said:**
> First make sure the sdb hard drive is the first read in the bios. Boot a live Ubuntu cd and run these two commands.
```
sudo mount /dev/sdb1 /mnt
```then
```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```Reboot to Ubuntu and run.
```
sudo update-grub
```


I got this:

```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb
/usr/sbin/grub-probe: error: cannot find a device for /mnt//boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ 

```

btw the hard drive is mounted!

---

### Post by sudoer541 on 2011-01-20
> **wilee-nilee said:**
> First make sure the sdb hard drive is the first read in the bios. Boot a live Ubuntu cd and run these two commands.
```
sudo mount /dev/sdb1 /mnt
```then
```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```Reboot to Ubuntu and run.
```
sudo update-grub
```


I got this:

```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb
/usr/sbin/grub-probe: error: cannot find a device for /mnt//boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ 

```

btw the hard drive is mounted!

EDIT: I am using the Live CD.

---

### Post by sudoer541 on 2011-01-20
> **wilee-nilee said:**
> First make sure the sdb hard drive is the first read in the bios. Boot a live Ubuntu cd and run these two commands.
```
sudo mount /dev/sdb1 /mnt
```then
```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```Reboot to Ubuntu and run.
```
sudo update-grub
```


I got this:

```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb
/usr/sbin/grub-probe: error: cannot find a device for /mnt//boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ 

```

btw the hard drive is mounted!

EDIT: I am using the Live CD.

---

### Post by wilee-nilee on 2011-01-20
So as is now when you turn on the computer it goes straight to XP?

Is the sdb drive first in the bios to be read?

You might download the supergrub disc #2 and see if it will boot you into Ubuntu to run.
sudo update-grub
And see if that gets you in shape. 
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

From there you can also purge grub and reinstall it and reload the mbr=sdb again if needed.

If the supergrub gets you in, but the update-grub command still has you not seeing a grub menu when you are sure the sdb drive is booting then look to this guide to purge and reload grub. The grub files that were added extra to the Ubuntu sdb1 partition should not be a problem but anything is possible. Top of the thread, from the normal OS.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Is kind of hard really to tell what is going on since it is unconfirmed what the computer is doing actually, other then my Ubuntu is gone. So describe if you can exactly whats going on, if none of this works.

---

### Post by Quackers on 2011-01-20
You've got one too many / in the command
```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt[COLOR="Red"]/[/COLOR] /dev/sdb[COLOR="Black"][/COLOR]
```
take out the red one and try again.

It should be ```
sudo grub-install --root-directory=/mnt /dev/sdb
```

---

### Post by wilee-nilee on 2011-01-20
> **Quackers said:**
> You've got one too many / in the command
```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt[COLOR="Red"]/[/COLOR] /dev/sdb[COLOR="Black"][/COLOR]
```
take out the red one and try again.

It should be ```
sudo grub-install --root-directory=/mnt /dev/sdb
```

I looked at the commands, and didn't see any problems the / is correct in his set.

I still could be missing who knows what though.;)

---

### Post by Quackers on 2011-01-20
OP's set
```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb
/usr/sbin/grub-probe: error: cannot find a device for /mnt//boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
```

There should be no / immediately after --root-directory=/mnt/

---

### Post by wilee-nilee on 2011-01-20
Run the grub-install command as described below. This will reinstall the GRUB 2 files on the mounted partition to the proper location and to the MBR of the designated device.

sudo grub-install --root-directory=/mnt/ /dev/sdX
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Maybe I'm missing something, or just giddy from finding out I'm one class from filling my college major requirements.;)

I think we are both first concerned that the information is correct for the OP.:)

---

### Post by Quackers on 2011-01-20
Absolutely wilee-nilee.
I see what you mean. The page you linked to shows the command that you are showing above. However I have always used drs305's guide which does not include a / after /mnt
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
I presume it depends on where you mount to /mnt or /mnt/

I don't know whether one is right and one is wrong, or whether both are right!
Very odd, I think you'll agree :-)

---

### Post by sudoer541 on 2011-01-22
Solved!

I re-installed ubuntu 10.04 from scratch. I guess Windows and Ubuntu are not that different when it comes to corrupted files.

---

