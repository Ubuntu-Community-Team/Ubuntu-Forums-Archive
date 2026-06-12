---
title: "HDD and win7  problem"
date: 2011-01-08
forum: General Help
---

### Post by akeee on 2011-01-08
Hello and thank you for tryng helping me.I am new in usign UBUNTU OS. I have 2 HDD : At the first HDD (SATA) in one partition is installedted win 7 and ubuntu is installed at secound HDD (IDE). When i installed Ubuntu from CD i choose that ubuntu to use whole HDD (IDE) . The problem is: after i install  ubuntu i can't boot with win, doesnt start up a boot menu, go straigh in ubuntu. I check in ubuntu and all files in HDD (SATA - win 7 hdd) are OK, the same. I read on forums,how to corect this and i found : with boot cd win 7 enter in Repair menu, and there win doesnt_ recognize  _preview installations.There for i read more and at command prompt-ul (same in Repair menu): i try to bootrec.exe /rebuildbcd and found nothing, after this i choose "diskpart" and i set something wrong (obvios) because now when a enter in ubuntu OS doesnt recognize the other HDD (SATA) at all. 

> sudo fdisk -l :
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cd21a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table


If i try:
>fdisk /dev/sdb

Unable to open /dev/sdb

Please help, and sorry for my english.

---

### Post by searchfgold6789 on 2011-01-08
Well first of all, it may help if you gave us the output (RESULTS.TXT file) of meirfera's Bootscript which is at <bootscript.sourceforge.net>.
I am thinking that you either wrote some sort of partition over the pre-existing Windows one, or you raised the Hidden flag on the partition. I have not heard much about the hidden flag, so maybe you could Google it for more information, maybe you can find a way to determine if you raised it or not.
If you overwrote the partition, look up how to use testdisk to recover your files and maybe your entire system. In short you
[LIST]
[*]Boot from a Live Cd
[*]Open up a terminal
[*]type ```
sudo apt-get install testdisk
```
[*]type ```
sudo testdisk
```
[*]search for a partition of type Intel
[*]Type N to bypass the vista search
[*]Select the partition
[*]Type P
[*]Recover some or all of the files to a folder on your ubuntu partition
[*]Put them back onto the partition and fix the boot sector/mbr from the Windows CD
[/LIST]
It worked for my friend. He lost windows but I recovered the files and wrote them back to the partition, then fixed his MBR.
I might have gone off on a tangent with the mini-testdisk-tutorial, so first post the results of the bootscript.

---

### Post by akeee on 2011-01-08
Thank you. I remember the command thats damage : in command prost ( at repiar win 7 boot): and i select disc 1 ( before was disk 0 ). disk 1- HDD SATA with win and disk 0 - IDE with ubuntu. let me try testdisk i will post. Thank you

---

### Post by akeee on 2011-01-08
how to post boot script? i install the program and i recover same important date ( they was on other partition than win 7 ).

---

### Post by theasprint on 2011-01-08
Hi,

To use the bootscript (or more commonly known as bootinfoscript):

1. Go and boot from a LiveCD (that means Try Ubuntu without Changes)

2. Have internet connection and download the bootinfoscript from the link in my signature below.

3. Follow the instructions in the bootinfoscript website. For your case I think you should make sure that the 2 HDDs are connected and working. The bootinfoscript will then give an overview of the whole system.

4. Post the results (results.txt) in this thread, use the [CODE] tags to wrap them up in a nice box.

---

### Post by akeee on 2011-01-08
With testdisk : i succes made apear the partition with my data (music, movies etc) but,  the same method ( testdisk - write and reboot) that i use for this doesnt work with the partition with win 7 on it. At that partition when i selected apear this:
Disk /dev/mapper/nvidia_hiaachbj1 - 36 GB / 34 GiB - CHS 71681967 1 1
Current partition structure:
     Partition                  Start        End    Size in sectors

Warning: Incorrect number of heads/cylinder 255 (NTFS) != 1 (HD)
Warning: Incorrect number of sectors per track 63 (NTFS) != 1 (HD)
 1 * HPFS - NTFS                 1985   71679936   71677952
 

Right away with bootscript, if u still need it.
I will make a deeper search and post the result

---

### Post by akeee on 2011-01-08
result of boot script:
```

         Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Testdisk is installed in the MBR of /dev/mapper/nvidia_hiaachbj

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

nvidia_hiaachbj1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

nvidia_hiaachbj2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   149,843,967   149,841,920  83 Linux
/dev/sdb2         149,846,014   156,301,311     6,455,298   5 Extended
/dev/sdb5         149,846,016   156,301,311     6,455,296  82 Linux swap / Solaris


Drive: nvidia_hiaachbj ___________________ _____________________________________________________

Disk /dev/mapper/nvidia_hiaachbj: 500.1 GB, 500107860992 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773166 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/nvidia_hiaachbj1   *             63    71,682,029    71,681,967   7 HPFS/NTFS
/dev/mapper/nvidia_hiaachbj2         71,682,030   976,768,064   905,086,035   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/nvidia_hiaachbj1: PTTYPE="dos" 
/dev/mapper/nvidia_hiaachbj2 EAE056A2E0567533                       ntfs       New Volume                    
/dev/mapper/nvidia_hiaachbj: PTTYPE="dos" 
/dev/sda                                                nvidia_raid_member                               
/dev/sdb1        695930db-21e7-4158-bfa2-2f52e3f8790b   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        b6c3686b-cff3-4f0c-937d-c07bd945f6a5   swap                                     
/dev/sdb: PTTYPE="dos" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
nvidia_hiaachbj
nvidia_hiaachbj1
nvidia_hiaachbj2

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/mapper/nvidia_hiaachbj2 /media/New Volume        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 695930db-21e7-4158-bfa2-2f52e3f8790b
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
search --no-floppy --fs-uuid --set 695930db-21e7-4158-bfa2-2f52e3f8790b
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 695930db-21e7-4158-bfa2-2f52e3f8790b
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=695930db-21e7-4158-bfa2-2f52e3f8790b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 695930db-21e7-4158-bfa2-2f52e3f8790b
    echo    'Loading Linux 2.6.32-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=695930db-21e7-4158-bfa2-2f52e3f8790b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 695930db-21e7-4158-bfa2-2f52e3f8790b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 695930db-21e7-4158-bfa2-2f52e3f8790b
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=695930db-21e7-4158-bfa2-2f52e3f8790b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b6c3686b-cff3-4f0c-937d-c07bd945f6a5 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  17.4GB: boot/grub/core.img
  40.9GB: boot/grub/grub.cfg
  17.4GB: boot/initrd.img-2.6.32-27-generic-pae
  17.4GB: boot/vmlinuz-2.6.32-27-generic-pae
  17.4GB: initrd.img
  17.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  f1 9a b5 76 48 a2 37 43  93 4f bd 61 50 b2 95 a2  |...vH.7C.O.aP...|
00000010  fe 1b b5 6f c9 5f 8e d2  5b 36 0b dd fc 08 3a 66  |...o._..[6....:f|
00000020  c4 08 23 6b b6 14 d8 b4  b9 2d 18 d2 3b c9 5f 4e  |..#k.....-..;._N|
00000030  00 fd b7 02 1e d5 a6 33  5c 32 a5 cb 4a 7e cd 84  |.......3\2..J~..|
00000040  f8 a0 4c 97 1a 63 96 94  43 26 c5 a2 4b 41 40 8e  |..L..c..C&..KA@.|
00000050  b1 27 fb a7 05 08 9d 71  4f 93 89 2c 14 75 45 8c  |.'.....qO..,.uE.|
00000060  9d 16 4d 77 07 2d 34 c3  15 06 25 75 15 04 bf 47  |..Mw.-4...%u...G|
00000070  cf c4 a0 17 3b 7e 2a 3a  1a 1a cc 64 c8 58 d3 53  |....;~*:...d.X.S|
00000080  22 a2 96 84 20 4e ac 2d  c5 99 6d f2 d2 61 88 f4  |"... N.-..m..a..|
00000090  6d 71 78 0c 51 d4 12 7d  cc 47 6e 49 49 22 f7 27  |mqx.Q..}.GnII".'|
000000a0  76 b9 42 d5 31 3a b7 24  d5 18 b8 c3 01 62 0f e2  |v.B.1:.$.....b..|
000000b0  02 0e eb 45 00 2b 75 38  11 bb 58 ee 7f c6 8d 5e  |...E.+u8..X....^|
000000c0  3b 6c b6 aa fb 72 62 b3  64 6c 2b 19 e3 ae 6d 3e  |;l...rb.dl+...m>|
000000d0  3c 16 ba 8b 12 9c 14 b6  ed d1 2e 96 49 2d 65 bb  |<...........I-e.|
000000e0  6a 38 9f 61 4f d9 1d 67  65 a9 4b 1f 08 9a 5b b6  |j8.aO..ge.K...[.|
000000f0  21 fc 5f 6f 89 21 43 4e  16 f7 39 f0 c3 f3 77 03  |!._o.!CN..9...w.|
00000100  f4 59 d3 61 8b f0 30 40  60 7d 33 36 69 58 15 fe  |.Y.a..0@`}36iX..|
00000110  f6 b8 98 a5 09 d6 d4 e9  7f dc 82 5a 34 2d f1 b1  |...........Z4-..|
00000120  68 f1 71 53 a3 c5 4c 16  9a 8c 4e 62 e5 83 db d6  |h.qS..L...Nb....|
00000130  68 f8 29 40 fe a8 d1 d0  2e 16 80 ff 26 30 ac a2  |h.)@........&0..|
00000140  71 3a e8 71 4e 1d 1f ac  9e 87 d1 ae ae 17 c7 0b  |q:.qN...........|
00000150  5d 4c 9b c4 34 bb 62 03  75 67 31 44 8c 94 96 75  |]L..4.b.ug1D...u|
00000160  76 7f c0 20 16 f9 29 5b  12 81 0a 2a 96 cd 02 34  |v.. ..)[...*...4|
00000170  64 31 0b 01 a1 62 97 f0  b7 a9 31 c0 32 29 b9 9a  |d1...b....1.2)..|
00000180  a9 0b 49 ac 2f cc 2f 81  64 51 11 db f6 c6 8a dc  |..I././.dQ......|
00000190  bd 92 46 62 55 57 c3 fe  38 aa f1 ff c7 e5 63 22  |..FbUW..8.....c"|
000001a0  ca 46 bb 2b 8a c6 ec 00  06 e6 f4 ed 15 d4 54 14  |.F.+..........T.|
000001b0  48 37 e5 33 54 49 a3 37  97 38 0f 19 86 fc 00 fe  |H7.3TI.7.8......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 80 62 00 00 00  |............b...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on nvidia_hiaachbj1

00000000  fc 31 c0 8e d0 31 e4 8e  d8 8e c0 be 00 7c bf 00  |.1...1.......|..|
00000010  06 b9 00 01 f3 a5 be ee  07 b0 08 ea 20 06 00 00  |............ ...|
00000020  80 3e b3 07 ff 75 04 88  16 b3 07 80 3c 00 74 04  |.>...u......<.t.|
00000030  08 06 af 07 83 ee 10 d0  e8 73 f0 90 90 90 90 90  |.........s......|
00000040  90 90 90 90 90 90 90 90  90 90 90 90 90 90 90 90  |................|
*
00000070  90 90 90 90 90 90 90 90  90 90 90 90 90 90 be be  |................|
00000080  07 b0 00 b9 04 00 80 3c  00 75 6e fe c0 83 c6 10  |.......<.un.....|
00000090  e2 f4 31 db b4 0e be 9d  07 8a 0e af 07 ac d0 e9  |..1.............|
000000a0  73 02 cd 10 08 c9 75 f5  b0 3a cd 10 31 c0 cd 16  |s.....u..:..1...|
000000b0  3c 00 74 f8 be 8b 07 b9  02 00 e8 ba 00 3c 0d 74  |<.t..........<.t|
000000c0  b4 3c 61 72 06 3c 7a 77  02 2c 20 88 c3 be 9d 07  |.<ar.<zw., .....|
000000d0  8a 0e af 07 ac d0 e9 73  04 38 c3 74 06 08 c9 75  |.......s.8.t...u|
000000e0  f3 eb af b8 0d 0e 31 db  cd 10 8d 84 62 00 3c 07  |......1.....b.<.|
000000f0  75 07 b0 1f a2 af 07 eb  99 31 d2 b9 01 00 3c 04  |u........1....<.|
00000100  74 11 73 f3 30 e4 b1 04  d2 e0 be be 07 01 c6 8a  |t.s.0...........|
00000110  16 b3 07 bf 05 00 56 f6  c2 80 74 31 b4 41 bb aa  |......V...t1.A..|
00000120  55 52 cd 13 5a 5e 56 72  1e 81 fb 55 aa 75 18 f6  |UR..Z^Vr...U.u..|
00000130  c1 01 74 13 8b 44 08 8b  5c 0a be 8d 07 89 44 08  |..t..D..\.....D.|
00000140  89 5c 0a b4 42 eb 0c 8a  74 01 8b 4c 02 b8 01 02  |.\..B...t..L....|
00000150  bb 00 7c 50 c6 06 8f 07  01 cd 13 58 5e 73 05 4f  |..|P.......X^s.O|
00000160  75 b4 eb 93 81 3e fe 7d  55 aa 75 f6 ea 00 7c 00  |u....>.}U.u...|.|
00000170  00 be 83 07 b9 0a 00 50  b4 0e 31 db ac cd 10 e2  |.......P..1.....|
00000180  fb 58 c3 54 65 73 74 44  69 73 6b 0d 0a 10 00 01  |.X.TestDisk.....|
00000190  00 00 7c 00 00 00 00 00  00 00 00 00 00 31 32 33  |..|..........123|
000001a0  34 46 00 00 41 4e 44 54  6d 62 72 00 02 02 02 1f  |4F..ANDTmbr.....|
000001b0  c7 00 00 80 00 00 00 00  00 00 00 00 a5 01 80 00  |................|
000001c0  c1 ff 07 00 c1 ff c1 07  00 00 00 b8 45 04 00 00  |............E...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by akeee on 2011-01-08
Result on netdisk deep search :
Disk /dev/mapper/nvidia_hiaachbj1 - 36 GB / 34 GiB - CHS 71681967 1 1

The harddisk (36 GB / 34 GiB) seems too small! (< 1334 GB / 1242 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
  HFS                      1761702 2241521063 2239759362
  HFS                      6614484 2605559381 2598944898
  HFS                     41361110 2281120471 2239759362
  HPFS - NTFS             61814176  133492127   71677952
  HFS                     69054176  102608613   33554438
  HFS                     69944645 2309704006 2239759362
  HPFS - NTFS             71679936  143357887   71677952

---

### Post by akeee on 2011-01-10
Any help?

---

