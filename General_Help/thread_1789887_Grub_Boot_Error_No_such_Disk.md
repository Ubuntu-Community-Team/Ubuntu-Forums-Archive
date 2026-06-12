---
title: "Grub Boot Error: No such Disk"
date: 2011-06-24
forum: General Help
---

### Post by metallikz on 2011-06-24
Hi all, apologies for my first post being one asking for help but....

I was running ubuntu server 10.04lts on a home server for backups and media etc which somehow broke. I had installed ubuntu on a different partition (with LVM) to my data just in case something like this happened. 

I reinstalled the os to that partition in the hope that I would be left with a working system and could retain my data. 

Now, here things get a little complicated but are probably relevant! I extended the data partition over another drive which I added after I originally set it all up and used the sata power adaptor from the dvd drive to power the new hdd. Its an old computer so doesnt support booting from usb and only has two sata power connectors. 

My thinking was that if I unplugged the second hard drive which contained the os partition and part of the data partition I should be able to install the new os without problem which I did (I think!). The partition manager from the install cd couldnt read or recognise the data partition since part of it was not plugged in but could see the os partition which I installed to.

Now after formatting and installing onto that partition I get the grub boot error of No such disk and am left with the grub rescue command prompt. I have tried booting with and without the second hard drive plugged in, just in case it made a difference. 

Reading around the forums here I found the boot info script which is below. (I used a live cd of the desktop version to run it)

If anyone could help I would really appreciate it, this must be a software problem but losing the data would be a massive pain!

Thanks in advance.

>                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (mediaserver-root)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       499,711       497,664  83 Linux
/dev/sda2             501,758   625,141,759   624,640,002   5 Extended
/dev/sda5             501,760   625,141,759   624,640,000  8e Linux LVM


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 260 MB, 260355072 bytes
255 heads, 63 sectors/track, 31 cylinders, total 508506 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63       508,472       508,410   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        b5fe8c06-6beb-4d2d-861e-51c9d74d38c3   ext2       
/dev/sda5        Aoen99-Svlz-Unxy-wVae-VHyx-FuQh-MLiRgE LVM2_member 
/dev/sdb1        F085-C5E1                              vfat       UNTITLED

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/UNTITLED          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


============================= sda1/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
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
insmod lvm
insmod ext2
set root='(mediaserver-root)'
search --no-floppy --fs-uuid --set 116a95f4-7b28-467a-a705-1d82941b738d
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
search --no-floppy --fs-uuid --set b5fe8c06-6beb-4d2d-861e-51c9d74d38c3
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-28-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b5fe8c06-6beb-4d2d-861e-51c9d74d38c3
	linux	/vmlinuz-2.6.32-28-server root=/dev/mapper/mediaserver-root ro   quiet
	initrd	/initrd.img-2.6.32-28-server
}
menuentry 'Ubuntu, with Linux 2.6.32-28-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b5fe8c06-6beb-4d2d-861e-51c9d74d38c3
	echo	'Loading Linux 2.6.32-28-server ...'
	linux	/vmlinuz-2.6.32-28-server root=/dev/mapper/mediaserver-root ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-28-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b5fe8c06-6beb-4d2d-861e-51c9d74d38c3
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b5fe8c06-6beb-4d2d-861e-51c9d74d38c3
	linux16	/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.119218826 = 0.128010240    grub/core.img                                  2
   0.122201920 = 0.131213312    grub/grub.cfg                                  1
   0.028848648 = 0.030976000    initrd.img-2.6.32-28-server                   37
   0.010981560 = 0.011791360    vmlinuz-2.6.32-28-server                      18

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  de 28 c1 36 49 1a 79 eb  c8 91 6a ea 23 22 d4 52  |.(.6I.y...j.#".R|
00000010  7f 24 00 cb 21 5d 92 5d  18 c5 22 ee d9 0e ff 9d  |.$..!].]..".....|
00000020  a0 80 58 9e 24 f9 bf a8  0e 68 69 34 3f 80 3c 33  |..X.$....hi4?.<3|
00000030  7c 32 e1 f9 09 f9 f9 89  da f8 81 01 75 c4 13 6b  ||2..........u..k|
00000040  32 bb e5 b0 46 78 b0 3e  77 da 13 1c 36 a1 94 c0  |2...Fx.>w...6...|
00000050  29 43 43 33 3c c1 ff 8d  64 0f 07 7f 04 3c 49 eb  |)CC3<...d....<I.|
00000060  06 3c 67 bb e7 0d cc fb  3c 74 75 d0 3b 04 4b 0f  |.<g.....<tu.;.K.|
00000070  09 0e 03 78 96 c0 03 b8  3f a9 54 32 26 20 42 aa  |...x....?.T2& B.|
00000080  b0 06 1a 3f 13 23 18 9c  ff 2f 28 a0 0d 3e 34 53  |...?.#.../(..>4S|
00000090  19 23 19 b1 8c 54 27 ed  e5 7d 6b c0 48 eb 00 25  |.#...T'..}k.H..%|
000000a0  06 43 fa 4f 32 de 48 69  ef 43 0f 72 6f 6c 2d 43  |.C.O2.Hi.C.rol-C|
000000b0  0a 5b 44 82 9a 7f 06 62  65 bd 5e 38 6c a1 2c 06  |.[D....be.^8l.,.|
000000c0  dc e9 1d 67 ea 84 92 01  8c 91 8b 48 7e 0e 0c fc  |...g.......H~...|
000000d0  21 e9 29 83 f9 b3 fa 8d  c0 d6 4d 3b e9 a1 fe 30  |!.).......M;...0|
000000e0  d7 eb 06 55 70 20 cb a6  69 16 85 b0 f0 d6 98 00  |...Up ..i.......|
000000f0  62 68 bd 06 10 59 a7 9b  b8 5c df 9a 57 98 e8 98  |bh...Y...\..W...|
00000100  fb 22 19 67 e9 ff 70 ec  e8 dc 5e ff 35 1c ba 60  |.".g..p...^.5..`|
00000110  1e a9 a1 d9 2d 6a 1a 6f  43 1f 30 da 12 e3 b6 60  |....-j.oC.0....`|
00000120  c1 eb d7 8d 42 51 51 78  68 58 d6 cf 0e df 21 eb  |....BQQxhX....!.|
00000130  5a eb bc 29 2c 28 5c e4  9d f6 21 5f eb a7 5f 56  |Z..),(\...!_.._V|
00000140  56 34 5f c6 9e 80 3e 5b  eb 8c 28 1f 86 bc 9d 24  |V4_...>[..(....$|
00000150  84 d7 0d 24 64 41 45 59  f9 af 00 75 2f 2a 4e e7  |...$dAEY...u/*N.|
00000160  fa 0f 81 7f 42 78 04 39  fa 74 07 66 39 3a 01 c0  |....Bx.9.t.f9:..|
00000170  da 75 ef 40 2d 28 98 40  37 c4 a3 76 40 58 85 70  |.u.@-(.@7..v@X.p|
00000180  0c 6a 17 09 f0 b5 80 07  e2 57 ff 10 a0 e5 5b e6  |.j.......W....[.|
00000190  c4 a2 3a b3 ab 68 98 07  ed 37 dc 0c 23 6a 01 2b  |..:..h...7..#j.+|
000001a0  01 eb 1c 5b 43 80 9c 1a  87 7f bf d7 1d f0 26 57  |...[C.........&W|
000001b0  83 ff d9 78 13 02 11 ec  bb b4 f4 52 bd 58 5a 7c  |...x.......R.XZ||
000001c0  fa 43 18 f7 85 8a a1 12  38 ad aa 23 88 7c 62 57  |.C......8..#.|bW|
000001d0  7b 04 99 e4 12 84 88 93  17 26 81 35 ce 7c 2c 1a  |{........&.5.|,.|
000001e0  a2 04 2b 1f 47 24 63 d1  d9 82 28 2d 5f 01 fe e1  |..+.G$c...(-_...|
000001f0  17 f2 8b 30 74 1a 8b 50  25 da 74 13 39 5a a9 18  |...0t..P%.t.9Z..|
00000200

Unknown BootLoader on sda2

00000000  66 79 7e fd 03 c3 cd 00  f9 34 56 b8 d5 2d 64 a4  |fy~......4V..-d.|
00000010  f6 51 13 26 ef 4d ba d9  81 bb 8b 3e b0 42 0f 9a  |.Q.&.M.....>.B..|
00000020  af d7 94 50 63 d8 f1 ca  51 0d 6b 7a 4a a8 af 61  |...Pc...Q.kzJ..a|
00000030  52 0e 84 51 50 fd 2c a8  b8 75 fb 5e 2c c1 73 cb  |R..QP.,..u.^,.s.|
00000040  bc cd 31 01 cd 9b 3b a0  01 9f 1b 0d 06 51 a5 32  |..1...;......Q.2|
00000050  da 01 6a 4c 01 77 1d e0  0c d8 a3 8a c7 a2 5a 97  |..jL.w........Z.|
00000060  45 47 5f 83 34 0b 52 54  67 91 cd b5 ea 22 40 58  |EG_.4.RTg...."@X|
00000070  ec a0 45 c7 0a da b4 8f  ef 53 68 b3 e6 8b 1c ce  |..E......Sh.....|
00000080  5e e8 f0 0e db 13 7c 01  82 25 1a fb 1a 5c d1 22  |^.....|..%...\."|
00000090  cd 8f 55 65 d7 96 28 8b  0b 47 55 b8 61 af d7 1a  |..Ue..(..GU.a...|
000000a0  47 f4 a4 bc e4 41 da 3d  d8 01 7c 60 ae 25 52 d3  |G....A.=..|`.%R.|
000000b0  8e da 44 d3 6f 83 8f 14  b9 26 09 78 90 00 c1 6d  |..D.o....&.x...m|
000000c0  c0 2f 95 82 ab 43 0b df  ed 91 18 1a 9e 9a aa 36  |./...C.........6|
000000d0  39 ca 1f 9e 02 2e 1d 95  d7 c7 85 60 f6 37 6d f7  |9..........`.7m.|
000000e0  7f de 0a 37 f0 3d 7c 52  be 78 87 0c f5 1a 7b 25  |...7.=|R.x....{%|
000000f0  2e c6 a8 21 2b 0e 7a d2  74 86 c5 17 36 7e 81 42  |...!+.z.t...6~.B|
00000100  6b 44 19 4a 59 4d 8d 73  0c 11 5a 34 f5 39 20 b4  |kD.JYM.s..Z4.9 .|
00000110  e6 6a 17 15 ab a3 35 6b  7b 9e 33 59 6b 18 55 71  |.j....5k{.3Yk.Uq|
00000120  f4 7a 07 4a 26 1b 6c f9  9d 6c 00 f9 bd 76 a5 98  |.z.J&.l..l...v..|
00000130  3e 77 82 31 42 4e b9 91  2b 26 6b cf b7 24 33 83  |>w.1BN..+&k..$3.|
00000140  2a 6d 56 c1 50 de de c8  a4 e5 95 76 00 96 d7 3a  |*mV.P......v...:|
00000150  34 4a 9b c3 d0 0e f6 72  cf 49 c3 35 a9 de e0 b7  |4J.....r.I.5....|
00000160  52 17 4a 18 89 6a 1e bf  e6 c4 17 85 79 e9 60 06  |R.J..j......y.`.|
00000170  8d f9 73 11 a0 3a 6f ff  86 0f 78 c5 b9 c6 bc de  |..s..:o...x.....|
00000180  23 d4 b3 bd c0 a4 08 9c  77 2f fe 91 ed e5 28 ab  |#.......w/....(.|
00000190  a3 d2 09 c0 f0 c1 fa ad  a2 40 15 4b a6 da bf 59  |.........@.K...Y|
000001a0  4a 22 20 ab 53 8a 70 80  6f 80 cb c5 e5 32 54 6a  |J" .S.p.o....2Tj|
000001b0  b7 73 ba 0d ea f8 c6 ac  7e 47 4b 18 14 36 00 3b  |.s......~GK..6.;|
000001c0  1d 1f 8e fe ff ff 02 00  00 00 00 40 3b 25 00 00  |...........@;%..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200





---

### Post by dino99 on 2011-06-24
as you can see at the beginning:

 grub installed on sda,
 but then it try to boot on sdb, 

so it fail of course, edit the boot line to give the good path. when booted run: sudo grub-mkconfig && sudo update-grub

---

### Post by metallikz on 2011-06-25
Thanks for your reply! 

Im a little stuck, im trying to do the rescue mode booting method described here: [https://help.ubuntu.com/community/Grub2#Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Rescue%20Mode)

In grub rescue> 
ls gives me: (hd0)(hd1)(fd0)
so it doesnt recognise any of the partitions on the drive like I was expecting

as a long shot
>set prefix=(hd0,1)/boot/grub)
>set root=(hd0,1)
insmod normal 
error: no such partition


Apologies if im overlooking something very obvious!
Thanks.

---

