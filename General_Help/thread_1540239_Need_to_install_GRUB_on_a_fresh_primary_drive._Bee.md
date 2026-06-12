---
title: "Need to install GRUB on a fresh primary drive. Been searching for an answer for days."
date: 2010-07-27
forum: General Help
---

### Post by dbz253 on 2010-07-27
I have two hard drives in my computer. 

I had windows xp installed on the primary drive, and Ubuntu installed on the secondary drive.

I swapped out the primary drive with a new one that also has windows xp, but no trace of GRUB whatsoever.

Now my computer boots directly to windows xp.

For the past 3 days, I have been trawling through forum and blog posts trying to find a way to get GRUB installed on my primary drive without completely reinstalling Ubuntu.

I have finally given up and decided to ask for help with my specific problem. I will provide info that other people requested for similar problems.

---

### Post by wilee-nilee on 2010-07-27
From a live ubuntu cd run and post the bootscript in my signature and post in code tags as described.

---

### Post by dbz253 on 2010-07-27
**transcript of grub commands:**
```

grub> find /boot/grub/stage1

Error 15: File not found

grub> root (hd0,0)

grub> setup (hd0)

Error 17: Cannot mount selected partition

grub> 


```

[B]sudo fdisk -l
[/B]```

Disk /dev/sda: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5eaff47a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5168    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ef0a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14220   114213888   83  Linux
/dev/sdb2           14220       14594     3004417    5  Extended
/dev/sdb5           14220       14594     3004416   82  Linux swap / Solaris

```

---

### Post by dbz253 on 2010-07-27
> **wilee-nilee said:**
> from a live ubuntu cd run and post the bootscript in my signature and post in code tags as described.

[B]results.txt
[/B]```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

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
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,140,159    78,140,097   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   228,429,823   228,427,776  83 Linux
/dev/sdb2         228,431,870   234,440,703     6,008,834   5 Extended
/dev/sdb5         228,431,872   234,440,703     6,008,832  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D004877604875DFA                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        d38db6ac-2e30-44b6-8310-fec45cefca9b   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        4d270c76-7353-4027-9e5a-5474f8ce2580   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

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
search --no-floppy --fs-uuid --set d38db6ac-2e30-44b6-8310-fec45cefca9b
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
search --no-floppy --fs-uuid --set d38db6ac-2e30-44b6-8310-fec45cefca9b
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
    search --no-floppy --fs-uuid --set d38db6ac-2e30-44b6-8310-fec45cefca9b
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=d38db6ac-2e30-44b6-8310-fec45cefca9b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d38db6ac-2e30-44b6-8310-fec45cefca9b
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=d38db6ac-2e30-44b6-8310-fec45cefca9b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d38db6ac-2e30-44b6-8310-fec45cefca9b
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=d38db6ac-2e30-44b6-8310-fec45cefca9b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d38db6ac-2e30-44b6-8310-fec45cefca9b
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=d38db6ac-2e30-44b6-8310-fec45cefca9b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d38db6ac-2e30-44b6-8310-fec45cefca9b
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=d38db6ac-2e30-44b6-8310-fec45cefca9b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d38db6ac-2e30-44b6-8310-fec45cefca9b
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=d38db6ac-2e30-44b6-8310-fec45cefca9b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d38db6ac-2e30-44b6-8310-fec45cefca9b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set d38db6ac-2e30-44b6-8310-fec45cefca9b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 52c435c3c435a9dd
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
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=4d270c76-7353-4027-9e5a-5474f8ce2580 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  60.2GB: boot/grub/core.img
  96.8GB: boot/grub/grub.cfg
    .2GB: boot/initrd.img-2.6.32-21-generic
  60.2GB: boot/initrd.img-2.6.32-23-generic
  60.3GB: boot/initrd.img-2.6.32-24-generic
  60.2GB: boot/vmlinuz-2.6.32-21-generic
  60.2GB: boot/vmlinuz-2.6.32-23-generic
  60.2GB: boot/vmlinuz-2.6.32-24-generic
  60.3GB: initrd.img
  60.2GB: initrd.img.old
  60.2GB: vmlinuz
  60.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  1e 9c be 16 85 d4 51 56  48 e6 d0 93 02 c2 c3 c1  |......QVH.......|
00000010  88 5d 79 a0 78 33 49 c6  06 9c 0b 12 45 ed 27 f4  |.]y.x3I.....E.'.|
00000020  20 4f 30 31 44 45 4f bd  74 46 52 00 04 62 00 10  | O01DEO.tFR..b..|
00000030  94 6b 33 cd f4 c4 d5 76  a3 3f d7 ff fb b0 64 08  |.k3....v.?....d.|
00000040  02 05 a9 70 5a 23 09 36  50 56 8b 2c 0f 24 05 77  |...pZ#.6PV.,.$.w|
00000050  55 61 a3 6d 8c 30 cd ca  4e 33 ec 14 96 22 d9 f3  |Ua.m.0..N3..."..|
00000060  e9 60 39 47 77 04 f7 3d  ca a5 91 d4 2a 99 81 16  |.`9Gw..=....*...|
00000070  0d c2 68 12 85 20 c4 ae  4a 18 fb 99 41 1d 69 f9  |..h.. ..J...A.i.|
00000080  c9 e0 c8 de 92 4d cb cd  b6 d0 3b a3 4d 72 42 e8  |.....M....;.MrB.|
00000090  e7 47 8b 24 7a 0f 2e c1  14 e6 26 0c a0 26 49 18  |.G.$z.....&..&I.|
000000a0  f9 a2 3b 49 01 55 1d 24  a6 97 5d a2 cd ea 23 b4  |..;I.U.$..]...#.|
000000b0  89 b8 be 69 4c 34 99 73  c7 a5 cf 21 c9 06 a1 18  |...iL4.s...!....|
000000c0  90 23 55 40 c1 86 ea de  75 94 b1 d0 86 5a a9 03  |.#U@....u....Z..|
000000d0  2e c1 00 a4 c2 ce c2 8d  53 bc ba 35 f9 85 da f5  |........S..5....|
000000e0  38 48 fc 46 1d 12 cf 30  d9 99 da 2b 9d 52 d2 91  |8H.F...0...+.R..|
000000f0  39 be 85 dd 58 3e 6b 4e  7c a7 a7 fc c7 d3 04 2f  |9...X>kN|....../|
00000100  9d 3a 41 94 03 ba 4c c3  80 00 bc 54 09 9f 82 6c  |.:A...L....T...l|
00000110  ac 6a a8 48 be 54 bc 11  ed ec ed 08 14 e3 48 18  |.j.H.T........H.|
00000120  61 61 16 3f ff d8 ce 53  8b 14 82 e4 02 83 0c 15  |aa.?...S........|
00000130  da 94 76 5e fb 74 46 ed  f9 3b dd 5d d1 48 63 b6  |..v^.tF..;.].Hc.|
00000140  a4 75 6b a7 33 25 2f d9  56 ba 77 4d bc 88 e8 27  |.uk.3%/.V.wM...'|
00000150  8d 51 0e 13 6c 66 94 86  f7 af d0 00 52 d0 00 02  |.Q..lf......R...|
00000160  15 9a 96 d6 7f 6f 55 a7  0c c4 08 ad 95 b3 a4 bb  |.....oU.........|
00000170  20 cb 2f fb a4 1d db 1d  c7 91 f5 28 4a 23 af 2d  | ./........(J#.-|
00000180  09 a6 a7 e5 42 f2 53 83  e1 8f f1 81 d5 3a 56 43  |....B.S......:VC|
00000190  55 f0 57 d3 ad 39 78 88  72 91 10 8c bd 93 f5 00  |U.W..9x.r.......|
000001a0  e8 94 89 f6 1d 12 47 03  80 0d 4b 06 0a b2 44 a1  |......G...K...D.|
000001b0  28 04 44 e2 f9 48 0c 63  9a 07 01 03 81 13 00 fe  |(.D..H.c........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 b0 5b 00 00 00  |............[...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

**EDIT:** changed "quote" tags to "code" tags as requested

---

### Post by oldfred on 2010-07-27
Install grub2 from LiveCD, Ubuntu install on sdb1 and want grub2 in drive sda's MBR:
Find linux partition, change sdb1 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

I might also install to sdb just incase you remove the sda drive, you could set sdb as master and then it would boot. Right after the install to sda you could run this also:
sudo grub-install --root-directory=/mnt /dev/sdb

---

### Post by wilee-nilee on 2010-07-27
> **oldfred said:**
> Install grub2 from LiveCD, Ubuntu install on sdb1 and want grub2 in drive sda's MBR:
Find linux partition, change sdb1 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

I might also install to sdb just incase you remove the sda drive, you could set sdb as master and then it would boot. Right after the install to sda you could run this also:
sudo grub-install --root-directory=/mnt /dev/sdb

+1 makes sense for disc swapping, and getting everything working.

---

### Post by dbz253 on 2010-07-27
> **oldfred said:**
> Install grub2 from LiveCD, Ubuntu install on sdb1 and want grub2 in drive sda's MBR:
Find linux partition, change sdb1 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

I might also install to sdb just incase you remove the sda drive, you could set sdb as master and then it would boot. Right after the install to sda you could run this also:
sudo grub-install --root-directory=/mnt /dev/sdb

HELL YES! THANK YOU! THANK YOU!! THANK YOU!!! :D

If it's not too much trouble, would you mind explaining the following lines and why they are needed?

**# mkdir /mnt/sdb1** *I'm assuming this makes the directory "/mnt/sdb1", but where and why? I also know that "/dev/sdb1" is my second drive, even though the folder "sdb1" is not in my "dev" folder (this has always confused me).*

**# mount /dev/sdb1 /mnt** *Does this just mount my secondary drive in the temporary "/mnt" directory used by the live CD? If so, why "sdb1" instead of "sda1"?*

**grub-install --root-directory=/mnt /dev/sda** *Completely lost here...*


Thanks again! I was so close to formatting and starting from scratch.

---

### Post by oldfred on 2010-07-27
When you install grub to the MBR to boot it has to know where to look to find the rest of grub's files. 

In Ubuntu you have to make a mount point to mount anything. Then you mount something to that mount point. Now most is done automatically but you still have to do it if you are manually setting something up.

Then you have to tell grub what drive sda, sdb, sdc etc that you want grub installed to the MBR.

INfo on grub:
 GRUB 2  has three main parts plus a boot loader installed to the MBR:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

MBR - master boot record, also type of partition structure of a hard drive with a MBR, and four primary partitions. This is the msdos standard since IBM released the PC in the early '80s.

---

