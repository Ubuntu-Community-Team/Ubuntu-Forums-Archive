---
title: "No GRUB with Windows XP and Maverick Meerkat dual boot"
date: 2010-12-24
forum: General Help
---

### Post by Ender of Games on 2010-12-24
On this old P4 comp I had a somewhat broken XP removed for Ubuntu, opting for the 32-bit 10.10 after it had came out. The CD booted perfectly. I had another XP CD and I was going to dual boot the two.

I made sure that I had XP installed first, then I re-installed Ubuntu. I gave XP 160 GB, and Ubuntu 40 GB, both of which are more than enough. Worked great.

But then I restarted the computer, expecting GRUB to be in control. But it isn't, and I can't boot to the partition that Ubuntu is on. I can clearly see the files now that I have booted with the CD, again. 

I attempted to reinstall GRUB, manually, using some info I found:  

```
sudo -i
mount /dev/sda6 /mnt
grub-install --root-directory=/mnt/ /dev/sda

```

...where sda6 is where Ubuntu had been installed. The message I got back was simply 
```
Installation finished. No error reported.
```
a couple of seconds later. But upon restart, XP booted again. 

I watched many videos, and read many tutorials on dual booting 10.10, and all of them seemed to work at this point. I really have no idea what I have done differently, or why it won't load GRUB on this computer. Can anyone suggest something to try next? 

Thanks!

---

### Post by mikewhatever on 2010-12-24
Are there two hard disks by any chance? Can you post the output of the following from the live cd.

sudo fdisk -l

---

### Post by Ender of Games on 2010-12-25
Both of the OS installed are on one hard drive, partitioned between the two, though there is a second hard drive. 

I hope this is what you were looking for: 

```
Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00005e6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14269   114612203+   7  HPFS/NTFS
/dev/sda2           14269       19930    45472769    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5           19116       19930     6538240   82  Linux swap / Solaris
/dev/sda6           14269       18912    37289984   83  Linux
/dev/sda7           18912       19116     1637376   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x65d47c98

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      243201  1953512001    7  HPFS/NTFS


```

---

### Post by wilee-nilee on 2010-12-25
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

The script will give us what is where including the mbr information and boot files present.

---

### Post by Ender of Games on 2010-12-26
All of the text? Woo hoo!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

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
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   229,224,469   229,224,407   7 HPFS/NTFS
/dev/sda2         229,226,494   320,172,031    90,945,538   5 Extended
/dev/sda5         307,095,552   320,172,031    13,076,480  82 Linux swap / Solaris
/dev/sda6         229,226,496   303,806,463    74,579,968  83 Linux
/dev/sda7         303,808,512   307,083,263     3,274,752  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 3,907,024,064 3,907,024,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6424D12624D0FC4C                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        ba431b0a-dcd5-46a5-8944-bec2ee2b42a6   swap                                     
/dev/sda6        37b11652-b670-4677-abef-2eb07534dd43   ext4                                     
/dev/sda7        6cf7e66d-7b80-4c12-b09b-59326dbea50c   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        34C8C782C8C7413A                       ntfs       Tubrculosis                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 37b11652-b670-4677-abef-2eb07534dd43
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 37b11652-b670-4677-abef-2eb07534dd43
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 37b11652-b670-4677-abef-2eb07534dd43
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=37b11652-b670-4677-abef-2eb07534dd43 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 37b11652-b670-4677-abef-2eb07534dd43
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=37b11652-b670-4677-abef-2eb07534dd43 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 37b11652-b670-4677-abef-2eb07534dd43
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 37b11652-b670-4677-abef-2eb07534dd43
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 34c8c782c8c7413a
    drivemap -s (hd0) ${root}
    chainloader +1
}
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
UUID=37b11652-b670-4677-abef-2eb07534dd43 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=6cf7e66d-7b80-4c12-b09b-59326dbea50c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 143.3GB: boot/grub/core.img
 130.4GB: boot/grub/grub.cfg
 118.2GB: boot/initrd.img-2.6.35-22-generic
 143.3GB: boot/vmlinuz-2.6.35-22-generic
 118.2GB: initrd.img
 143.3GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptOut 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  e6 c5 f0 76 90 5e fa 02  a1 43 b5 19 c5 aa 84 9e  |...v.^...C......|
00000010  bf a8 b4 15 9e e6 c5 ba  2f 10 74 52 61 32 da e6  |......../.tRa2..|
00000020  5b 87 23 cb bf 50 a9 ce  12 a6 e6 e5 ca 47 10 6c  |[.#..P.......G.l|
00000030  b7 f5 50 3d 16 bd f3 3a  b9 98 62 6b 5e b9 8f c2  |..P=...:..bk^...|
00000040  34 64 66 25 aa 2d 38 b5  33 60 5a 18 79 0d 93 2d  |4df%.-8.3`Z.y..-|
00000050  d7 bc 9e eb 81 2d e2 16  00 f2 1c db ad f2 e2 84  |.....-..........|
00000060  27 e1 7f c5 54 69 de ef  fb 40 63 3c c6 3b ad 4d  |'...Ti...@c<.;.M|
00000070  3b e1 3f 4d a6 67 92 a2  07 0e 53 f3 e9 cb 0f 6c  |;.?M.g....S....l|
00000080  24 ae 02 00 43 8c 51 f9  a3 3c b2 c9 fd 5b 50 3d  |$...C.Q..<...[P=|
00000090  1c fd 12 15 5a 61 96 58  68 85 4b 0f 01 70 a9 bf  |....Za.Xh.K..p..|
000000a0  c7 1a dd cf 67 99 f8 25  4c b5 a6 ac 23 5e 03 01  |....g..%L...#^..|
000000b0  22 7b f0 b6 dd ef 88 16  59 89 a4 47 01 57 28 d7  |"{......Y..G.W(.|
000000c0  94 0f 71 86 8c a3 2b 6a  90 5b da 94 0d 6b 5e a3  |..q...+j.[...k^.|
000000d0  4d 54 23 d6 10 4d f9 cd  5f 34 86 7f 7a 0d ba bc  |MT#..M.._4..z...|
000000e0  74 88 68 ee 3c 06 9f c8  22 fb 69 be 3f 31 e2 b7  |t.h.<...".i.?1..|
000000f0  37 c1 01 57 d2 de 35 4b  d7 05 64 91 5c 3f 99 a6  |7..W..5K..d.\?..|
00000100  62 f0 17 c8 78 f1 2f 42  23 7f cd 2c ba bc ea b5  |b...x./B#..,....|
00000110  2f f1 89 2c 4d 65 ea 11  eb a5 fd 7b cf cc a8 b8  |/..,Me.....{....|
00000120  2b 5f e7 e1 a7 c5 6c 4d  4d 14 07 32 d2 38 08 ad  |+_....lMM..2.8..|
00000130  b8 fb f5 81 34 a7 0b a0  32 6d 15 9a da f4 39 10  |....4...2m....9.|
00000140  0c b2 8d 62 65 5e 85 80  08 18 71 34 e8 e7 5c 08  |...be^....q4..\.|
00000150  76 db ee 41 da 3e 25 bc  25 48 e2 a7 05 cf 86 10  |v..A.>%.%H......|
00000160  19 72 00 0e aa 9d 2f ab  33 2b 88 3e a5 40 24 d2  |.r..../.3+.>.@$.|
00000170  da 2d 4b a3 01 a9 8d bd  1f 7c 7f 75 0d 11 26 e0  |.-K......|.u..&.|
00000180  69 61 bb 74 c8 28 7d 56  8b 3a 39 5f 92 37 0c fd  |ia.t.(}V.:9_.7..|
00000190  35 98 12 45 96 6b 1d 32  e3 b0 af ac 76 06 53 26  |5..E.k.2....v.S&|
000001a0  78 df e7 d4 ce 51 91 6b  4c a6 b6 e1 b8 ae 10 a4  |x....Q.kL.......|
000001b0  9e 43 88 57 da 23 6b 72  d5 38 d2 41 5e 22 00 cf  |.C.W.#kr.8.A^"..|
000001c0  e5 ff 82 c8 ef ff 02 30  a4 04 00 88 c7 00 00 fe  |.......0........|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 00 72 04 00 00  |............r...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wilee-nilee on 2010-12-26
So if it is booting straight into XP are you sure it's not booting the sdb drive rather then sda. take the bootflag off of sdb by using gparted on a live Ubuntu cd. make sure the sda is first in the bios.

You have 2 swaps sda5 and sda7 as well.

---

### Post by Ender of Games on 2010-12-26
I went into the BIOS, and checked the boot priority, to find that the correct hard drive was on the list. So I went to hard disk priority, and found that the wrong drive was primary. Restarted immediately, and it worked absolutely beautifully. 

Thank you very much!

---

### Post by wilee-nilee on 2010-12-26
> **Ender of Games said:**
> I went into the BIOS, and checked the boot priority, to find that the correct hard drive was on the list. So I went to hard disk priority, and found that the wrong drive was primary. Restarted immediately, and it worked absolutely beautifully. 

Thank you very much!

Cool.:)

---

### Post by drewboy70 on 2011-02-19
I am seeking help here.  I have plenty of experience with M$ products but have long wanted to get into a Linux based OS to learn it.  I tried with Mandriva a while back, but didn't have the time to figure out what was going wrong so I abandoned the attempt.  Now I have some extra time and figured I'd try Ubuntu.  I did my research and pre-formatted my hard drive to accommodate both my XP OS and the Ubuntu OS.  I put 40gb NTFS for XP (+10gb unformatted for growing either the primary or the extended partition later), I put another 40gb NTFS for personal data, 20gb ext4 for Ubuntu 10.10, 4gb for linux-swap, and 40.01gb of FAT32 for shared.

I put my XP install back on the drive from an image and booted into it fine.  Then I installed Ubuntu 10.10 and got the grub error message:
 
error: out of disk grub rescue> 
It didn't allow any commands to be entered, so I used my XP disk to repair the Windows XP MBR.

I have tried to get the grub working again according to the steps given by multiple thread here and elsewhere, hoping to get the grub loader screen showing the options to choose XP or Ubuntu, but it seems I run into a problem somewhere every time.

I don't want to use wubi, I want to have the systems to be largely independent of each other and I simply can't see the logic (well, I can see it, but it seems less than truly logical) to running Ubuntu alongside or inside Windows--kind of defeats the point of being a completely different OS.

I have attached a report generated when I ran the program: boot_info_script055.sh that shows what I have going on.  Also, I attached a System Information Report in case anyone finds that helpful.

AND THANK YOU, in advance for helping me out.  Apologies if I have breached posting etiquette in any way. :)
[B]
_Here's the text for it:_[/B]

  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

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

/dev/sda1    *             63    83,907,494    83,907,432   7 HPFS/NTFS
/dev/sda2         104,861,694   188,766,207    83,904,514   5 Extended
/dev/sda5         104,861,696   188,766,207    83,904,512   7 HPFS/NTFS
/dev/sda3         262,166,528   304,111,615    41,945,088  83 Linux
/dev/sda4         304,111,616   312,498,175     8,386,560  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5ED42D2FD42D0B3B                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        d9a877e6-b5a1-438d-9f2f-3e30733797a2   ext4       Ubuntu                        
/dev/sda4        c2fc458b-ebd3-4342-ae7f-6fedce30d8fb   swap       Linux Swap                    
/dev/sda5        4EF1F72204F8A9FA                       ntfs       Personal Data                 
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/5ED42D2FD42D0B3B  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set d9a877e6-b5a1-438d-9f2f-3e30733797a2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set d9a877e6-b5a1-438d-9f2f-3e30733797a2
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set d9a877e6-b5a1-438d-9f2f-3e30733797a2
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d9a877e6-b5a1-438d-9f2f-3e30733797a2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set d9a877e6-b5a1-438d-9f2f-3e30733797a2
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d9a877e6-b5a1-438d-9f2f-3e30733797a2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set d9a877e6-b5a1-438d-9f2f-3e30733797a2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set d9a877e6-b5a1-438d-9f2f-3e30733797a2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5ed42d2fd42d0b3b
    drivemap -s (hd0) ${root}
    chainloader +1
}
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=d9a877e6-b5a1-438d-9f2f-3e30733797a2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=c2fc458b-ebd3-4342-ae7f-6fedce30d8fb none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 138.7GB: boot/grub/core.img
 153.7GB: boot/grub/grub.cfg
 147.9GB: boot/initrd.img-2.6.35-22-generic
 134.6GB: boot/vmlinuz-2.6.35-22-generic
 147.9GB: initrd.img
 134.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  01 a3 94 62 f1 86 c2 65  e8 07 ce 03 00 90 3a 12  |...b...e......:.|
00000010  00 00 08 00 00 00 22 07  27 87 9f f0 e2 de 1f ea  |......".'.......|
00000020  82 61 56 29 4f 10 43 2c  5e 8d d1 9d 07 55 5e 68  |.aV)O.C,^....U^h|
00000030  99 d7 25 cf b0 00 7b 30  b6 0d b4 19 16 90 eb 08  |..%...{0........|
00000040  ae 8d a2 29 21 c4 62 73  48 83 ec 48 83 64 24 50  |...)!.bsH..H.d$P|
00000050  00 48 8d 05 19 5a 03 00  48 89 44 24 58 e8 84 5a  |.H...Z..H.D$X..Z|
00000060  03 00 f6 05 a7 a7 05 00  01 74 20 48 8b 0d 96 f1  |.........t H....|
00000070  05 00 48 83 64 24 20 00  48 8d 15 e9 d9 03 00 45  |..H.d$ .H......E|
00000080  33 c9 45 33 c0 ff 15 dd  d8 03 00 48 8d 0d 8e f0  |3.E3.......H....|
00000090  05 00 ff 15 e0 d7 03 00  48 8d 0d 81 f9 05 00 ff  |........H.......|
000000a0  15 d3 d7 03 00 48 8d 0d  f4 f0 05 00 ff 15 c6 d7  |.....H..........|
000000b0  03 00 c7 05 48 a7 05 00  01 00 00 00 e8 5f cc 03  |....H........_..|
000000c0  00 90 1c 12 00 00 09 00  00 00 85 c0 78 13 e8 86  |............x...|
000000d0  fd ff ff e8 3c cd 03 00  90 1c 12 00 00 09 00 00  |....<...........|
000000e0  00 83 64 24 3c 00 f6 05  23 a7 05 00 01 48 8d 44  |..d$<...#....H.D|
000000f0  24 50 48 89 44 24 30 c7  44 24 38 04 00 00 00 74  |$PH.D$0.D$8....t|
00000100  27 48 8b 0d 00 f1 05 00  48 8d 44 24 30 48 8d 15  |'H......H.D$0H..|
00000110  64 d9 03 00 41 b9 01 00  00 00 45 33 c0 48 89 44  |d...A.....E3.H.D|
00000120  24 20 ff 15 40 d8 03 00  48 83 c4 48 c3 0b 45 d1  |$ ..@...H..H..E.|
00000130  e4 c3 53 ad 7e 91 74 01  59 81 18 8b 9d 4f 4e 13  |..S.~.t.Y....ON.|
00000140  a3 67 75 a9 33 ec f0 22  5a 0b 0c cc 99 d9 02 81  |.gu.3.."Z.......|
00000150  57 c4 0a 58 5f b4 be 72  bf fa ce 38 7e 62 59 f1  |W..X_..r...8~bY.|
00000160  8f da 9c fa 8d 53 cb 05  0c 3a 69 a9 b6 be 42 ff  |.....S...:i...B.|
00000170  16 85 04 6d 29 4c bb 3b  eb 04 85 95 fc 67 b9 6e  |...m)L.;.....g.n|
00000180  f6 56 03 9b af d5 67 2d  6d 5f a0 87 8c 3f 0e 0e  |.V....g-m_...?..|
00000190  95 c4 f3 d8 b4 06 15 f4  9f 1a 6d d3 c4 f3 99 3e  |..........m....>|
000001a0  b5 2c 66 46 15 51 5d b3  8f 1a 85 0e 21 96 d7 b2  |.,fF.Q].....!...|
000001b0  d4 72 fa 85 16 06 bc 2c  c5 2f e1 63 12 6e 00 56  |.r.....,./.c.n.V|
000001c0  d8 fe 07 d2 d8 fe 02 00  00 00 00 48 00 05 00 00  |...........H....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by pattais on 2011-03-27
I am having a very similar problem - with some minor variations:  I am trying to create a bootable USB hard-disk with both windows xp and linux on it.  I installed from the live CD into the USB drive and as far as I can see everything checks out: grub is properly installed, grub.cfg is pointing to the right devices.

My laptop bios has the right boot order - CD / USB Hard Drive / Hard Drive.

Either the USB hard drive Grub menu will not come up at all and the system boots into my /dev/sda hard drive after a error: out of disks message or the System attemps to boot into the USB drive and hangs - without a grub menu.

RESULTS.txt from boot_info_script is attached.

Any help will be greatly appreciated. I suspect I am missing something trivial, but for the life of me I cannot figure it out.

---

