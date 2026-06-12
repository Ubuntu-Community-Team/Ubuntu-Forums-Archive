---
title: "Use Grub instead of Win 7 boot loader"
date: 2010-08-26
forum: General Help
---

### Post by JoeGoalie on 2010-08-26
Every dual boot guide and every dual boot I've set up I've done the same way. Always install Windows first then install Ubuntu. Well, this time Windows didn't let go of the bootloader it seems like. I have kind of an awkward setup for hard drives...
32gb SSD /
2X250gb raid1 /home
3gb(at beginning of 1tb HDD) swap
The rest of the TB is Windows 7 Home Premium
I installed Windows 7 without problems the installed Ubuntu 10.04 x64 without problems. It asked if I wanted grub to overwrite mbr I said yes. Computer rebooted... Straight into Windows. I downloaded EasyBCD and added grub to Windows boot menu. The option works great, goes straight into grub. Grub even has Windows listed.

Why is my computer using Windows boot manager and how do I switch it to grub? I'm very confused.

---

### Post by oldfred on 2010-08-26
Grub typically overwrites which ever drive it sees as sda or hd0 as it assumes you boot from that. Are you booting from a drive that the system does not see as sda? 

To see where everything is at -  from liveCD:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by JoeGoalie on 2010-08-26
No, I'm not booting Windows from the sda drive. Is there a guide to move or install grub to a different hdd?

---

### Post by -kg- on 2010-08-26
I have a similar "awkward hard drive setup" on my desktop.  I have two PATA hard drives and a 1 TB internal SATA drive.  I, also, had trouble with GRUB installation when I first installed Ubuntu on it, after I installed the SATA drive.  The situation was this:

When I installed the SATA drive, it changed the apparent drive designations.  My SATA drive is now sda, with my two PATA (IDE) drives being sdb and sdc, respectively.  BIOS still recognizes sdb as the drive with the bootloader and checks it for booting information, but the Ubuntu installer doesn't.

If I allowed the installer to install GRUB in the default location, it installed on sda, which in this case was the SATA drive.  Of course, when I rebooted, BIOS would look on sdb for GRUB, which of course wasn't there.

What you need to do is to determine which drive BIOS looks to for booting information.  I would assume that BIOS is looking at the drive that Windows in installed on, but not necessarily.  When you find that out, you need to see what drive designation (sdb, sdc, or whatever), you need to install GRUB in the MBR of that drive.

During installation, you would go through to the last step of the installer, in which it shows you what steps are going to be taken.  There is a button marked "Advanced" there, which allows you to select the location to install GRUB.  You would choose the drive (or partition, like sdb1, sdc2, etc., but that's not what you want) to install GRUB to.  Default is sda; I had to select sdb.  You need to install to whatever your BIOS recognizes as the "Master Drive."

If you don't want to reinstall Ubuntu, then you should be able to install using the "sudo grub-install" command.  Instructions on its usage is on the following page:

[https://help.ubuntu.com/community/Grub2#Changing%20or%20Moving%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Changing%20or%20Moving%20GRUB%202")

---

### Post by JoeGoalie on 2010-08-26
Thanks for the help guys.  As both installs are clean installs I think I might just switch the SATA ports the HDD's are plugged into in order to have windows on the sda drive.  That seems simple enough.

As for an advanced install option, I never saw one.  I was using an alternate install cd as I am setting up software raids.  Maybe that's why, I'm not sure.

---

### Post by oldfred on 2010-08-26
The alternate install is a little different.

[http://members.iinet.net.au/~herman546/p6.html#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location](http://members.iinet.net.au/~herman546/p6.html#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location)

From this which may be a slightly older version:
[http://members.iinet.net.au/~herman546/p2.html](http://members.iinet.net.au/~herman546/p2.html)

But if you really want to know what is where run the boot info script. I run it before and after any system changes just to document what is where.

---

### Post by JoeGoalie on 2010-08-27
This is a behemoth of a "code" lol.  I switched the disks on my motherboard and it didn't work.  I still need to find what dive to install grub to.  I think I understand the link you gave me to show ubuntu where to install grub.  I just need to know where to actually put it. :)
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

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
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc6: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdd6: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,947,230,207 1,947,228,160   7 HPFS/NTFS
/dev/sda2       1,947,232,254 1,953,523,711     6,291,458   5 Extended
/dev/sda5       1,947,232,256 1,953,523,711     6,291,456  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 32.0 GB, 32044482560 bytes
255 heads, 63 sectors/track, 3895 cylinders, total 62586880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             208,894    62,584,831    62,375,938   5 Extended
/dev/sdb5             208,896    62,584,831    62,375,936  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,046   488,396,799   488,394,754   5 Extended
/dev/sdc5               2,048   468,944,895   468,942,848  fd Linux raid autodetect
/dev/sdc6         468,946,944   488,396,799    19,449,856  fd Linux raid autodetect


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,046   488,396,799   488,394,754   5 Extended
/dev/sdd5               2,048   468,944,895   468,942,848  fd Linux raid autodetect
/dev/sdd6         468,946,944   488,396,799    19,449,856  fd Linux raid autodetect


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D4609F62609F49DE                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        63785bb4-5418-4b7c-8433-d2e8df16cba0   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F0269DEB269DB2D8                       ntfs       System Reserved               
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        c46d2701-2085-49c4-882c-e88fac1fc05f   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1: PTTYPE="dos" 
/dev/sdc5        f4a9db37-b83f-3fcf-2cbf-fd6c5fcae8c7   linux_raid_member                               
/dev/sdc6        017832c9-9e3c-1f29-686a-66b64903a7ff   linux_raid_member                               
/dev/sdc: PTTYPE="dos" 
/dev/sdd1: PTTYPE="dos" 
/dev/sdd5        f4a9db37-b83f-3fcf-2cbf-fd6c5fcae8c7   linux_raid_member                               
/dev/sdd6        017832c9-9e3c-1f29-686a-66b64903a7ff   linux_raid_member                               
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set c46d2701-2085-49c4-882c-e88fac1fc05f
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set c46d2701-2085-49c4-882c-e88fac1fc05f
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set c46d2701-2085-49c4-882c-e88fac1fc05f
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c46d2701-2085-49c4-882c-e88fac1fc05f ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set c46d2701-2085-49c4-882c-e88fac1fc05f
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c46d2701-2085-49c4-882c-e88fac1fc05f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set c46d2701-2085-49c4-882c-e88fac1fc05f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set c46d2701-2085-49c4-882c-e88fac1fc05f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set f0269deb269db2d8
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=c46d2701-2085-49c4-882c-e88fac1fc05f /               ext4    errors=remount-ro 0       1
# /AndroidSDK was on /dev/md0 during installation
UUID=2db71f46-a997-4cf2-8b83-8036ad0523b4 /AndroidSDK     ext4    defaults        0       2
# /home was on /dev/md1 during installation
UUID=ad6c6fd1-456e-4eaa-892a-60ef92e0b61c /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=63785bb4-5418-4b7c-8433-d2e8df16cba0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


  17.4GB: boot/grub/core.img
  17.4GB: boot/grub/grub.cfg
  17.6GB: boot/initrd.img-2.6.32-21-generic
    .3GB: boot/vmlinuz-2.6.32-21-generic
  17.6GB: initrd.img
    .3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  3f 50 5f dd d9 23 72 05  6e cd 7a de 3a 9a 95 06  |?P_..#r.n.z.:...|
00000010  af d9 ff 5b 98 88 88 20  5a ef cf 3a 27 eb ad 1d  |...[... Z..:'...|
00000020  bd ab d9 9e 9b ed 5b 66  71 74 1e 0b 1c f0 74 7b  |......[fqt....t{|
00000030  3c 3d ea d2 ef ef 2b 23  d7 e2 2e 38 20 78 c8 e1  |<=....+#...8 x..|
00000040  24 e8 cf 69 8b d7 15 25  c0 f1 da b5 26 ed 73 70  |$..i...%....&.sp|
00000050  20 c9 08 86 0a e9 28 1f  f9 d9 a2 da 91 a5 50 dc  | .....(.......P.|
00000060  b0 ee fe ea 87 22 f1 6b  3e 3f 9a 95 b4 73 de e0  |.....".k>?...s..|
00000070  05 aa 48 02 50 54 82 cf  09 20 24 d7 2d ce 79 5a  |..H.PT... $.-.yZ|
00000080  bf b1 0c fc 1a b1 e6 8c  48 e3 ac 37 f9 97 ae 5f  |........H..7..._|
00000090  6b 9d 17 ab 19 18 5b d6  80 79 e4 cd c0 8b 4f 20  |k.....[..y....O |
000000a0  01 28 25 38 2e 66 b5 27  e3 79 a9 b8 05 da c6 a2  |.(%8.f.'.y......|
000000b0  c8 08 2e 0d 6d 43 03 76  44 41 82 c3 d7 ca d0 a2  |....mC.vDA......|
000000c0  f6 1c 25 4c ed 74 59 88  c4 50 6c 2f 2e da 83 e5  |..%L.tY..Pl/....|
000000d0  54 d8 17 86 da 59 35 4d  4c 9e d8 54 0c 89 92 93  |T....Y5ML..T....|
000000e0  5b db 29 36 de 7d f0 10  05 13 0f da a0 0d e3 a8  |[.)6.}..........|
000000f0  5b 14 57 4f 70 5e 34 e4  f1 d4 49 b8 59 29 51 54  |[.WOp^4...I.Y)QT|
00000100  45 75 e9 e1 5a db 39 93  a9 54 d4 d0 71 b6 c1 c9  |Eu..Z.9..T..q...|
00000110  96 0d 42 78 de 89 fe e9  c0 da 10 dd c9 ae 87 94  |..Bx............|
00000120  af e7 5c a2 8f 13 1a d1  28 ac 96 a2 05 8e 7d b6  |..\.....(.....}.|
00000130  af d9 d5 bc 70 07 fe 0c  ab 74 2b b6 30 02 92 42  |....p....t+.0..B|
00000140  42 1e d4 92 77 01 4b 8d  b7 c0 b8 89 2e 25 b2 14  |B...w.K......%..|
00000150  34 aa d4 13 0e 10 7d 77  cc b7 58 7e ef d2 04 93  |4.....}w..X~....|
00000160  d0 37 23 97 38 05 d1 c3  9e 17 90 32 92 ed 3e be  |.7#.8......2..>.|
00000170  d5 1f 7a 71 fc aa 6f 10  a9 81 68 b0 1c 74 1e 83  |..zq..o...h..t..|
00000180  46 85 61 f6 5f b7 32 51  24 25 1e 99 30 42 2d ad  |F.a._.2Q$%..0B-.|
00000190  e2 4b c9 15 0f d6 87 37  19 f3 35 95 dd 46 10 e8  |.K.....7..5..F..|
000001a0  02 63 52 24 9d 9a 2d 44  33 4f 00 38 c7 98 a0 ca  |.cR$..-D3O.8....|
000001b0  c1 8a 20 11 17 10 a0 ee  c2 c8 78 68 06 4c 00 fe  |.. .......xh.L..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 00 60 00 00 00  |............`...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  51 c9 b4 92 4f 2b eb 97  6c db 2a e6 db 1f 7a 32  |Q...O+..l.*...z2|
00000010  ab db 13 d7 61 75 0e 53  42 eb 10 27 57 9a d6 4c  |....au.SB..'W..L|
00000020  85 f0 fa 74 da 93 99 11  4f e7 31 f0 23 04 bb 27  |...t....O.1.#..'|
00000030  e9 cf 90 22 5b 77 3e db  ed 84 ca 0e 02 60 1c e5  |..."[w>......`..|
00000040  e9 37 24 5b 9e 09 32 69  22 e8 aa 13 13 b2 d1 ab  |.7$[..2i".......|
00000050  f3 ba f6 98 ba ff 4c 4a  7d 2a db 7d 57 b6 7c 67  |......LJ}*.}W.|g|
00000060  b6 7b 26 24 ee 36 20 5b  7e 04 12 e7 24 d8 61 65  |.{&$.6 [~...$.ae|
00000070  ca c6 2a 57 41 e2 6c 98  48 20 73 ef 25 82 1f b2  |..*WA.l.H s.%...|
00000080  dd b7 8c f2 c4 41 b6 5d  b3 e5 07 21 b1 94 68 87  |.....A.]...!..h.|
00000090  f9 9d 8d 62 29 8b 72 ee  7c 13 24 b4 eb f6 66 bb  |...b).r.|.$...f.|
000000a0  6f b2 cb 37 67 bb 1f 84  9c a3 bb d8 e5 d1 a0 13  |o..7g...........|
000000b0  54 82 3d b2 8a cd 7f 60  ee 76 98 de 3d 05 32 8f  |T.=....`.v..=.2.|
000000c0  39 b0 0f 69 b6 d8 dd e2  48 4f ea 6d 76 b9 ad 24  |9..i....HO.mv..$|
000000d0  cf 85 f4 4c 56 04 45 c4  1d 76 77 11 7a e1 fa 08  |...LV.E..vw.z...|
000000e0  92 4b ba cb 92 3b 65 a4  27 7a 80 24 df 4b 0e ef  |.K...;e.'z.$.K..|
000000f0  e4 25 8b 69 39 df a8 11  22 3d 20 75 15 a6 8e 7c  |.%.i9..."= u...||
00000100  c2 c8 28 24 b9 1c 93 52  02 20 bc 51 be 7c 72 73  |..($...R. .Q.|rs|
00000110  8b f2 e5 40 97 10 f9 92  1c 94 2f 56 f9 33 33 0a  |...@....../V.33.|
00000120  14 12 23 55 02 13 32 a2  d5 fd bc 39 54 cc 88 35  |..#U..2....9T..5|
00000130  63 f4 21 32 86 d4 27 ab  fc bc 39 20 65 7a eb 5b  |c.!2..'...9 ez.[|
00000140  92 32 b8 19 7b 57 3e 9b  b4 78 74 d3 e6 19 67 4e  |.2..{W>..xt...gN|
00000150  b0 56 3d 6f 8e 83 80 1e  6c 48 26 48 62 31 7e 85  |.V=o....lH&Hb1~.|
00000160  c0 96 ba e1 36 f7 38 f3  0c c9 b5 05 94 a8 c7 61  |....6.8........a|
00000170  65 9a 61 c4 b7 ae 67 cf  7d 24 5d d8 69 f7 cc 85  |e.a...g.}$].i...|
00000180  a9 e4 57 0e ed 26 5f 40  62 f5 10 3c d2 e2 76 98  |..W..&_@b..<..v.|
00000190  41 be 5c b6 cb bf a0 fb  a0 fd 8f e0 06 4d 94 cd  |A.\..........M..|
000001a0  f5 b4 39 1e 64 e7 94 2e  f8 a6 6e b2 d9 24 d6 54  |..9.d.....n..$.T|
000001b0  74 21 69 b5 06 b4 b5 6c  8f 1d dd 99 f7 ae 00 00  |t!i....l........|
000001c0  34 0d 83 fe ff ff 02 00  00 00 00 c8 b7 03 00 00  |4...............|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by oldfred on 2010-08-27
It looks like if you boot sda - 1000 GB you will boot Ubuntu. Either grub2 or the script mis report the drive so even though it says same drive the sdb5 is the partition it is booting. If you are booting windows directly then you are currently booting sdb the 32GB SSD. Go into BIOS or use one time boot key to boot 1TB drive and see it Ubuntu boots.

You have window's boot/recovery 100mb partition on sdb1 but your full windows partition on sda1?

---

### Post by JoeGoalie on 2010-08-27
> **oldfred said:**
> It looks like if you boot sda - 1000 GB you will boot Ubuntu. Either grub2 or the script mis report the drive so even though it says same drive the sdb5 is the partition it is booting. If you are booting windows directly then you are currently booting sdb the 32GB SSD. Go into BIOS or use one time boot key to boot 1TB drive and see it Ubuntu boots.

You have window's boot/recovery 100mb partition on sdb1 but your full windows partition on sda1?

Funny because Windows is on the 1tb while Ubuntu is on the 32gb SSD. The stupid Windows partition is what it did automatically. At this point I don't care anymore I just want the damn thing to work.

---

### Post by JoeGoalie on 2010-08-28
I ended up getting it to work.  Like I said, both installs were clean installs so I didn't mind doing it again.  I plugged the 1tb into the sda spot on my motherboard and unplugged every other hdd. It forced the Windows install to be on the 1tb completely.  Then I replugged all the other hdd's in and installed Ubuntu.  Grub then automatically wrote to sda which is where Windows actually was this time.  I wonder why Windows was defaulting to installing the boot loader on a different drive? Very odd.

---

