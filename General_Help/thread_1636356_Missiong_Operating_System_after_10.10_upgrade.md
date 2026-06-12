---
title: "Missiong Operating System after 10.10 upgrade"
date: 2010-12-03
forum: General Help
---

### Post by sikuneh on 2010-12-03
I just got Ununtu on my laptop today. And after spending 2.5 hours upgrading it, it tells me to restart my computer, well I did that and now whenever I try to boot up my laptop I get to the screen that says "Missing Operating System." 

I then put Ubuntu on my flash drive and went to check if the files had disappeared, they had not. Could someone help me with this problem?

---

### Post by wilee-nilee on 2010-12-03
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

---

### Post by sikuneh on 2010-12-03
```

    Boot Info Script 0.55    dated February 15th, 2010                      ============================= Boot Info Summary: ==============================   =&gt; Windows is installed in the MBR of /dev/sda  =&gt; Syslinux is installed in the MBR of /dev/sdc  sda1: _________________________________________________________________________      File system:       swap     Boot sector type:  -     Boot sector info:    sda2: _________________________________________________________________________      File system:       swap     Boot sector type:  -     Boot sector info:    sda3: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:  Windows 7     Boot files/dirs:   /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr                         /ubuntu/winboot/wubildr /ubuntu/disks/root.disk                         /ubuntu/disks/swap.disk  sda3/Wubi: _________________________________________________________________________      File system:       ext4     Boot sector type:  -     Boot sector info:       Operating System:  Ubuntu 10.10     Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab  sdc1: _________________________________________________________________________      File system:       vfat     Boot sector type:  Unknown     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files/dirs:     =========================== Drive/Partition Info: =============================  Drive: sda ___________________ _____________________________________________________  Disk /dev/sda: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot         Start           End          Size  Id System  /dev/sda1                  63        80,324        80,262  de Dell Utility /dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS /dev/sda3          30,801,920   976,771,119   945,969,200   7 HPFS/NTFS   Drive: sdc ___________________ _____________________________________________________  Disk /dev/sdc: 8021 MB, 8021606400 bytes 5 heads, 32 sectors/track, 97920 cylinders, total 15667200 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot         Start           End          Size  Id System  /dev/sdc1    *          8,064    15,667,199    15,659,136   b W95 FAT32   blkid -c /dev/null: ____________________________________________________________  Device           UUID                                   TYPE       LABEL                           /dev/loop0                                              squashfs                                  /dev/loop1       7a55c93a-6a3d-2349-b51e-1d1e57dc4dcf   ext2       casper-rw                      /dev/loop2       8cf1132a-5a2f-4c23-8487-c236e22631d7   ext4                                      /dev/mmcblk0p1   3418-977F                              vfat                                      /dev/sda1        76bc12ff-f645-4020-af86-2cf0b1eeeff2   swap                                      /dev/sda2        4a7404a7-4d8c-4dd7-8f43-dfd1e8b2ac7e   swap                                      /dev/sda3        E8FA6D1CFA6CE870                       ntfs       OS                             /dev/sda: PTTYPE="dos"  /dev/sdc1        1A55-0855                              vfat       NICK'S 8 GB                    /dev/sdc: PTTYPE="dos"   ============================ "mount | grep ^/dev  output: ===========================  Device           Mount_Point              Type       Options  aufs             /                        aufs       (rw) /dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro) /dev/loop0       /rofs                    squashfs   (ro,noatime) /dev/sdc1        /media/NICK'S 8 GB       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush) /dev/loop1       /media/casper-rw         ext2       (rw,nosuid,nodev,uhelper=udisks)   ======================== sda3/Wubi/boot/grub/grub.cfg: ========================  # # DO NOT EDIT THIS FILE # # It is automatically generated by grub-mkconfig using templates # from /etc/grub.d and settings from /etc/default/grub #  ### BEGIN /etc/grub.d/00_header ### if [ -s $prefix/grubenv ]; then   set have_grubenv=true   load_env fi set default="0" if [ "${prev_saved_entry}" ]; then   set saved_entry="${prev_saved_entry}"   save_env saved_entry   set prev_saved_entry=   save_env prev_saved_entry   set boot_once=true fi  function savedefault {   if [ -z "${boot_once}" ]; then     saved_entry="${chosen}"     save_env saved_entry   fi }  function recordfail {   set recordfail=1   if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi }  function load_video {   insmod vbe   insmod vga }  insmod part_msdos insmod ntfs set root='(hd1,msdos3)' search --no-floppy --fs-uuid --set e8fa6d1cfa6ce870 loopback loop0 /ubuntu/disks/root.disk set root=(loop0) if loadfont /usr/share/grub/unicode.pf2 ; then   set gfxmode=640x480   load_video   insmod gfxterm fi terminal_output gfxterm insmod part_msdos insmod ntfs set root='(hd1,msdos3)' search --no-floppy --fs-uuid --set e8fa6d1cfa6ce870 loopback loop0 /ubuntu/disks/root.disk set root=(loop0) set locale_dir=($root)/boot/grub/locale set lang=en insmod gettext if [ "${recordfail}" = 1 ]; then   set timeout=-1 else   set timeout=10 fi ### END /etc/grub.d/00_header ###  ### BEGIN /etc/grub.d/05_debian_theme ### set menu_color_normal=white/black set menu_color_highlight=black/light-gray ### END /etc/grub.d/05_debian_theme ###  ### BEGIN /etc/grub.d/10_linux ### ### END /etc/grub.d/10_linux ###  ### BEGIN /etc/grub.d/10_lupin ### menuentry "Ubuntu, Linux 2.6.35-23-generic" { 	insmod part_msdos 	insmod ntfs 	set root='(hd1,msdos3)' 	search --no-floppy --fs-uuid --set e8fa6d1cfa6ce870 	loopback loop0 /ubuntu/disks/root.disk 	set root=(loop0) 	linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash 	initrd /boot/initrd.img-2.6.35-23-generic } menuentry "Ubuntu, Linux 2.6.35-23-generic (recovery mode)" { 	insmod part_msdos 	insmod ntfs 	set root='(hd1,msdos3)' 	search --no-floppy --fs-uuid --set e8fa6d1cfa6ce870 	loopback loop0 /ubuntu/disks/root.disk 	set root=(loop0) 	linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single  	initrd /boot/initrd.img-2.6.35-23-generic } menuentry "Ubuntu, Linux 2.6.32-26-generic" { 	insmod part_msdos 	insmod ntfs 	set root='(hd1,msdos3)' 	search --no-floppy --fs-uuid --set e8fa6d1cfa6ce870 	loopback loop0 /ubuntu/disks/root.disk 	set root=(loop0) 	linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash 	initrd /boot/initrd.img-2.6.32-26-generic } menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" { 	insmod part_msdos 	insmod ntfs 	set root='(hd1,msdos3)' 	search --no-floppy --fs-uuid --set e8fa6d1cfa6ce870 	loopback loop0 /ubuntu/disks/root.disk 	set root=(loop0) 	linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single  	initrd /boot/initrd.img-2.6.32-26-generic } ### END /etc/grub.d/10_lupin ###  ### BEGIN /etc/grub.d/20_linux_xen ### ### END /etc/grub.d/20_linux_xen ###  ### BEGIN /etc/grub.d/20_memtest86+ ### ### END /etc/grub.d/20_memtest86+ ###  ### BEGIN /etc/grub.d/30_os-prober ### if [ "x${timeout}" != "x-1" ]; then   if keystatus; then     if keystatus --shift; then       set timeout=-1     else       set timeout=0     fi   else     if sleep --interruptible 3 ; then       set timeout=0     fi   fi fi ### END /etc/grub.d/30_os-prober ###  ### BEGIN /etc/grub.d/40_custom ### # This file provides an easy way to add custom menu entries.  Simply type the # menu entries you want to add after this comment.  Be careful not to change # the 'exec tail' line above. ### END /etc/grub.d/40_custom ###  ### BEGIN /etc/grub.d/41_custom ### if [ -f  $prefix/custom.cfg ]; then   source $prefix/custom.cfg; fi ### END /etc/grub.d/41_custom ###  ============================= sda3/Wubi/etc/fstab: =============================  # /etc/fstab: static file system information. # # Use 'blkid -o value -s UUID' to print the universally unique identifier # for a device; this may be used with UUID= as a more robust way to name # devices that works even if disks are added and removed. See fstab(5). # # &lt;file system&gt; &lt;mount point&gt;   &lt;type&gt;  &lt;options&gt;       &lt;dump&gt;  &lt;pass&gt; proc            /proc           proc    nodev,noexec,nosuid 0       0 /host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1 /host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0  ================= sda3/Wubi: Location of files loaded by Grub: =================      9.3GB: boot/grub/grub.cfg    1.5GB: boot/initrd.img-2.6.32-26-generic    1.8GB: boot/initrd.img-2.6.35-23-generic   19.8GB: boot/vmlinuz-2.6.32-26-generic   19.8GB: boot/vmlinuz-2.6.35-23-generic    1.8GB: initrd.img    1.5GB: initrd.img.old   19.8GB: vmlinuz   19.8GB: vmlinuz.old =========================== Unknown MBRs/Boot Sectors/etc =======================  Unknown BootLoader  on sdc1  00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 c6 08  |.X.SYSLINUX.....| 00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 80 1f 00 00  |........?.......| 00000020  80 f0 ee 00 9d 3b 00 00  00 00 00 00 02 00 00 00  |.....;..........| 00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................| 00000040  80 00 29 55 08 55 1a 4e  4f 20 4e 41 4d 45 20 20  |..)U.U.NO NAME  | 00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...| 00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&amp;.x{...| 00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.| 00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M| 00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8| 000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..| 000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.| 000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r| 000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?| 000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..| 000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2| 00000100  7d 00 66 b8 b8 a9 8f 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......| 00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.&gt;$~4..ruv.| 00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..| 00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f| 00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`| 00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`| 00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..&gt;.|f..1| 00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...| 00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa| 00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.| 000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......| 000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........| 000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot| 000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........| 000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................| 000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.| 00000200

```

---

### Post by iponeverything on 2010-12-03
having that all one line makes that output difficult to be useful.

---

### Post by wilee-nilee on 2010-12-03
z

---

### Post by sikander3786 on 2010-12-03
> **sikuneh said:**
> ```

    Boot Info Script 0.55    dated February 15th, 2010                      ============================= Boot Info Summary: ==============================   =&gt; Windows is installed in the MBR of /dev/sda  =&gt; Syslinux is installed in the MBR of /dev/sdc  sda1: _________________________________________________________________________      File system:       swap     Boot sector type:  -     Boot sector info:    sda2: _________________________________________________________________________      File system:       swap     Boot sector type:  -     Boot sector info:    sda3: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:  Windows 7     Boot files/dirs:   /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr                         /ubuntu/winboot/wubildr /ubuntu/disks/root.disk                         /ubuntu/disks/swap.disk  sda3/Wubi: _________________________________________________________________________      File system:       ext4     Boot sector type:  -     Boot sector info:       Operating System:  Ubuntu 10.10     Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab  sdc1: _________________________________________________________________________      File system:       vfat     Boot sector type:  Unknown     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files/dirs:     =========================== Drive/Partition Info: =============================  Drive: sda ___________________ _____________________________________________________  Disk /dev/sda: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot         Start           End          Size  Id System  /dev/sda1                  63        80,324        80,262  de Dell Utility /dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS /dev/sda3          30,801,920   976,771,119   945,969,200   7 HPFS/NTFS   Drive: sdc ___________________ _____________________________________________________  Disk /dev/sdc: 8021 MB, 8021606400 bytes 5 heads, 32 sectors/track, 97920 cylinders, total 15667200 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot         Start           End          Size  Id System  /dev/sdc1    *          8,064    15,667,199    15,659,136   b W95 FAT32   blkid -c /dev/null: ____________________________________________________________  Device           UUID                                   TYPE       LABEL                           /dev/loop0                                              squashfs                                  /dev/loop1       7a55c93a-6a3d-2349-b51e-1d1e57dc4dcf   ext2       casper-rw                      /dev/loop2       8cf1132a-5a2f-4c23-8487-c236e22631d7   ext4                                      /dev/mmcblk0p1   3418-977F                              vfat                                      /dev/sda1        76bc12ff-f645-4020-af86-2cf0b1eeeff2   swap                                      /dev/sda2        4a7404a7-4d8c-4dd7-8f43-dfd1e8b2ac7e   swap                                      /dev/sda3        E8FA6D1CFA6CE870                       ntfs       OS                             /dev/sda: PTTYPE="dos"  /dev/sdc1        1A55-0855                              vfat       NICK'S 8 GB                    /dev/sdc: PTTYPE="dos"   ============================ "mount | grep ^/dev  output: ===========================  Device           Mount_Point              Type       Options  aufs             /                        aufs       (rw) /dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro) /dev/loop0       /rofs                    squashfs   (ro,noatime) /dev/sdc1        /media/NICK'S 8 GB       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush) /dev/loop1       /media/casper-rw         ext2       (rw,nosuid,nodev,uhelper=udisks)   ======================== sda3/Wubi/boot/grub/grub.cfg: ========================  # # DO NOT EDIT THIS FILE # # It is automatically generated by grub-mkconfig using templates # from /etc/grub.d and settings from /etc/default/grub #  ### BEGIN /etc/grub.d/00_header ### if [ -s $prefix/grubenv ]; then   set have_grubenv=true   load_env fi set default="0" if [ "${prev_saved_entry}" ]; then   set saved_entry="${prev_saved_entry}"   save_env saved_entry   set prev_saved_entry=   save_env prev_saved_entry   set boot_once=true fi  function savedefault {   if [ -z "${boot_once}" ]; then     saved_entry="${chosen}"     save_env saved_entry   fi }  function recordfail {   set recordfail=1   if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi }  function load_video {   insmod vbe   insmod vga }  insmod part_msdos insmod ntfs set root='(hd1,msdos3)' search --no-floppy --fs-uuid --set e8fa6d1cfa6ce870 loopback loop0 /ubuntu/disks/root.disk set root=(loop0) if loadfont /usr/share/grub/unicode.pf2 ; then   set gfxmode=640x480   load_video   insmod gfxterm fi terminal_output gfxterm insmod part_msdos insmod ntfs set root='(hd1,msdos3)' search --no-floppy --fs-uuid --set e8fa6d1cfa6ce870 loopback loop0 /ubuntu/disks/root.disk set root=(loop0) set locale_dir=($root)/boot/grub/locale set lang=en insmod gettext if [ "${recordfail}" = 1 ]; then   set timeout=-1 else   set timeout=10 fi ### END /etc/grub.d/00_header ###  ### BEGIN /etc/grub.d/05_debian_theme ### set menu_color_normal=white/black set menu_color_highlight=black/light-gray ### END /etc/grub.d/05_debian_theme ###  ### BEGIN /etc/grub.d/10_linux ### ### END /etc/grub.d/10_linux ###  ### BEGIN /etc/grub.d/10_lupin ### menuentry "Ubuntu, Linux 2.6.35-23-generic" { 	insmod part_msdos 	insmod ntfs 	set root='(hd1,msdos3)' 	search --no-floppy --fs-uuid --set e8fa6d1cfa6ce870 	loopback loop0 /ubuntu/disks/root.disk 	set root=(loop0) 	linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash 	initrd /boot/initrd.img-2.6.35-23-generic } menuentry "Ubuntu, Linux 2.6.35-23-generic (recovery mode)" { 	insmod part_msdos 	insmod ntfs 	set root='(hd1,msdos3)' 	search --no-floppy --fs-uuid --set e8fa6d1cfa6ce870 	loopback loop0 /ubuntu/disks/root.disk 	set root=(loop0) 	linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single  	initrd /boot/initrd.img-2.6.35-23-generic } menuentry "Ubuntu, Linux 2.6.32-26-generic" { 	insmod part_msdos 	insmod ntfs 	set root='(hd1,msdos3)' 	search --no-floppy --fs-uuid --set e8fa6d1cfa6ce870 	loopback loop0 /ubuntu/disks/root.disk 	set root=(loop0) 	linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash 	initrd /boot/initrd.img-2.6.32-26-generic } menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" { 	insmod part_msdos 	insmod ntfs 	set root='(hd1,msdos3)' 	search --no-floppy --fs-uuid --set e8fa6d1cfa6ce870 	loopback loop0 /ubuntu/disks/root.disk 	set root=(loop0) 	linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single  	initrd /boot/initrd.img-2.6.32-26-generic } ### END /etc/grub.d/10_lupin ###  ### BEGIN /etc/grub.d/20_linux_xen ### ### END /etc/grub.d/20_linux_xen ###  ### BEGIN /etc/grub.d/20_memtest86+ ### ### END /etc/grub.d/20_memtest86+ ###  ### BEGIN /etc/grub.d/30_os-prober ### if [ "x${timeout}" != "x-1" ]; then   if keystatus; then     if keystatus --shift; then       set timeout=-1     else       set timeout=0     fi   else     if sleep --interruptible 3 ; then       set timeout=0     fi   fi fi ### END /etc/grub.d/30_os-prober ###  ### BEGIN /etc/grub.d/40_custom ### # This file provides an easy way to add custom menu entries.  Simply type the # menu entries you want to add after this comment.  Be careful not to change # the 'exec tail' line above. ### END /etc/grub.d/40_custom ###  ### BEGIN /etc/grub.d/41_custom ### if [ -f  $prefix/custom.cfg ]; then   source $prefix/custom.cfg; fi ### END /etc/grub.d/41_custom ###  ============================= sda3/Wubi/etc/fstab: =============================  # /etc/fstab: static file system information. # # Use 'blkid -o value -s UUID' to print the universally unique identifier # for a device; this may be used with UUID= as a more robust way to name # devices that works even if disks are added and removed. See fstab(5). # # &lt;file system&gt; &lt;mount point&gt;   &lt;type&gt;  &lt;options&gt;       &lt;dump&gt;  &lt;pass&gt; proc            /proc           proc    nodev,noexec,nosuid 0       0 /host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1 /host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0  ================= sda3/Wubi: Location of files loaded by Grub: =================      9.3GB: boot/grub/grub.cfg    1.5GB: boot/initrd.img-2.6.32-26-generic    1.8GB: boot/initrd.img-2.6.35-23-generic   19.8GB: boot/vmlinuz-2.6.32-26-generic   19.8GB: boot/vmlinuz-2.6.35-23-generic    1.8GB: initrd.img    1.5GB: initrd.img.old   19.8GB: vmlinuz   19.8GB: vmlinuz.old =========================== Unknown MBRs/Boot Sectors/etc =======================  Unknown BootLoader  on sdc1  00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 c6 08  |.X.SYSLINUX.....| 00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 80 1f 00 00  |........?.......| 00000020  80 f0 ee 00 9d 3b 00 00  00 00 00 00 02 00 00 00  |.....;..........| 00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................| 00000040  80 00 29 55 08 55 1a 4e  4f 20 4e 41 4d 45 20 20  |..)U.U.NO NAME  | 00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...| 00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&amp;.x{...| 00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.| 00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M| 00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8| 000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..| 000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.| 000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r| 000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?| 000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..| 000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2| 00000100  7d 00 66 b8 b8 a9 8f 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......| 00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.&gt;$~4..ruv.| 00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..| 00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f| 00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`| 00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`| 00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..&gt;.|f..1| 00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...| 00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa| 00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.| 000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......| 000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........| 000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot| 000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........| 000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................| 000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.| 00000200

```
It needs to look like this.

[http://ubuntuforums.org/showpost.php?p=10141033&postcount=3](http://ubuntuforums.org/showpost.php?p=10141033&postcount=3)

Please highlight all the text in your Results.txt file on the desktop, copy it. Come to forums, click new reply, click #, paste your text in between the generated code tags so that [/code] at the end and [code] at the beginning.

Thanks.

---

### Post by sikuneh on 2010-12-03
I have no idea what was wrong last time. Half of the programs wouldn't work, including the text editor. So I opened it in Firefox and copy/pasted from there which turned into one GIGANTIC run on line.

Hows this?
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
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

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    30,801,919    30,720,000  82 Linux swap / Solaris
/dev/sda3          30,801,920   740,948,769   710,146,850   7 HPFS/NTFS
/dev/sda4         740,950,014   976,771,071   235,821,058   5 Extended
/dev/sda5         740,950,016   967,102,463   226,152,448  83 Linux
/dev/sda6         967,104,512   976,771,071     9,666,560  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8021 MB, 8021606400 bytes
5 heads, 32 sectors/track, 97920 cylinders, total 15667200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064    15,667,199    15,659,136   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       7a55c93a-6a3d-2349-b51e-1d1e57dc4dcf   ext2       casper-rw                     
/dev/loop2       8cf1132a-5a2f-4c23-8487-c236e22631d7   ext4                                     
/dev/mmcblk0p1   3418-977F                              vfat                                     
/dev/sda1        76bc12ff-f645-4020-af86-2cf0b1eeeff2   swap                                     
/dev/sda2        4a7404a7-4d8c-4dd7-8f43-dfd1e8b2ac7e   swap                                     
/dev/sda3        E8FA6D1CFA6CE870                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        d59dc544-38ba-4527-a7a4-86067b404960   ext4                                     
/dev/sda6        188fa69d-3761-47dc-a0d1-66eba670efcc   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1A55-0855                              vfat       NICK'S 8 GB                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mmcblk0p1   /media/3418-977F         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


======================== sda3/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set e8fa6d1cfa6ce870
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ntfs
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set e8fa6d1cfa6ce870
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-23-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set e8fa6d1cfa6ce870
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.35-23-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set e8fa6d1cfa6ce870
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set e8fa6d1cfa6ce870
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set e8fa6d1cfa6ce870
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-26-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
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

============================= sda3/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda3/Wubi: Location of files loaded by Grub: =================


   9.3GB: boot/grub/grub.cfg
   1.5GB: boot/initrd.img-2.6.32-26-generic
   1.8GB: boot/initrd.img-2.6.35-23-generic
  19.8GB: boot/vmlinuz-2.6.32-26-generic
  19.8GB: boot/vmlinuz-2.6.35-23-generic
   1.8GB: initrd.img
   1.5GB: initrd.img.old
  19.8GB: vmlinuz
  19.8GB: vmlinuz.old

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set d59dc544-38ba-4527-a7a4-86067b404960
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set d59dc544-38ba-4527-a7a4-86067b404960
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set d59dc544-38ba-4527-a7a4-86067b404960
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=d59dc544-38ba-4527-a7a4-86067b404960 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set d59dc544-38ba-4527-a7a4-86067b404960
    echo    'Loading Linux 2.6.35-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=d59dc544-38ba-4527-a7a4-86067b404960 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set d59dc544-38ba-4527-a7a4-86067b404960
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set d59dc544-38ba-4527-a7a4-86067b404960
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=d59dc544-38ba-4527-a7a4-86067b404960 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=188fa69d-3761-47dc-a0d1-66eba670efcc none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 383.8GB: boot/grub/core.img
 437.5GB: boot/grub/grub.cfg
 380.0GB: boot/initrd.img-2.6.35-23-generic-pae
 383.8GB: boot/vmlinuz-2.6.35-23-generic-pae
 380.0GB: initrd.img
 383.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 c6 08  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 80 1f 00 00  |........?.......|
00000020  80 f0 ee 00 9d 3b 00 00  00 00 00 00 02 00 00 00  |.....;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 55 08 55 1a 4e  4f 20 4e 41 4d 45 20 20  |..)U.U.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 b8 a9 8f 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by wilee-nilee on 2010-12-03
Not sure what to do with this one, you will need some expert help at the least. We have 2 totally different operating systems intertwined and yet missing so much in the script. The script can misread stuff though. I would make sure that you are running the script on a live booted Ubuntu cd or thumb, I think you did but your would best be served to see if running it again shows any different results.

Your probably gonna ant to state what you have as far as install discs in regard to Windows and Ubuntu, and what is backed up that you can't loose.

---

### Post by sikuneh on 2010-12-03
Here it is again. I haven't had a chance to back up anything yet... But all the files are there, I may be able to zip a ton of it.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
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

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    30,801,919    30,720,000  82 Linux swap / Solaris
/dev/sda3          30,801,920   740,948,769   710,146,850   7 HPFS/NTFS
/dev/sda4         740,950,014   976,771,071   235,821,058   5 Extended
/dev/sda5         740,950,016   967,102,463   226,152,448  83 Linux
/dev/sda6         967,104,512   976,771,071     9,666,560  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8021 MB, 8021606400 bytes
5 heads, 32 sectors/track, 97920 cylinders, total 15667200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064    15,667,199    15,659,136   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       7a55c93a-6a3d-2349-b51e-1d1e57dc4dcf   ext2       casper-rw                     
/dev/loop2       8cf1132a-5a2f-4c23-8487-c236e22631d7   ext4                                     
/dev/mmcblk0p1   3418-977F                              vfat                                     
/dev/sda1        76bc12ff-f645-4020-af86-2cf0b1eeeff2   swap                                     
/dev/sda2        4a7404a7-4d8c-4dd7-8f43-dfd1e8b2ac7e   swap                                     
/dev/sda3        E8FA6D1CFA6CE870                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        d59dc544-38ba-4527-a7a4-86067b404960   ext4                                     
/dev/sda6        188fa69d-3761-47dc-a0d1-66eba670efcc   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1A55-0855                              vfat       NICK'S 8 GB                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mmcblk0p1   /media/3418-977F         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


======================== sda3/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set e8fa6d1cfa6ce870
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ntfs
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set e8fa6d1cfa6ce870
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-23-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set e8fa6d1cfa6ce870
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.35-23-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set e8fa6d1cfa6ce870
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set e8fa6d1cfa6ce870
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set e8fa6d1cfa6ce870
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-26-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
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

============================= sda3/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda3/Wubi: Location of files loaded by Grub: =================


   9.3GB: boot/grub/grub.cfg
   1.5GB: boot/initrd.img-2.6.32-26-generic
   1.8GB: boot/initrd.img-2.6.35-23-generic
  19.8GB: boot/vmlinuz-2.6.32-26-generic
  19.8GB: boot/vmlinuz-2.6.35-23-generic
   1.8GB: initrd.img
   1.5GB: initrd.img.old
  19.8GB: vmlinuz
  19.8GB: vmlinuz.old

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set d59dc544-38ba-4527-a7a4-86067b404960
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set d59dc544-38ba-4527-a7a4-86067b404960
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set d59dc544-38ba-4527-a7a4-86067b404960
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=d59dc544-38ba-4527-a7a4-86067b404960 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set d59dc544-38ba-4527-a7a4-86067b404960
    echo    'Loading Linux 2.6.35-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=d59dc544-38ba-4527-a7a4-86067b404960 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set d59dc544-38ba-4527-a7a4-86067b404960
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set d59dc544-38ba-4527-a7a4-86067b404960
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=d59dc544-38ba-4527-a7a4-86067b404960 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=188fa69d-3761-47dc-a0d1-66eba670efcc none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 383.8GB: boot/grub/core.img
 437.5GB: boot/grub/grub.cfg
 380.0GB: boot/initrd.img-2.6.35-23-generic-pae
 383.8GB: boot/vmlinuz-2.6.35-23-generic-pae
 380.0GB: initrd.img
 383.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 c6 08  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 80 1f 00 00  |........?.......|
00000020  80 f0 ee 00 9d 3b 00 00  00 00 00 00 02 00 00 00  |.....;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 55 08 55 1a 4e  4f 20 4e 41 4d 45 20 20  |..)U.U.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 b8 a9 8f 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by wilee-nilee on 2010-12-03
Personally I'm just unable to concentrate well enough to be of any help. The good thing though is that there are others who are regular forum. daily posters, so it may be fixable, but being backed up will speed things up to just get to it when they see the script. If not tonight, but during the day tomorrow US time, probably.

Some of us have some specialized skills some have a very broad palate of experience, and skills.

---

### Post by sikander3786 on 2010-12-03
Have you got a Windows 7 repair disc? If yes, I would recommend to try Startup Repair from that, 3 times at least.

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)

Once you are able to boot Windows 7 successfully, everything should be pretty straight forward.

If the Windows 7 repair was successful, all you need to do is to boot Ubuntu/Mint Live CD and re-install Grub2.

```
sudo mount /dev/sda5 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Note, for the second command it is just sda without an integer and not sda5.

I am not sure about Wubi though. Anyhow, if that contains any important data, you can later mount root.disk folder and extract that once you are able to boot Windows successfully.

To be honest, your setup looks pretty messed up. Why did you need to create 2 swap partitions? And those too at the beginning and as a primary partition? And then another swap partition in extended/logical that make the total of 3 swaps.

If you've got the resources i.e, Windows install disc and all your important data (if any) is backed up, I would go for a clean install of both Ubuntu and Windows.

**[COLOR="Red"]Edit:[/COLOR]** And another thing, if you go for a recovery/repair, bootflag needs to be set to sda3 instead of sda2. You can use gparted from Ubuntu Live CD to do that.

And your dell recovery partition is being read as Swap by the script. :confused:

---

### Post by bcbc on 2010-12-03
All your windows 7 boot files were on /dev/sda2. This is now listed as "swap". When you run the windows bootloader (in /dev/sda) it looks at this partition for an OS, but can't find it. That's why you're getting the message: No os found.

Try and recover /dev/sda2 using testdisk and it will probably boot. Hopefully making it swap didn't destroy all the files and you can just recover it in place.

Otherwise, I'm not sure how Windows 7 could recover - other people know more about that than me.

---

### Post by sikuneh on 2010-12-03
I haven't had much luck, for some reason, in booting from CDs. I have the CD in my drive and I have the [burned] ISO file in there but it doesn't recognise that the CD can be live.

@bcbc: I looked at Testdisk but I downloaded all the linux distributions and none worked. I'm running ubuntu 10.10. Which one do I download?

@sikander3786: I tried that but it can't find the bootmanager

Can you perform a windows backup from ubuntu?

---

### Post by sikuneh on 2010-12-03
Ok, I can't get anything work. I just have one more question: If I format my OS partition would that remove all my windows files, including the boot files because I don't have a windows install disk.

---

### Post by sikander3786 on 2010-12-04
Yes a format would definitely remove everything on that particular partition includin the OS, boot files and even personal files.

I would recommend to give testdisk a shot from Live CD.

[https://help.ubuntu.com/community/DataRecovery#Testdisk](https://help.ubuntu.com/community/DataRecovery#Testdisk)

---

### Post by sikuneh on 2010-12-04
I'll come out and admit I have no idea what to do after I load it it up. Assuming all the data from the previous stuff is accurate, what do I do now?

---

### Post by bcbc on 2010-12-04
[http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_reformatted_partition](http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_reformatted_partition)
> Recovery of reformatted partition

If the partition has been reformatted to another file system (FAT32 formatted as NTFS or vice-versa),
run TestDisk,
select the hard disk and the partition type
choose Advanced
select the partition
choose Type,
enter the value corresponding to the previous filesystem
choose Boot
choose RebuildBS
List
If you can see your files, choose Write and confirm
In Analyse, choose to rewrite the partition with the correct partition type.

To run testdisk, boot an Ubuntu live CD, 10.10 is fine. Install testdisk and run it:
```
sudo apt-get install testdisk
sudo testdisk
```
You'll be selecting /dev/sda2 and switching it to ntfs
You could probably repair /dev/sda1 too as that isn't swap either, it's likely Fat16 (Dell utility) - at least on my Dell it's Fat16

---

### Post by sikuneh on 2010-12-05
Ok I repaired startup from an upgrade CD (which apparently you can do) and after trying everything I have one last resort: formatting. I have one question before I try this, can you install windows 7 from an upgrade disk?

Also, I have about 5-6 partitions on my hard drive, would it be wise to just delete them and reinstall ubuntu?

Does windows have a partition manager built in or somewhere I can find one?

---

