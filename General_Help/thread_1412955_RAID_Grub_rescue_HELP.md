---
title: "RAID Grub rescue HELP"
date: 2010-02-21
forum: General Help
---

### Post by linuxcss on 2010-02-21
[LEFT]I just rebooted a raid system and all i see is the Grub rescue prompt,

last shutdown wasn't clean but I have booted with gparted and done
fsck on the md parts

what do i do to get it to boot?

partition i want it to boot is md125 (sda6/sdb6)



[/LEFT]

---

### Post by linuxcss on 2010-02-21
still can not boot .... need this working tonight

anybody have idea to make this work on RAID1 

install was done with alternate install

at grub rescue> 
help does not work ... ls
produces
(md124)(md1)(md126)(md127)(hd0) (hd0,7)(hd0,6)(hd0,5)(hd0,3)(hd0,1)(hd1)(hd1,7)(hd1,6)(hd1,5)(hd1,1)

i want md126 to boot that was paired with (sda6/sdb6) md126 and has /  ... (sda7/sdb7) md127 is /home

---

### Post by linuxcss on 2010-02-22
just ran boot_info_script055.sh (full output below)

can anyone tell me how i can get this working in next 20 mins .... 
I am running karmic alternate install with ubuntu software RAID1 

I want to boot /dev/md126 

what exactly do i need to do????


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for (md126)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for (md126)/boot/grub.
 => Windows is installed in the MBR of /dev/sdh

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdh1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

md/127_0: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

md/126_0: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: /dev/md126 already mounted or MDRaid/md/126_0 busy
mount: according to mtab, /dev/md126 is mounted on /home/user/sda6

md/1_0: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

md/124_0: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

hda: _________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c93e6

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    12,289,724    12,289,662  fd Linux raid autodetect
/dev/sda2          12,289,725   299,547,989   287,258,265   5 Extended
/dev/sda5          12,289,788    30,716,279    18,426,492  fd Linux raid autodetect
/dev/sda6          30,716,343    63,488,879    32,772,537  fd Linux raid autodetect
/dev/sda7          63,488,943   299,547,989   236,059,047  fd Linux raid autodetect
/dev/sda3         943,995,465   976,768,064    32,772,600  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a521d

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    12,289,724    12,289,662  fd Linux raid autodetect
/dev/sdb2          12,289,725   299,547,989   287,258,265   5 Extended
/dev/sdb5          12,289,788    30,716,279    18,426,492  fd Linux raid autodetect
/dev/sdb6          30,716,343    63,488,879    32,772,537  fd Linux raid autodetect
/dev/sdb7          63,488,943   299,547,989   236,059,047  fd Linux raid autodetect


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 16.2 GB, 16173236224 bytes
101 heads, 40 sectors/track, 7818 cylinders, total 31588352 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sdh1    *             40    31,588,351    31,588,312   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/hda                                                iso9660    GParted-live                  
/dev/loop0                                              squashfs                                 
/dev/md/1_0      dc622091-fba0-45af-ad8b-3aa6f87de109   swap                                     
/dev/md/124_0    f11570d4-fb4d-489c-97d4-26c2e2641a54   ext3                                     
/dev/md124       f11570d4-fb4d-489c-97d4-26c2e2641a54   ext3                                     
/dev/md125       dc622091-fba0-45af-ad8b-3aa6f87de109   swap                                     
/dev/md/126_0    5ab41392-696f-4d12-a8d0-5c2fd9eee97b   ext4       normRoot                      
/dev/md126       5ab41392-696f-4d12-a8d0-5c2fd9eee97b   ext4       normRoot                      
/dev/md/127_0    00879ffd-8b9e-42eb-8bbe-a30cf0f7c91c   ext4                                     
/dev/md127       00879ffd-8b9e-42eb-8bbe-a30cf0f7c91c   ext4                                     
/dev/sda1        c3430a77-a48a-f1aa-8868-f8cfc824fefa   linux_raid_member                               
/dev/sda3        3687cf24-1ffc-4ff1-b2d8-9d78c6783a4d   ext3                                     
/dev/sda5        7d7d292b-3fcf-4e17-7139-6ecf3d55c77e   linux_raid_member                               
/dev/sda6        c79e53bd-0d6e-9c35-35df-44364839faed   linux_raid_member                               
/dev/sda7        fd364590-9edd-e5d6-4007-6ee93b02ee88   linux_raid_member                               
/dev/sdb1        c3430a77-a48a-f1aa-8868-f8cfc824fefa   linux_raid_member                               
/dev/sdb5        7d7d292b-3fcf-4e17-7139-6ecf3d55c77e   linux_raid_member                               
/dev/sdb6        c79e53bd-0d6e-9c35-35df-44364839faed   linux_raid_member                               
/dev/sdb7        fd364590-9edd-e5d6-4007-6ee93b02ee88   linux_raid_member                               
/dev/sdh1        9a9a3d52-d395-4421-bd0c-6790463c97da   ext3       cors16gb                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/hda         /live/image              iso9660    (ro,noatime)
/dev/md126       /home/user/sda6          ext4       (rw)
/dev/sdh1        /home/user/corsair       ext3       (rw)


========================= md/124_0/boot/grub/grub.cfg: =========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod raid
insmod mdraid
insmod ext2
set root=(md0)
search --no-floppy --fs-uuid --set f11570d4-fb4d-489c-97d4-26c2e2641a54
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod raid
    insmod mdraid
    insmod ext2
    set root=(md0)
    search --no-floppy --fs-uuid --set f11570d4-fb4d-489c-97d4-26c2e2641a54
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=f11570d4-fb4d-489c-97d4-26c2e2641a54 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod raid
    insmod mdraid
    insmod ext2
    set root=(md0)
    search --no-floppy --fs-uuid --set f11570d4-fb4d-489c-97d4-26c2e2641a54
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=f11570d4-fb4d-489c-97d4-26c2e2641a54 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod raid
    insmod mdraid
    insmod ext2
    set root=(md0)
    search --no-floppy --fs-uuid --set f11570d4-fb4d-489c-97d4-26c2e2641a54
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f11570d4-fb4d-489c-97d4-26c2e2641a54 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod raid
    insmod mdraid
    insmod ext2
    set root=(md0)
    search --no-floppy --fs-uuid --set f11570d4-fb4d-489c-97d4-26c2e2641a54
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f11570d4-fb4d-489c-97d4-26c2e2641a54 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
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

============================= md/124_0/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/md0 during installation
UUID=f11570d4-fb4d-489c-97d4-26c2e2641a54 /               ext3    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

================= md/124_0: Location of files loaded by Grub: =================


   1.6GB: boot/grub/core.img
   1.5GB: boot/grub/grub.cfg
   1.0GB: boot/initrd.img-2.6.31-14-generic
   1.1GB: boot/initrd.img-2.6.31-19-generic
   1.0GB: boot/vmlinuz-2.6.31-14-generic
   1.1GB: boot/vmlinuz-2.6.31-19-generic
   2.5GB: grub/core.img
   1.1GB: initrd.img
   1.0GB: initrd.img.old
   1.1GB: vmlinuz
   1.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on hda

00000000  fa 31 c0 8e d8 8e d0 bc  00 7c 89 e6 06 57 8e c0  |.1.......|...W..|
00000010  fb fc bf 00 06 b9 00 01  f3 a5 ea 1f 06 00 00 52  |...............R|
00000020  52 b4 41 bb aa 55 31 c9  30 f6 f9 cd 13 72 14 81  |R.A..U1.0....r..|
00000030  fb 55 aa 75 0e 83 e1 01  74 09 66 c7 06 b6 06 b4  |.U.u....t.f.....|
00000040  42 eb 15 5a 51 b4 08 cd  13 83 e1 3f 51 0f b6 c6  |B..ZQ......?Q...|
00000050  40 50 f7 e1 52 50 bb 00  7c b9 04 00 66 a1 b0 07  |@P..RP..|...f...|
00000060  e8 42 00 72 76 66 40 80  c7 02 e2 f4 66 81 3e 40  |.B.rvf@.....f.>@|
00000070  7c fb c0 78 70 75 09 fa  bc f4 7b ea 44 7c 00 00  ||..xpu....{.D|..|
00000080  e8 79 00 69 73 6f 6c 69  6e 75 78 2e 62 69 6e 20  |.y.isolinux.bin |
00000090  6d 69 73 73 69 6e 67 20  6f 72 20 63 6f 72 72 75  |missing or corru|
000000a0  70 74 2e 0d 0a 66 60 66  31 d2 66 52 66 50 06 53  |pt...f`f1.fRfP.S|
000000b0  6a 01 6a 10 89 e6 66 f7  36 f0 7b c0 e4 06 88 e1  |j.j...f.6.{.....|
000000c0  88 c5 92 f6 36 f6 7b 88  c6 08 e1 41 b8 01 02 8a  |....6.{....A....|
000000d0  16 fa 7b cd 13 8d 64 10  66 61 c3 e8 1e 00 4f 70  |..{...d.fa....Op|
000000e0  65 72 61 74 69 6e 67 20  73 79 73 74 65 6d 20 6c  |erating system l|
000000f0  6f 61 64 20 65 72 72 6f  72 2e 0d 0a 5e ac b4 0e  |oad error...^...|
00000100  8a 3e 62 04 b3 07 cd 10  3c 0a 75 f1 cd 18 f4 eb  |.>b.....<.u.....|
00000110  fd 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  ac 5e 03 00 00 00 00 00  86 f5 f7 f0 00 00 80 00  |.^..............|
000001c0  01 00 83 3f 20 6c 00 00  00 00 00 68 03 00 00 00  |...? l.....h....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg 
=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file or automatically

---

