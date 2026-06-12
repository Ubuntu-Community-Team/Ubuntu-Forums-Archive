---
title: "Computer will not load OS on boot"
date: 2010-10-09
forum: General Help
---

### Post by Hazzy on 2010-10-09
My computer was built by a small, local business. This past spring, I wiped the computer and reinstalled Windows 7 Pro from a 64 disk. It has worked well. I wanted to play with Ubuntu, so I set up a dual-boot. When I first installed Ubuntu last week, I had issues with Java. After  countless failures from Google, I installed a new Ubuntu partition  without deleting the old one. The other day, I got curious and wanted to  try Mint. This went on yet another partition. Yesterday I wanted to  organize this out better, so I formatted the Mint partition and it's  swap. The computer functioned just fine until I tried to reboot. It  starts out with normal BIOS(?) stuff, "Loading Operating System..."  for a bit... and then breaks. It says something about not being able to  find device, shows a UUID, then goes into grub rescue. 

I spent  around an hour or so Googling about this and have come up with nothing.  Internet tells me to do this, I do, nothing happens. Internet tells me  to do that, the file does not exist, nothing happens. I was Googling via  my mom's laptop, and I am currently posting this from Firefox on the  LiveCD (demo). I still have my Windows 7 install disk, although finding it is a different story.
 
 How do I fix my booting issue, preferably without losing any data from my second Ubuntu install (I do not care about the first one - on sdb5?) or Windows 7.

**sudo fdisk -l**
 ```
ubuntu@ubuntu:~$ sudo fdisk -l
 
 Disk /dev/sda: 500.1 GB, 500107862016 bytes
 255 heads, 63 sectors/track, 60801 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disk identifier: 0x916be406
 
    Device Boot      Start         End      Blocks   Id  System
 /dev/sda1   *           1          13      102400    7  HPFS/NTFS
 Partition 1 does not end on cylinder boundary.
 /dev/sda2              13       60802   488282112    7  HPFS/NTFS
 Partition 2 does not end on cylinder boundary.
 
 Disk /dev/sdb: 320.1 GB, 320072933376 bytes
 255 heads, 63 sectors/track, 38913 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disk identifier: 0x916be41e
 
    Device Boot      Start         End      Blocks   Id  System
 /dev/sdb1               1       18194   146140077+   7  HPFS/NTFS
 /dev/sdb2           18194       38914   166429697    5  Extended
 /dev/sdb5           25101       31916    54744536   83  Linux
 /dev/sdb6           38347       38914     4552704   82  Linux swap / Solaris
 /dev/sdb7           18194       24813    53165056   83  Linux
 /dev/sdb8           24813       25100     2308096   82  Linux swap / Solaris
 
 Partition table entries are not in disk order
               
 Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
 255 heads, 63 sectors/track, 121601 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disk identifier: 0x44fdfe06
 
    Device Boot      Start         End      Blocks   Id  System
 /dev/sdd1               1      121601   976760001    c  W95 FAT32 (LBA)
 
``` **Boot Info Script**
```
                Boot Info Script 0.55    dated February 15th, 2010                    
 
 ============================= Boot Info Summary: ==============================
 
  => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
     partition #9 for /boot/grub.
  => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
     in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
  => Windows is installed in the MBR of /dev/sdd
 
 sda1: _________________________________________________________________________
 
     File system:       ntfs
     Boot sector type:  Windows Vista/7
     Boot sector info:  No errors found in the Boot Parameter Block.
     Operating System:  
     Boot files/dirs:   /bootmgr /Boot/BCD
 
 sda2: _________________________________________________________________________
 
     File system:       ntfs
     Boot sector type:  Windows Vista/7
     Boot sector info:  No errors found in the Boot Parameter Block.
     Operating System:  Windows 7
     Boot files/dirs:   /Windows/System32/winload.exe
 
 sdb1: _________________________________________________________________________
 
     File system:       ntfs
     Boot sector type:  Windows Vista/7
     Boot sector info:  No errors found in the Boot Parameter Block.
     Operating System:  Windows 7
     Boot files/dirs:   /Windows/System32/winload.exe
 
 sdb2: _________________________________________________________________________
 
     File system:       Extended Partition
     Boot sector type:  Unknown
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
 
 sdb7: _________________________________________________________________________
 
     File system:       ext4
     Boot sector type:  -
     Boot sector info:  
     Operating System:  Ubuntu 10.04.1 LTS
     Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
 
 sdb8: _________________________________________________________________________
 
     File system:       swap
     Boot sector type:  -
     Boot sector info:  
 
 sdd1: _________________________________________________________________________
 
     File system:       vfat
     Boot sector type:  MSWIN4.1: Fat 32
     Boot sector info:  No errors found in the Boot Parameter Block.
     Operating System:  
     Boot files/dirs:   
 
 =========================== Drive/Partition Info: =============================
 
 Drive: sda ___________________ _____________________________________________________
 
 Disk /dev/sda: 500.1 GB, 500107862016 bytes
 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
 Units = sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 
 Partition  Boot         Start           End          Size  Id System
 
 /dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
 /dev/sda2             206,848   976,771,071   976,564,224   7 HPFS/NTFS
 
 
 Drive: sdb ___________________ _____________________________________________________
 
 Disk /dev/sdb: 320.1 GB, 320072933376 bytes
 255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
 Units = sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 
 Partition  Boot         Start           End          Size  Id System
 
 /dev/sdb1               2,048   292,282,202   292,280,155   7 HPFS/NTFS
 /dev/sdb2         292,282,366   625,141,759   332,859,394   5 Extended
 /dev/sdb5         403,238,912   512,727,983   109,489,072  83 Linux
 /dev/sdb6         616,036,352   625,141,759     9,105,408  82 Linux swap / Solaris
 /dev/sdb7         292,282,368   398,612,479   106,330,112  83 Linux
 /dev/sdb8         398,614,528   403,230,719     4,616,192  82 Linux swap / Solaris
 
 
 Drive: sdd ___________________ _____________________________________________________
 
 Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
 255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
 Units = sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 
 Partition  Boot         Start           End          Size  Id System
 
 /dev/sdd1                  63 1,953,520,064 1,953,520,002   c W95 FAT32 (LBA)
 
 
 blkid -c /dev/null: ____________________________________________________________
 
 Device           UUID                                   TYPE       LABEL                         
 
 /dev/loop0                                              squashfs                                 
 /dev/sda1        DAEE43A6EE4379B1                       ntfs       System Reserved               
 /dev/sda2        086445BA6445AB70                       ntfs                                     
 /dev/sda: PTTYPE="dos" 
 /dev/sdb1        FC60C91B60C8DE10                       ntfs                                     
 /dev/sdb2: PTTYPE="dos" 
 /dev/sdb5        1b780186-310c-4f08-a33d-f2b3332dc88c   ext4                                     
 /dev/sdb6        34b5a898-f4e1-4ab0-8de4-baf21af2b1bc   swap                                     
 /dev/sdb7        6c15b8d5-d0bf-4ec6-943e-6bd15656e525   ext4                                     
 /dev/sdb8        4f2cc65f-a8c2-40ae-8e15-62e22e8a2e52   swap                                     
 /dev/sdb: PTTYPE="dos" 
 /dev/sdd1        9389-61CD                              vfat       My Book                       
 /dev/sdd: PTTYPE="dos" 
 error: /dev/sdc: No medium found
 
 ============================ "mount | grep ^/dev  output: ===========================
 
 Device           Mount_Point              Type       Options
 
 aufs             /                        aufs       (rw)
 /dev/sr0         /cdrom                   iso9660    (ro,noatime)
 /dev/loop0       /rofs                    squashfs   (ro,noatime)
 
 
 =================== sdb5: Location of files loaded by Grub: ===================
 
 
  213.0GB: boot/grub/core.img
  213.0GB: boot/grub/stage2
 
 =========================== sdb7/boot/grub/grub.cfg: ===========================
 
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
 set root='(hd1,7)'
 search --no-floppy --fs-uuid --set 6c15b8d5-d0bf-4ec6-943e-6bd15656e525
 if loadfont /usr/share/grub/unicode.pf2 ; then
 set gfxmode=1024x768
   insmod gfxterm
   insmod vbe
   if terminal_output gfxterm ; then true ; else
     # For backward compatibility with versions of terminal.mod that don't
     # understand terminal_output
     terminal gfxterm
   fi
 fi
 insmod ext2
 set root='(hd1,7)'
 search --no-floppy --fs-uuid --set 6c15b8d5-d0bf-4ec6-943e-6bd15656e525
 set locale_dir=($root)/boot/grub/locale
 set lang=en
 insmod gettext
 if [ ${recordfail} = 1 ]; then
   set timeout=-1
 else
   set timeout=3
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
     set root='(hd1,7)'
     search --no-floppy --fs-uuid --set 6c15b8d5-d0bf-4ec6-943e-6bd15656e525
     linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=6c15b8d5-d0bf-4ec6-943e-6bd15656e525 ro  splash vga=795  quiet splash
     initrd    /boot/initrd.img-2.6.32-25-generic
 }
 menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
     recordfail
     insmod ext2
     set root='(hd1,7)'
     search --no-floppy --fs-uuid --set 6c15b8d5-d0bf-4ec6-943e-6bd15656e525
     echo    'Loading Linux 2.6.32-25-generic ...'
     linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=6c15b8d5-d0bf-4ec6-943e-6bd15656e525 ro single  splash vga=795
     echo    'Loading initial ramdisk ...'
     initrd    /boot/initrd.img-2.6.32-25-generic
 }
 menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
     recordfail
     insmod ext2
     set root='(hd1,7)'
     search --no-floppy --fs-uuid --set 6c15b8d5-d0bf-4ec6-943e-6bd15656e525
     linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6c15b8d5-d0bf-4ec6-943e-6bd15656e525 ro  splash vga=795  quiet splash
     initrd    /boot/initrd.img-2.6.32-24-generic
 }
 menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
     recordfail
     insmod ext2
     set root='(hd1,7)'
     search --no-floppy --fs-uuid --set 6c15b8d5-d0bf-4ec6-943e-6bd15656e525
     echo    'Loading Linux 2.6.32-24-generic ...'
     linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6c15b8d5-d0bf-4ec6-943e-6bd15656e525 ro single  splash vga=795
     echo    'Loading initial ramdisk ...'
     initrd    /boot/initrd.img-2.6.32-24-generic
 }
 ### END /etc/grub.d/10_linux ###
 
 ### BEGIN /etc/grub.d/20_memtest86+ ###
 menuentry "Memory test (memtest86+)" {
     insmod ext2
     set root='(hd1,7)'
     search --no-floppy --fs-uuid --set 6c15b8d5-d0bf-4ec6-943e-6bd15656e525
     linux16    /boot/memtest86+.bin
 }
 menuentry "Memory test (memtest86+, serial console 115200)" {
     insmod ext2
     set root='(hd1,7)'
     search --no-floppy --fs-uuid --set 6c15b8d5-d0bf-4ec6-943e-6bd15656e525
     linux16    /boot/memtest86+.bin console=ttyS0,115200n8
 }
 ### END /etc/grub.d/20_memtest86+ ###
 
 ### BEGIN /etc/grub.d/30_os-prober ###
 menuentry "Windows 7 (loader) (on /dev/sda1)" {
     insmod ntfs
     set root='(hd0,1)'
     search --no-floppy --fs-uuid --set daee43a6ee4379b1
     chainloader +1
 }
 menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sdb5)" {
     insmod ext2
     set root='(hd1,5)'
     search --no-floppy --fs-uuid --set e302aa9b-9b4d-45c1-b27f-f57bb0c8dbf8
     linux /boot/vmlinuz-2.6.32-25-generic root=UUID=e302aa9b-9b4d-45c1-b27f-f57bb0c8dbf8 ro quiet splash
     initrd /boot/initrd.img-2.6.32-25-generic
 }
 menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sdb5)" {
     insmod ext2
     set root='(hd1,5)'
     search --no-floppy --fs-uuid --set e302aa9b-9b4d-45c1-b27f-f57bb0c8dbf8
     linux /boot/vmlinuz-2.6.32-25-generic root=UUID=e302aa9b-9b4d-45c1-b27f-f57bb0c8dbf8 ro single
     initrd /boot/initrd.img-2.6.32-25-generic
 }
 menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sdb5)" {
     insmod ext2
     set root='(hd1,5)'
     search --no-floppy --fs-uuid --set e302aa9b-9b4d-45c1-b27f-f57bb0c8dbf8
     linux /boot/vmlinuz-2.6.32-24-generic root=UUID=e302aa9b-9b4d-45c1-b27f-f57bb0c8dbf8 ro quiet splash
     initrd /boot/initrd.img-2.6.32-24-generic
 }
 menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sdb5)" {
     insmod ext2
     set root='(hd1,5)'
     search --no-floppy --fs-uuid --set e302aa9b-9b4d-45c1-b27f-f57bb0c8dbf8
     linux /boot/vmlinuz-2.6.32-24-generic root=UUID=e302aa9b-9b4d-45c1-b27f-f57bb0c8dbf8 ro single
     initrd /boot/initrd.img-2.6.32-24-generic
 }
 menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sdb9) (on /dev/sdb9)" {
     insmod ext2
     set root='(hd1,9)'
     search --no-floppy --fs-uuid --set f1fa46b2-fe30-4d00-ac70-1d7beac61d48
     linux /boot/vmlinuz-2.6.32-21-generic root=UUID=f1fa46b2-fe30-4d00-ac70-1d7beac61d48 ro quiet splash
     initrd /boot/initrd.img-2.6.32-21-generic
 }
 menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sdb9) -- recovery mode (on /dev/sdb9)" {
     insmod ext2
     set root='(hd1,9)'
     search --no-floppy --fs-uuid --set f1fa46b2-fe30-4d00-ac70-1d7beac61d48
     linux /boot/vmlinuz-2.6.32-21-generic root=UUID=f1fa46b2-fe30-4d00-ac70-1d7beac61d48 ro single
     initrd /boot/initrd.img-2.6.32-21-generic
 }
 ### END /etc/grub.d/30_os-prober ###
 
 ### BEGIN /etc/grub.d/40_custom ###
 # This file provides an easy way to add custom menu entries.  Simply type the
 # menu entries you want to add after this comment.  Be careful not to change
 # the 'exec tail' line above.
 ### END /etc/grub.d/40_custom ###
 
 =============================== sdb7/etc/fstab: ===============================
 
 # /etc/fstab: static file system information.
 #
 # Use 'blkid -o value -s UUID' to print the universally unique identifier
 # for a device; this may be used with UUID= as a more robust way to name
 # devices that works even if disks are added and removed. See fstab(5).
 #
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
 proc            /proc           proc    nodev,noexec,nosuid 0       0
 # / was on /dev/sdb7 during installation
 UUID=6c15b8d5-d0bf-4ec6-943e-6bd15656e525 /               ext4    errors=remount-ro 0       1
 # swap was on /dev/sdb8 during installation
 UUID=4f2cc65f-a8c2-40ae-8e15-62e22e8a2e52 none            swap    sw              0       0
 
 =================== sdb7: Location of files loaded by Grub: ===================
 
 
  201.3GB: boot/grub/core.img
  152.2GB: boot/grub/grub.cfg
  201.4GB: boot/initrd.img-2.6.32-24-generic
  201.5GB: boot/initrd.img-2.6.32-25-generic
  201.4GB: boot/vmlinuz-2.6.32-24-generic
  201.4GB: boot/vmlinuz-2.6.32-25-generic
  201.5GB: initrd.img
  201.4GB: initrd.img.old
  201.4GB: vmlinuz
  201.4GB: vmlinuz.old
 =========================== Unknown MBRs/Boot Sectors/etc =======================
 
 Unknown BootLoader  on sdb2
 
 00000000  93 70 68 86 25 cd e7 39  ae 90 ee 4e cc 77 20 9f  |.ph.%..9...N.w .|
 00000010  61 d4 a2 8c 1a 77 4b fe  55 e0 69 15 8e e8 5e e4  |a....wK.U.i...^.|
 00000020  ce c0 32 72 ea 56 f8 35  ca 3d b0 92 38 39 db f7  |..2r.V.5.=..89..|
 00000030  c6 7c 68 9a 98 a8 09 4f  53 26 ba c9 78 74 8b b1  |.|h....OS&..xt..|
 00000040  17 1f 06 e1 bc d1 cf 1d  21 70 35 44 4e 4a 44 2d  |........!p5DNJD-|
 00000050  aa c6 bd bf 70 3f 34 a3  11 1c 33 bb 84 8d 78 ce  |....p?4...3...x.|
 00000060  15 8e 94 86 1d ea 7f d1  57 e3 f5 6e 81 97 65 71  |........W..n..eq|
 00000070  4a 5c 9b af a4 e9 62 a1  86 89 24 50 7e ee b8 d2  |J\....b...$P~...|
 00000080  b7 f1 68 5c c4 28 3b 75  1e 33 54 ae 5a eb 93 7d  |..h\.(;u.3T.Z..}|
 00000090  47 83 3c a6 ce ae 9c 9d  d3 04 5b 8f fe 2a ff 47  |G.<.......[..*.G|
 000000a0  1e 6a 3d 7e 8c f4 bf d8  4c 7c 6f 6e 4f 9b 0e 7e  |.j=~....L|onO..~|
 000000b0  61 bf 62 b4 60 8e c7 49  93 f1 a3 ce c2 49 9f c2  |a.b.`..I.....I..|
 000000c0  54 c6 49 63 6d 7e 93 d4  6e cb 4a e3 73 2d d6 92  |T.Icm~..n.J.s-..|
 000000d0  0b 4e 80 55 bc a8 59 1e  73 0c 02 33 63 21 c2 f8  |.N.U..Y.s..3c!..|
 000000e0  16 1d 9d 40 86 40 7c ba  d8 03 fe 36 95 12 3d 11  |...@.@|....6..=.|
 000000f0  68 c5 29 bd 6d a3 d7 9e  1e 9e 2a c8 34 a1 d3 03  |h.).m.....*.4...|
 00000100  d4 c8 3b 40 42 32 fc ee  72 09 78 b1 a7 85 c8 9c  |..;@B2..r.x.....|
 00000110  37 61 c0 ba 09 3f 9c f2  7f 98 19 a3 15 2e 81 a3  |7a...?..........|
 00000120  65 f2 40 b8 3c 7b a3 66  d5 72 00 80 db ab f4 e8  |e.@.<{.f.r......|
 00000130  a5 5d f0 9a 80 f0 0f cc  5f 49 9c 9e 0a 80 14 a7  |.]......_I......|
 00000140  dc 76 2b ca 34 ca 5a 28  34 80 fe a3 63 69 3b f9  |.v+.4.Z(4...ci;.|
 00000150  de ef 85 a1 ab 47 26 61  ce 18 7a 32 a8 b0 1e 1e  |.....G&a..z2....|
 00000160  f8 3a 88 3a d0 88 91 00  2a 26 f0 ea d6 cc fc 12  |.:.:....*&......|
 00000170  20 fe 82 8d de 33 6c 48  bb 63 fb c4 0a df 2a 89  | ....3lH.c....*.|
 00000180  10 43 d0 dd f0 5f 4e 9e  38 96 eb bb ad a9 0c 74  |.C..._N.8......t|
 00000190  f1 a5 6c 35 24 a8 49 61  4a 49 17 b4 ed 78 30 e6  |..l5$.IaJI...x0.|
 000001a0  71 11 49 b8 f3 f9 4a 60  e9 66 c0 c4 12 e4 49 25  |q.I...J`.f....I%|
 000001b0  ef 01 e2 00 c1 b3 2e 6e  79 d7 f3 c6 03 33 00 fe  |.......ny....3..|
 000001c0  ff ff 83 fe ff ff 02 10  9d 06 b0 ab 86 06 00 fe  |................|
 000001d0  ff ff 05 fe ff ff 4c f9  4b 13 b6 0e 8b 00 00 00  |......L.K.......|
 000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
 000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
 00000200
 
 
 =======Devices which don't seem to have a corresponding hard drive==============
 
 sdc 
```

---

### Post by oldfred on 2010-10-09
You just need to reinstall grub2 to the MBR. Often moving partitions around will required a reinstall.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Install MBR from LiveCD, Ubuntu install on sdb7 and want grub2 in drive sdb's MBR:
Find linux partition, change sdb7 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sdb7 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb

Then set BIOS to boot sdb - the 320GB drive.

You may want to reinstall a windows boot loader to sda. I like to have the MBR boot the system on that drive.

An aside. Why a FAT partition on a 1GB drive? NTFS is almost always better. FAT will not save large files and is less reliable especially on large drives.

---

