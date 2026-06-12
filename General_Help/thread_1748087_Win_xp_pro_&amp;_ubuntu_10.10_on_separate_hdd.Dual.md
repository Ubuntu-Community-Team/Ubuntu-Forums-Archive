---
title: "Win xp pro &amp; ubuntu 10.10 on separate hdd.Dual boot problem"
date: 2011-05-03
forum: General Help
---

### Post by nathan soulfly on 2011-05-03
Hey people.I m new to ubuntu (about a mounth).I like them a lot but want to be able to use windows also.My problem is with the dual booting.I have two hdd on my pc.The master is 30gb and the slave is 60gb.I have installed windows xp pro on the master and ubuntu 10.10 on the slave.When i open my pc it starts with ubuntu,no boot screen to chose an o.s no nothing.I have read lots and lots of things about how to make a dual boot but i cant make it work.Here is how i made the installation based on something i read about how to make a dual boot:

During the installation of win xp pro on the 30gb m hdd (/dev/sda) i made a partition of 1gb and installation win xp on the second partition the 29gb.The windows where working fine.
For ubuntu i used the 1 gb i had partitioned in the master and made it ext4 mounted as /boot (/dev/sda1).On the slave 60db hdd (/dev/sdb) ive made three partitions.The first 25gb ext4 mounted as / (dev/sdb1) .The second 33gb ext4 mounted as /home (dev/sdb5).And the third 2.5gb swap (/dev/sdb6).

help
thank you in advance

---

### Post by Mark Phelps on 2011-05-03
GRUB doesn't automatically detect other OSs on a PC, you have to tell it to do that.  Open a terminal and enter "sudo update-grub".  That will generate a new GRUB menu which should add an entry for your Windows OS.

---

### Post by nathan soulfly on 2011-05-03
**Mark Phelps**;10762444]GRUB doesn't automatically detect other OSs on a PC, you have to tell it to do that.  Open a terminal and enter "sudo update-grub".  That will generate a new GRUB menu which should add an entry for your Windows OS.

Done the "sudo update-grub".Nothing

---

### Post by oldfred on 2011-05-03
Post results.txt from this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by nathan soulfly on 2011-05-03
> **oldfred said:**
> Post results.txt from this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.



ive tried and here is what it came to the terminal:

soulfly@soulfly-desktop:~$ sudo bash file system/home/soulfly/downloads/boot_info_script055.sh
[sudo] password for soulfly: 
/usr/bin/file: /usr/bin/file: cannot execute binary file

---

### Post by oldfred on 2011-05-03
If it is in Downloads you can either cd to Downloads or run this

sudo bash ~/Downloads/boot_info_script*.sh 

I do not think you have a downloads folder unless you created it. The default is Downloads.

Linux is case sensitive.

---

### Post by nathan soulfly on 2011-05-03
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders, total 58633344 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     2,039,807     2,037,760  83 Linux
/dev/sda2           2,040,316    58,605,119    56,564,804   f W95 Ext d (LBA)
/dev/sda5           2,040,318    58,605,119    56,564,802   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders, total 117266688 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    48,828,415    48,826,368  83 Linux
/dev/sdb2          48,830,462   117,264,383    68,433,922   5 Extended
/dev/sdb5          48,830,464   112,386,047    63,555,584  83 Linux
/dev/sdb6         112,388,096   117,264,383     4,876,288  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
1 heads, 63 sectors/track, 15504336 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   976,768,127   976,768,065   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7a17ecec-d795-4026-8b5c-f491aa426318   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        180C3A190C39F1FC                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        b6595e12-20e3-4de2-9127-92da4e71d8a3   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        06bf6bc8-6613-4e0c-858f-e99d6f403db6   ext4                                     
/dev/sdb6        777abc3f-0035-4816-8c20-badb3997243b   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        284064F24064C7E0                       ntfs       Expansion Drive               
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /boot                    ext4       (rw,commit=0)
/dev/sdb5        /home                    ext4       (rw,commit=0)
/dev/sdc1        /media/Expansion Drive   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


============================= sda1/grub/grub.cfg: =============================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set b6595e12-20e3-4de2-9127-92da4e71d8a3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 7a17ecec-d795-4026-8b5c-f491aa426318
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7a17ecec-d795-4026-8b5c-f491aa426318
    linux    /vmlinuz-2.6.35-28-generic root=UUID=b6595e12-20e3-4de2-9127-92da4e71d8a3 ro   quiet splash
    initrd    /initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7a17ecec-d795-4026-8b5c-f491aa426318
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /vmlinuz-2.6.35-28-generic root=UUID=b6595e12-20e3-4de2-9127-92da4e71d8a3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7a17ecec-d795-4026-8b5c-f491aa426318
    linux    /vmlinuz-2.6.35-22-generic root=UUID=b6595e12-20e3-4de2-9127-92da4e71d8a3 ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7a17ecec-d795-4026-8b5c-f491aa426318
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=b6595e12-20e3-4de2-9127-92da4e71d8a3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7a17ecec-d795-4026-8b5c-f491aa426318
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7a17ecec-d795-4026-8b5c-f491aa426318
    linux16    /memtest86+.bin console=ttyS0,115200n8
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

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: grub/core.img
    .1GB: grub/grub.cfg
    .1GB: initrd.img-2.6.35-22-generic
    .1GB: initrd.img-2.6.35-28-generic
    .1GB: vmlinuz-2.6.35-22-generic
    .2GB: vmlinuz-2.6.35-28-generic

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
UUID=b6595e12-20e3-4de2-9127-92da4e71d8a3 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=7a17ecec-d795-4026-8b5c-f491aa426318 /boot           ext4    defaults        0       2
# /home was on /dev/sdb5 during installation
UUID=06bf6bc8-6613-4e0c-858f-e99d6f403db6 /home           ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=777abc3f-0035-4816-8c20-badb3997243b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: initrd.img
    .1GB: initrd.img.old
    .2GB: vmlinuz
    .1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  73 39 f0 73 39 f0 73 39  f0 73 39 f0 73 39 f0 73  |s9.s9.s9.s9.s9.s|
00000010  39 f0 73 39 f0 73 39 f0  73 39 f0 73 39 f0 73 39  |9.s9.s9.s9.s9.s9|
00000020  f0 73 39 f0 73 39 ee 71  37 ee 71 37 ee 71 37 ee  |.s9.s9.q7.q7.q7.|
00000030  71 37 ee 71 37 ee 71 37  ee 71 37 ee 71 37 f0 73  |q7.q7.q7.q7.q7.s|
00000040  39 f0 73 39 f0 73 39 f0  73 39 f0 73 39 f0 73 39  |9.s9.s9.s9.s9.s9|
00000050  f0 73 39 f0 73 39 f0 73  39 f0 74 38 f1 73 39 f0  |.s9.s9.s9.t8.s9.|
00000060  74 38 f0 73 39 f0 73 39  f0 73 39 f0 73 39 ee 71  |t8.s9.s9.s9.s9.q|
00000070  37 ee 71 37 ee 71 37 ee  71 37 ee 71 37 ec 71 37  |7.q7.q7.q7.q7.q7|
00000080  ee 71 37 ec 71 39 f0 72  3b ee 72 3c f0 72 3c ee  |.q7.q9.r;.r<.r<.|
00000090  72 3c f0 72 3c ee 72 3c  ee 72 3c ee 71 3e ee 71  |r<.r<.r<.r<.q>.q|
000000a0  3e ee 71 3e ee 71 3e ee  71 3e ee 71 3e ee 71 3e  |>.q>.q>.q>.q>.q>|
000000b0  ee 71 3f ec 71 3f ed 74  42 eb 75 42 eb 75 42 eb  |.q?.q?.tB.uB.uB.|
000000c0  75 42 eb 75 42 eb 74 43  eb 74 43 eb 74 43 f2 7b  |uB.uB.tC.tC.tC.{|
000000d0  4a f2 7c 4b f3 7d 4e f4  7e 4f f6 80 51 f7 81 52  |J.|K.}N.~O..Q..R|
000000e0  f8 82 53 f7 83 54 f5 84  52 f3 84 52 f2 85 52 f0  |..S..T..R..R..R.|
000000f0  84 54 f0 84 55 ee 83 57  eb 83 58 e9 83 59 e8 83  |.T..U..W..X..Y..|
00000100  5c e8 87 63 eb 8a 68 e9  8a 69 e8 8b 6a ed 92 73  |\..c..h..i..j..s|
00000110  f8 9e 80 fc a8 8e fa b4  9d f2 b0 9d f0 ae 9b ee  |................|
00000120  af 9b f0 b1 9d f1 b5 9f  f7 b8 a3 f8 ba a2 f0 b2  |................|
00000130  9a ee b1 97 ef af 96 f1  af 96 f3 b0 95 f3 ae 93  |................|
00000140  ef a8 8d ec a2 88 f5 a8  8e f5 a5 8c f3 a3 8a f1  |................|
00000150  a1 88 f3 a1 88 f3 a2 87  f6 a2 88 f7 a3 89 fa a5  |................|
00000160  8b f9 a5 89 fa a3 88 f7  a0 85 f6 9d 82 f3 9b 7d  |...............}|
00000170  f0 98 7a ef 97 79 eb 92  70 ea 92 6e ea 90 6d ec  |..z..y..p..n..m.|
00000180  8e 6a eb 8a 66 ee 86 61  ed 82 5d ef 80 5a f0 7e  |.j..f..a..]..Z.~|
00000190  56 f0 7c 53 ef 79 4f ed  77 4d ec 77 4a ec 77 4a  |V.|S.yO.wM.wJ.wJ|
000001a0  ec 78 49 ed 79 4a ed 77  4d ed 77 4d ee 78 4e ef  |.xI.yJ.wM.wM.xN.|
000001b0  79 4f ef 7a 4d f0 7b 4e  f0 7c 4d f1 7e 4c 00 01  |yO.zM.{N.|M.~L..|
000001c0  01 7f 07 fe ff ff 02 00  00 00 42 1c 5f 03 00 00  |..........B._...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  0f 72 06 0f 96 6b 67 0a  79 ac 12 bc 84 8a ed 4f  |.r...kg.y......O|
00000010  e7 1a cb f3 7d 3c c1 73  33 64 cf 7e 95 cb 86 67  |....}<.s3d.~...g|
00000020  4d 20 f2 63 9a d0 d0 ea  39 c9 25 a4 46 0a 0c b5  |M .c....9.%.F...|
00000030  93 b7 ab 59 93 e6 a5 8d  51 48 60 00 95 06 57 70  |...Y....QH`...Wp|
00000040  84 11 bf 31 75 c2 94 25  4e 0d 3d fa 00 75 a0 16  |...1u..%N.=..u..|
00000050  e5 0c 40 62 72 7f a8 f2  d7 9d fd ce bf 8a e5 f3  |..@br...........|
00000060  f3 98 28 07 e7 0d a3 90  cf 92 6e 02 a8 63 d1 78  |..(.......n..c.x|
00000070  b7 13 af c8 e1 d8 c9 38  ec c2 9a 34 2b 0a 81 ec  |.......8...4+...|
00000080  60 90 0e 61 0a 04 5d a3  b1 35 68 03 8e 5d 98 69  |`..a..]..5h..].i|
00000090  5f 8d ae 8d 7d fb 5d c1  b2 78 d9 f7 37 df f7 76  |_...}.]..x..7..v|
000000a0  a0 44 d2 0b 84 bf 75 63  38 71 e2 d1 2b b9 2f e0  |.D....uc8q..+./.|
000000b0  a4 5b 3d ff 46 64 08 31  22 4a c4 f4 1c 79 e4 72  |.[=.Fd.1"J...y.r|
000000c0  7c 1a d5 12 4d e6 bc 35  88 0a 17 2f 5c 09 39 62  ||...M..5.../\.9b|
000000d0  95 91 d8 84 db ed 65 fe  a2 48 14 d3 29 ab e7 af  |......e..H..)...|
000000e0  99 67 6b 50 a9 8a 16 fc  e6 c6 04 cf 91 2b ce 9f  |.gkP.........+..|
000000f0  8d d0 ea 12 b1 34 f2 70  3f 7a e9 9c 74 d1 44 c2  |.....4.p?z..t.D.|
00000100  c3 9c a3 06 7b 13 6e cd  42 56 3c 44 f8 99 dc e5  |....{.n.BV<D....|
00000110  32 bc e7 db 08 7f c5 90  bf 4e 5c cb 98 e0 6a ab  |2........N\...j.|
00000120  89 3c 42 5d 7f 4b 02 df  28 d8 64 15 91 4a 58 f1  |.<B].K..(.d..JX.|
00000130  a7 ae 9c 70 e0 4e ec 8d  5a 4c 2b c5 f0 93 72 e2  |...p.N..ZL+...r.|
00000140  24 0f 27 70 72 8a 16 9c  49 20 32 73 2f 87 f1 d3  |$.'pr...I 2s/...|
00000150  4b 33 f2 59 64 c3 d5 e7  18 77 03 f5 df 89 9f 5f  |K3.Yd....w....._|
00000160  98 13 ee 04 02 a3 db 08  8d 84 72 ca 43 3c fd d0  |..........r.C<..|
00000170  d7 a9 0b e8 a6 dc fc 97  22 19 05 78 52 70 4f 21  |........"..xRpO!|
00000180  02 6d 5b a6 84 49 c0 10  4c 27 76 6d 6e ce c4 9c  |.m[..I..L'vmn...|
00000190  d3 fa 45 29 a6 04 5d 39  1f 31 b1 c1 11 7d 5c 3d  |..E)..]9.1...}\=|
000001a0  4f 6e 45 53 08 07 c7 e6  ed 3f 83 5a 04 b0 7b a8  |OnES.....?.Z..{.|
000001b0  4a ec 0f 95 67 ef 21 34  09 60 dc bd 68 75 00 fe  |J...g.!4.`..hu..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 c8 c9 03 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 c8  c9 03 00 70 4a 00 00 00  |...........pJ...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2011-05-03
You somehow installed XP to sda5 which is a logical partition. Windows will only boot from a primary partition.

Did you have another copy of windows in sda1 and when you deleted it, it deleted the windows boot files? Your install in sda5 has no boot files.

You also created a Linux /boot in sda1 but your install is in sdb1. Is this an old system where the BIOS will only boot from the first 137GB of a drive. That is about the only reason for a standard desktop to have a separate /boot. Plus I prefer to have all the system files on one drive, so if a drive fails I can boot the other. With your configuration, if either drive fails, you cannot boot except from a LiveCD.

---

### Post by nathan soulfly on 2011-05-03
> **oldfred said:**
> You somehow installed XP to sda5 which is a logical partition. Windows will only boot from a primary partition.

Did you have another copy of windows in sda1 and when you deleted it, it deleted the windows boot files? Your install in sda5 has no boot files.

You also created a Linux /boot in sda1 but your install is in sdb1. Is this an old system where the BIOS will only boot from the first 137GB of a drive. That is about the only reason for a standard desktop to have a separate /boot. Plus I prefer to have all the system files on one drive, so if a drive fails I can boot the other. With your configuration, if either drive fails, you cannot boot except from a LiveCD.




about a week from today im gona upgrate my pc with ram now its 1g ram i ll make it 3 and biger hdds .so i m thinking to install win 7 and ubuntu , in separate hdd again.little help there?



thank you very much for your time.

---

### Post by oldfred on 2011-05-03
Be sure to install win7 in a primary partition or let it install to an empty drive. It will normally create a small (hidden in windows) system/boot/recovery partition of 100MB and the main system partition. You may want to create a d: drive for data as it is best to only read from the windows system partition and use a shared NTFS partition as the read/write partition.

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

---

### Post by nathan soulfly on 2011-05-04
thanks that was very helpful

---

