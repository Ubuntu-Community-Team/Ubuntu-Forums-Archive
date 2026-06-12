---
title: "Missing operating system on boot"
date: 2011-06-11
forum: General Help
---

### Post by MTO on 2011-06-11
Hello,
today I turned on my laptop to find the following error on boot: "missing operating system".
Grub appears to not be loading at all.

No usb drives connected, I had made no system changes last time I used it, nothing I can imagine it might have something to do with it.

---

I took out the drive, and connected it to another computer I have, though a USB I have for it. Something must be wrong with the drive itself as it does not mount any drives (windows and ubuntu partitions).

I opened the ubuntu disk utility, and this is what I see:
[IMG]http://i.imgur.com/oDEfm.png[/IMG]

I cant think of anything that may have caused this, or how to fix it, I especially need to recover drive access, even if it's only enough to recover and copy some files from it.

---

### Post by MTO on 2011-06-11
Any suggestions as to what I should do?
Thanks.

---

### Post by linuxinstalledfromhdd on 2011-06-11
Let's hang in there for a while, when the grub experts can take a look at this... 

BUMP

---

### Post by wildmanne39 on 2011-06-11
> **MTO said:**
> Hello,
today I turned on my laptop to find the following error on boot: "missing operating system".
Grub appears to not be loading at all.

No usb drives connected, I had made no system changes last time I used it, nothing I can imagine it might have something to do with it.

---

I took out the drive, and connected it to another computer I have, though a USB I have for it. Something must be wrong with the drive itself as it does not mount any drives (windows and ubuntu partitions).

I opened the ubuntu disk utility, and this is what I see:


I cant think of anything that may have caused this, or how to fix it, I especially need to recover drive access, even if it's only enough to recover and copy some files from it.
Hi, post the information from this script so we can see what is where: Boot from the livecd or usb to run this boot script.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by MTO on 2011-06-11
Thanks, here are the results I have:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>.........X....0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 2725056 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         96,390   272,309,418   272,213,029   7 NTFS / exFAT / HPFS
/dev/sda3         272,310,270   488,392,064   216,081,795   f W95 Extended (LBA)
Invalid MBR Signature found.
/dev/sda5     ?   666,043,332 1,734,280,188 1,068,236,857  15 Unknown
/dev/sda6     ? 3,126,378,426 6,513,989,954 3,387,611,529  2b SyllableSecure

/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda3
/dev/sda6 ends after the last sector of /dev/sda
the logical partition /dev/sda6 is not contained in the extended partition /dev/sda3

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 3957 MB, 3957325824 bytes
61 heads, 60 sectors/track, 2111 cylinders, total 7729152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,192     7,729,151     7,720,960   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       4900ebb3-d14a-42c7-8754-f10de4dbdd5a   ext3       
/dev/sdb1        35E1-819E                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/loop1       /media/4900ebb3-d14a-42c7-8754-f10de4dbdd5a ext3       (rw,nosuid,nodev,uhelper=udisks,commit=600)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  3b 9e cc d2 34 44 22 f9  e9 de e1 32 71 c8 79 11  |;...4D"....2q.y.|
00000010  a3 e3 b9 9c 32 5b 70 75  e9 8d f6 cc 30 33 d5 8f  |....2[pu....03..|
00000020  60 2e ae a8 28 bf 0d 82  20 15 3d 3a 5e 14 db c5  |`...(... .=:^...|
00000030  4e 47 6f b0 ea c5 70 c0  27 3d 0a a2 6f 1f 9f af  |NGo...p.'=..o...|
00000040  aa 45 f1 30 24 9e 0f 7d  f8 72 dc c2 cb 29 c4 21  |.E.0$..}.r...).!|
00000050  07 87 fd 68 78 5c b6 f3  38 19 b3 ed d1 76 57 23  |...hx\..8....vW#|
00000060  89 08 27 3e dd 73 42 ef  f1 16 0f 54 63 69 d7 ad  |..'>.sB....Tci..|
00000070  3f aa 26 77 c0 d1 96 ba  b6 eb b7 39 97 44 91 d9  |?.&w.......9.D..|
00000080  f8 7f 21 d7 3f a0 f7 a6  a0 d4 0a 9a 74 fa 19 b0  |..!.?.......t...|
00000090  81 79 83 d7 9c 5d 68 35  c4 06 73 76 a6 d0 97 7b  |.y...]h5..sv...{|
000000a0  e6 b1 f6 c6 b9 aa cc cb  19 c9 a1 d5 32 29 66 c1  |............2)f.|
000000b0  ab fd 7f 6d 89 7e b8 a5  e3 5b 15 e8 f6 af ac bb  |...m.~...[......|
000000c0  ed 96 dc 72 dd 0d 96 2b  8c a4 0b 19 4c 1a e2 6b  |...r...+....L..k|
000000d0  94 c7 4c 7b b9 1d 92 34  f2 64 29 67 4c b9 07 18  |..L{...4.d)gL...|
000000e0  8d 1f 6a 7c 76 ae 53 bf  c7 45 6e 09 33 a9 fe c8  |..j|v.S..En.3...|
000000f0  66 79 b0 82 b3 f9 84 42  3e 6c 49 e3 ff 24 88 1a  |fy.....B>lI..$..|
00000100  a6 4d a8 0f 9b 75 6f 81  50 50 9f 7a 40 f9 38 34  |.M...uo.PP.z@.84|
00000110  a7 9d 8f e6 d5 29 8a a7  ff 77 fa 63 30 a6 3b 6e  |.....)...w.c0.;n|
00000120  a3 b5 36 db a9 0b ba 3c  48 14 bb b2 c3 ad f1 10  |..6....<H.......|
00000130  2e 33 30 ae f9 dc a4 68  dc 8f c9 b5 65 f0 6f 34  |.30....h....e.o4|
00000140  75 f9 44 57 f1 3c 1c 65  d3 dc 44 fa 01 77 cf d1  |u.DW.<.e..D..w..|
00000150  21 6f ba 86 0a e1 b8 a0  c8 48 2c bc b7 64 fe 56  |!o.......H,..d.V|
00000160  1c 43 fc e8 76 9b 52 16  c0 1d ff 48 15 94 a0 14  |.C..v.R....H....|
00000170  72 d5 b0 25 df 4c 1f e0  cb 5b c1 02 97 49 79 12  |r..%.L...[...Iy.|
00000180  57 c7 85 9e 29 4f 18 bd  c5 a0 48 8e db 5d 1a 8e  |W...)O....H..]..|
00000190  53 2a d8 67 8e 63 4f bc  b0 c1 cc 8e 15 04 2a 55  |S*.g.cO.......*U|
000001a0  b5 9f 8b f7 a8 08 9f 6a  7e 14 9c 88 f0 88 60 12  |.......j~.....`.|
000001b0  12 dd 03 67 b8 a5 37 c6  95 38 c4 9c 8e dc 6f 0e  |...g..7..8....o.|
000001c0  da 5b 95 69 77 0a e8 41  47 5c be 95 72 01 45 35  |.[.iw..AG\..r.E5|
000001d0  69 e4 75 fc 60 94 d7 fd  09 0d 65 49 72 9d 6d 24  |i.u.`.....eIr.m$|
000001e0  3e 9e f5 ae 49 59 7f f4  70 06 63 16 b6 fd 36 b0  |>...IY..p.c...6.|
000001f0  c5 d6 eb ee 34 1e 70 89  06 12 9b aa e7 30 0a 06  |....4.p......0..|
00000200

Unknown BootLoader on sda2

00000000  00 8b f8 85 ff 75 08 56  e8 2c d9 01 00 8b f8 ff  |.....u.V.,......|
00000010  75 08 e8 3e ff ff ff 8b  c7 5f 5e c9 c2 04 00 8b  |u..>....._^.....|
00000020  ff 55 8b ec 83 ec 38 a1  20 af 46 00 33 c5 89 45  |.U....8. .F.3..E|
00000030  fc 8b 45 08 89 45 cc 8b  45 0c 53 89 45 d0 56 57  |..E..E..E.S.E.VW|
00000040  33 db 33 c0 88 5d e8 8d  7d e9 ab ab ab ab 66 ab  |3.3..]..}.....f.|
00000050  aa 8d 45 d8 50 8b f1 6a  09 89 75 c8 89 5d d8 89  |..E.P..j..u..]..|
00000060  5d d4 89 5d e0 c6 45 e7  01 e8 e8 ae 01 00 89 45  |]..]..E........E|
00000070  dc 3b c3 0f 85 b7 00 00  00 8b 45 d8 33 c9 3b c3  |.;........E.3.;.|
00000080  75 07 b9 04 01 29 80 eb  17 8d 75 e7 8d 78 08 c7  |u....)....u..x..|
00000090  00 02 00 00 04 c7 40 04  01 00 00 00 a4 8b 75 c8  |......@.......u.|
000000a0  89 4d dc 3b cb 0f 85 85  00 00 00 53 8d 45 d4 50  |.M.;.......S.E.P|
000000b0  ff 75 d8 33 d2 6a 06 6a  09 59 e8 1b 08 00 00 89  |.u.3.j.j.Y......|
000000c0  45 dc 3d 06 01 29 80 74  0d 3b c3 75 63 c7 45 dc  |E.=..).t.;.uc.E.|
000000d0  05 40 00 80 eb 5a 8d 45  e0 50 ff 75 d4 e8 74 ae  |.@...Z.E.P.u..t.|
000000e0  01 00 89 45 dc 3b c3 75  47 8b 55 e0 8d 45 e8 50  |...E.;.uG.U..E.P|
000000f0  8d 45 d4 50 ff 75 d8 6a  06 6a 09 59 e8 d9 07 00  |.E.P.u.j.j.Y....|
00000100  00 89 45 dc 3b c3 75 28  3b f3 74 14 8b 45 cc 3b  |..E.;.u(;.t..E.;|
00000110  c3 74 0d 8b 4d d4 89 0e  8b 4d e0 89 08 89 5d e0  |.t..M....M....].|
00000120  39 5d d0 74 0b 8b 7d d0  6a 05 59 8d 75 e8 f3 a5  |9].t..}.j.Y.u...|
00000130  39 5d d8 74 08 ff 75 d8  e8 33 ae 01 00 39 5d e0  |9].t..u..3...9].|
00000140  5f 5e 5b 74 08 ff 75 e0  e8 23 ae 01 00 8b 4d fc  |_^[t..u..#....M.|
00000150  8b 45 dc 33 cd e8 7c 71  fd ff c9 c2 08 00 8b ff  |.E.3..|q........|
00000160  55 8b ec 83 ec 1c a1 20  af 46 00 33 c5 89 45 fc  |U...... .F.3..E.|
00000170  57 33 c0 c6 45 e8 00 8d  7d e9 ab ab ab ab 66 ab  |W3..E...}.....f.|
00000180  aa 8d 45 e8 50 8d 45 e4  50 33 c9 e8 8f fe ff ff  |..E.P.E.P3......|
00000190  5f 85 c0 75 0b 8d 45 e8  50 6a 0c e8 ea ad 01 00  |_..u..E.Pj......|
000001a0  8b 4d fc 33 cd e8 2c 71  fd ff c9 c3 8b ff 55 8b  |.M.3..,q......U.|
000001b0  ec 51 51 83 65 f8 00 83  65 fc 00 56 6a 00 8d 45  |.QQ.e...e..Vj..E|
000001c0  fc 50 8d 4d f8 e8 55 fe  ff ff 8b f0 85 f6 75 12  |.P.M..U.......u.|
000001d0  ff 75 fc 8b 75 f8 b8 9c  d3 48 00 e8 91 04 00 00  |.u..u....H......|
000001e0  8b f0 83 7d fc 00 74 08  ff 75 fc e8 80 ad 01 00  |...}..t..u......|
000001f0  8b c6 5e c9 c3 33 c0 85  c9 75 06 b8 04 01 29 80  |..^..3...u....).|
00000200

Unknown BootLoader on sda3

00000000  a0 78 e8 01 f3 4a 08 28  8f db 54 c5 75 5b 37 71  |.x...J.(..T.u[7q|
00000010  82 51 48 14 d2 ad f7 04  7f 81 6d fa d5 83 97 67  |.QH.......m....g|
00000020  b9 9a ca 96 2a 47 17 17  c9 f9 fe 5c 55 39 07 b4  |....*G.....\U9..|
00000030  0e 8f 23 55 23 43 18 25  e7 8b d3 67 94 20 28 d3  |..#U#C.%...g. (.|
00000040  d6 2a f7 3b 6b 14 a0 87  3f 7b 92 0e 17 20 02 96  |.*.;k...?{... ..|
00000050  bd 77 69 5f 4e 4e bb ff  9b 21 ff a6 3e b4 1a a7  |.wi_NN...!..>...|
00000060  b9 c6 a1 13 39 b1 a9 7f  aa db d3 f8 18 bd e1 43  |....9..........C|
00000070  19 2b 5a 01 96 97 31 a6  80 25 e6 fb ef 3b a7 f7  |.+Z...1..%...;..|
00000080  b7 69 d2 7a 7a 77 82 ae  be 4e 01 0f 18 ac 7b 54  |.i.zzw...N....{T|
00000090  2a 51 e0 60 36 24 82 88  b8 0b 4a 06 c7 e0 4a 1a  |*Q.`6$....J...J.|
000000a0  cc 64 75 32 fe d5 a3 bc  aa 6d a2 4a be 52 f8 07  |.du2.....m.J.R..|
000000b0  84 af 02 98 7d 01 2c 72  30 0a 7f 15 0e a1 70 1a  |....}.,r0.....p.|
000000c0  2e 8a 3c 9f 04 7f a5 b4  d8 90 01 e0 1e 25 02 00  |..<..........%..|
000000d0  95 f0 86 24 fd 41 72 a6  4a 12 bd 65 9a 70 40 08  |...$.Ar.J..e.p@.|
000000e0  20 de 80 c1 04 7c 0f 03  00 db 40 7f ea b2 ad 67  | ....|....@....g|
000000f0  e0 c9 2d 6b 46 4c a0 e1  30 14 ed 18 64 f3 e5 f0  |..-kFL..0...d...|
00000100  7e 01 c1 08 49 f4 fc 1f  2b ee ff ca 1b 6b 86 d4  |~...I...+....k..|
00000110  31 6e aa e3 6d 64 58 23  2f 57 b1 4f a8 33 1e 57  |1n..mdX#/W.O.3.W|
00000120  f8 bf 38 3a 5e 8d 7d 01  e0 e0 0f 8a 8b e7 fe 5c  |..8:^.}........\|
00000130  a3 89 d7 dc 2d 84 f6 35  54 6e 68 e9 1b e4 67 44  |....-..5Tnh...gD|
00000140  e1 4d f6 f7 79 c5 e7 31  36 99 2e 03 ea 87 ba 23  |.M..y..16......#|
00000150  68 8f f5 51 96 12 e4 e1  ed c5 0d 0e b1 66 89 bd  |h..Q.........f..|
00000160  3b 9c 03 54 46 f5 06 2b  8b a7 30 3a e7 67 03 b8  |;..TF..+..0:.g..|
00000170  26 69 22 33 c0 53 fa fd  92 45 e1 62 65 91 32 4e  |&i"3.S...E.be.2N|
00000180  a6 7b d2 77 6e c4 ec a7  e9 dc 57 fe f1 52 8d ef  |.{.wn.....W..R..|
00000190  bf 35 84 9a 5a 76 55 10  44 ff 6b 70 77 00 9d 60  |.5..ZvU.D.kpw..`|
000001a0  9b b8 dd d5 a6 80 46 da  cc c9 39 2b 68 4f 05 3e  |......F...9+hO.>|
000001b0  b3 a2 30 ea a5 d3 df 53  ce f4 44 0f cb 6d 31 f5  |..0....S..D..m1.|
000001c0  de 5f 15 64 53 fa c6 e3  77 17 39 00 ac 3f 8b 9e  |._.dS...w.9..?..|
000001d0  02 8d 2b d2 ac dc bc 9f  1d aa 89 d9 ea c9 88 b5  |..+.............|
000001e0  aa a9 4e c1 df ff fc 51  40 e8 18 59 82 65 1d 92  |..N....Q@..Y.e..|
000001f0  56 c7 79 57 9a dd 4e 4f  53 b6 b2 e0 8a 76 0c 14  |V.yW..NOS....v..|
00000200

Unknown BootLoader on sda5


Unknown BootLoader on sda6



========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by wildmanne39 on 2011-06-11
> **MTO said:**
> Thanks, here are the results I have:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>.........X....0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 2725056 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         96,390   272,309,418   272,213,029   7 NTFS / exFAT / HPFS
/dev/sda3         272,310,270   488,392,064   216,081,795   f W95 Extended (LBA)
Invalid MBR Signature found.
/dev/sda5     ?   666,043,332 1,734,280,188 1,068,236,857  15 Unknown
/dev/sda6     ? 3,126,378,426 6,513,989,954 3,387,611,529  2b SyllableSecure

/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda3
/dev/sda6 ends after the last sector of /dev/sda
the logical partition /dev/sda6 is not contained in the extended partition /dev/sda3

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 3957 MB, 3957325824 bytes
61 heads, 60 sectors/track, 2111 cylinders, total 7729152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,192     7,729,151     7,720,960   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       4900ebb3-d14a-42c7-8754-f10de4dbdd5a   ext3       
/dev/sdb1        35E1-819E                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/loop1       /media/4900ebb3-d14a-42c7-8754-f10de4dbdd5a ext3       (rw,nosuid,nodev,uhelper=udisks,commit=600)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  3b 9e cc d2 34 44 22 f9  e9 de e1 32 71 c8 79 11  |;...4D"....2q.y.|
00000010  a3 e3 b9 9c 32 5b 70 75  e9 8d f6 cc 30 33 d5 8f  |....2[pu....03..|
00000020  60 2e ae a8 28 bf 0d 82  20 15 3d 3a 5e 14 db c5  |`...(... .=:^...|
00000030  4e 47 6f b0 ea c5 70 c0  27 3d 0a a2 6f 1f 9f af  |NGo...p.'=..o...|
00000040  aa 45 f1 30 24 9e 0f 7d  f8 72 dc c2 cb 29 c4 21  |.E.0$..}.r...).!|
00000050  07 87 fd 68 78 5c b6 f3  38 19 b3 ed d1 76 57 23  |...hx\..8....vW#|
00000060  89 08 27 3e dd 73 42 ef  f1 16 0f 54 63 69 d7 ad  |..'>.sB....Tci..|
00000070  3f aa 26 77 c0 d1 96 ba  b6 eb b7 39 97 44 91 d9  |?.&w.......9.D..|
00000080  f8 7f 21 d7 3f a0 f7 a6  a0 d4 0a 9a 74 fa 19 b0  |..!.?.......t...|
00000090  81 79 83 d7 9c 5d 68 35  c4 06 73 76 a6 d0 97 7b  |.y...]h5..sv...{|
000000a0  e6 b1 f6 c6 b9 aa cc cb  19 c9 a1 d5 32 29 66 c1  |............2)f.|
000000b0  ab fd 7f 6d 89 7e b8 a5  e3 5b 15 e8 f6 af ac bb  |...m.~...[......|
000000c0  ed 96 dc 72 dd 0d 96 2b  8c a4 0b 19 4c 1a e2 6b  |...r...+....L..k|
000000d0  94 c7 4c 7b b9 1d 92 34  f2 64 29 67 4c b9 07 18  |..L{...4.d)gL...|
000000e0  8d 1f 6a 7c 76 ae 53 bf  c7 45 6e 09 33 a9 fe c8  |..j|v.S..En.3...|
000000f0  66 79 b0 82 b3 f9 84 42  3e 6c 49 e3 ff 24 88 1a  |fy.....B>lI..$..|
00000100  a6 4d a8 0f 9b 75 6f 81  50 50 9f 7a 40 f9 38 34  |.M...uo.PP.z@.84|
00000110  a7 9d 8f e6 d5 29 8a a7  ff 77 fa 63 30 a6 3b 6e  |.....)...w.c0.;n|
00000120  a3 b5 36 db a9 0b ba 3c  48 14 bb b2 c3 ad f1 10  |..6....<H.......|
00000130  2e 33 30 ae f9 dc a4 68  dc 8f c9 b5 65 f0 6f 34  |.30....h....e.o4|
00000140  75 f9 44 57 f1 3c 1c 65  d3 dc 44 fa 01 77 cf d1  |u.DW.<.e..D..w..|
00000150  21 6f ba 86 0a e1 b8 a0  c8 48 2c bc b7 64 fe 56  |!o.......H,..d.V|
00000160  1c 43 fc e8 76 9b 52 16  c0 1d ff 48 15 94 a0 14  |.C..v.R....H....|
00000170  72 d5 b0 25 df 4c 1f e0  cb 5b c1 02 97 49 79 12  |r..%.L...[...Iy.|
00000180  57 c7 85 9e 29 4f 18 bd  c5 a0 48 8e db 5d 1a 8e  |W...)O....H..]..|
00000190  53 2a d8 67 8e 63 4f bc  b0 c1 cc 8e 15 04 2a 55  |S*.g.cO.......*U|
000001a0  b5 9f 8b f7 a8 08 9f 6a  7e 14 9c 88 f0 88 60 12  |.......j~.....`.|
000001b0  12 dd 03 67 b8 a5 37 c6  95 38 c4 9c 8e dc 6f 0e  |...g..7..8....o.|
000001c0  da 5b 95 69 77 0a e8 41  47 5c be 95 72 01 45 35  |.[.iw..AG\..r.E5|
000001d0  69 e4 75 fc 60 94 d7 fd  09 0d 65 49 72 9d 6d 24  |i.u.`.....eIr.m$|
000001e0  3e 9e f5 ae 49 59 7f f4  70 06 63 16 b6 fd 36 b0  |>...IY..p.c...6.|
000001f0  c5 d6 eb ee 34 1e 70 89  06 12 9b aa e7 30 0a 06  |....4.p......0..|
00000200

Unknown BootLoader on sda2

00000000  00 8b f8 85 ff 75 08 56  e8 2c d9 01 00 8b f8 ff  |.....u.V.,......|
00000010  75 08 e8 3e ff ff ff 8b  c7 5f 5e c9 c2 04 00 8b  |u..>....._^.....|
00000020  ff 55 8b ec 83 ec 38 a1  20 af 46 00 33 c5 89 45  |.U....8. .F.3..E|
00000030  fc 8b 45 08 89 45 cc 8b  45 0c 53 89 45 d0 56 57  |..E..E..E.S.E.VW|
00000040  33 db 33 c0 88 5d e8 8d  7d e9 ab ab ab ab 66 ab  |3.3..]..}.....f.|
00000050  aa 8d 45 d8 50 8b f1 6a  09 89 75 c8 89 5d d8 89  |..E.P..j..u..]..|
00000060  5d d4 89 5d e0 c6 45 e7  01 e8 e8 ae 01 00 89 45  |]..]..E........E|
00000070  dc 3b c3 0f 85 b7 00 00  00 8b 45 d8 33 c9 3b c3  |.;........E.3.;.|
00000080  75 07 b9 04 01 29 80 eb  17 8d 75 e7 8d 78 08 c7  |u....)....u..x..|
00000090  00 02 00 00 04 c7 40 04  01 00 00 00 a4 8b 75 c8  |......@.......u.|
000000a0  89 4d dc 3b cb 0f 85 85  00 00 00 53 8d 45 d4 50  |.M.;.......S.E.P|
000000b0  ff 75 d8 33 d2 6a 06 6a  09 59 e8 1b 08 00 00 89  |.u.3.j.j.Y......|
000000c0  45 dc 3d 06 01 29 80 74  0d 3b c3 75 63 c7 45 dc  |E.=..).t.;.uc.E.|
000000d0  05 40 00 80 eb 5a 8d 45  e0 50 ff 75 d4 e8 74 ae  |.@...Z.E.P.u..t.|
000000e0  01 00 89 45 dc 3b c3 75  47 8b 55 e0 8d 45 e8 50  |...E.;.uG.U..E.P|
000000f0  8d 45 d4 50 ff 75 d8 6a  06 6a 09 59 e8 d9 07 00  |.E.P.u.j.j.Y....|
00000100  00 89 45 dc 3b c3 75 28  3b f3 74 14 8b 45 cc 3b  |..E.;.u(;.t..E.;|
00000110  c3 74 0d 8b 4d d4 89 0e  8b 4d e0 89 08 89 5d e0  |.t..M....M....].|
00000120  39 5d d0 74 0b 8b 7d d0  6a 05 59 8d 75 e8 f3 a5  |9].t..}.j.Y.u...|
00000130  39 5d d8 74 08 ff 75 d8  e8 33 ae 01 00 39 5d e0  |9].t..u..3...9].|
00000140  5f 5e 5b 74 08 ff 75 e0  e8 23 ae 01 00 8b 4d fc  |_^[t..u..#....M.|
00000150  8b 45 dc 33 cd e8 7c 71  fd ff c9 c2 08 00 8b ff  |.E.3..|q........|
00000160  55 8b ec 83 ec 1c a1 20  af 46 00 33 c5 89 45 fc  |U...... .F.3..E.|
00000170  57 33 c0 c6 45 e8 00 8d  7d e9 ab ab ab ab 66 ab  |W3..E...}.....f.|
00000180  aa 8d 45 e8 50 8d 45 e4  50 33 c9 e8 8f fe ff ff  |..E.P.E.P3......|
00000190  5f 85 c0 75 0b 8d 45 e8  50 6a 0c e8 ea ad 01 00  |_..u..E.Pj......|
000001a0  8b 4d fc 33 cd e8 2c 71  fd ff c9 c3 8b ff 55 8b  |.M.3..,q......U.|
000001b0  ec 51 51 83 65 f8 00 83  65 fc 00 56 6a 00 8d 45  |.QQ.e...e..Vj..E|
000001c0  fc 50 8d 4d f8 e8 55 fe  ff ff 8b f0 85 f6 75 12  |.P.M..U.......u.|
000001d0  ff 75 fc 8b 75 f8 b8 9c  d3 48 00 e8 91 04 00 00  |.u..u....H......|
000001e0  8b f0 83 7d fc 00 74 08  ff 75 fc e8 80 ad 01 00  |...}..t..u......|
000001f0  8b c6 5e c9 c3 33 c0 85  c9 75 06 b8 04 01 29 80  |..^..3...u....).|
00000200

Unknown BootLoader on sda3

00000000  a0 78 e8 01 f3 4a 08 28  8f db 54 c5 75 5b 37 71  |.x...J.(..T.u[7q|
00000010  82 51 48 14 d2 ad f7 04  7f 81 6d fa d5 83 97 67  |.QH.......m....g|
00000020  b9 9a ca 96 2a 47 17 17  c9 f9 fe 5c 55 39 07 b4  |....*G.....\U9..|
00000030  0e 8f 23 55 23 43 18 25  e7 8b d3 67 94 20 28 d3  |..#U#C.%...g. (.|
00000040  d6 2a f7 3b 6b 14 a0 87  3f 7b 92 0e 17 20 02 96  |.*.;k...?{... ..|
00000050  bd 77 69 5f 4e 4e bb ff  9b 21 ff a6 3e b4 1a a7  |.wi_NN...!..>...|
00000060  b9 c6 a1 13 39 b1 a9 7f  aa db d3 f8 18 bd e1 43  |....9..........C|
00000070  19 2b 5a 01 96 97 31 a6  80 25 e6 fb ef 3b a7 f7  |.+Z...1..%...;..|
00000080  b7 69 d2 7a 7a 77 82 ae  be 4e 01 0f 18 ac 7b 54  |.i.zzw...N....{T|
00000090  2a 51 e0 60 36 24 82 88  b8 0b 4a 06 c7 e0 4a 1a  |*Q.`6$....J...J.|
000000a0  cc 64 75 32 fe d5 a3 bc  aa 6d a2 4a be 52 f8 07  |.du2.....m.J.R..|
000000b0  84 af 02 98 7d 01 2c 72  30 0a 7f 15 0e a1 70 1a  |....}.,r0.....p.|
000000c0  2e 8a 3c 9f 04 7f a5 b4  d8 90 01 e0 1e 25 02 00  |..<..........%..|
000000d0  95 f0 86 24 fd 41 72 a6  4a 12 bd 65 9a 70 40 08  |...$.Ar.J..e.p@.|
000000e0  20 de 80 c1 04 7c 0f 03  00 db 40 7f ea b2 ad 67  | ....|....@....g|
000000f0  e0 c9 2d 6b 46 4c a0 e1  30 14 ed 18 64 f3 e5 f0  |..-kFL..0...d...|
00000100  7e 01 c1 08 49 f4 fc 1f  2b ee ff ca 1b 6b 86 d4  |~...I...+....k..|
00000110  31 6e aa e3 6d 64 58 23  2f 57 b1 4f a8 33 1e 57  |1n..mdX#/W.O.3.W|
00000120  f8 bf 38 3a 5e 8d 7d 01  e0 e0 0f 8a 8b e7 fe 5c  |..8:^.}........\|
00000130  a3 89 d7 dc 2d 84 f6 35  54 6e 68 e9 1b e4 67 44  |....-..5Tnh...gD|
00000140  e1 4d f6 f7 79 c5 e7 31  36 99 2e 03 ea 87 ba 23  |.M..y..16......#|
00000150  68 8f f5 51 96 12 e4 e1  ed c5 0d 0e b1 66 89 bd  |h..Q.........f..|
00000160  3b 9c 03 54 46 f5 06 2b  8b a7 30 3a e7 67 03 b8  |;..TF..+..0:.g..|
00000170  26 69 22 33 c0 53 fa fd  92 45 e1 62 65 91 32 4e  |&i"3.S...E.be.2N|
00000180  a6 7b d2 77 6e c4 ec a7  e9 dc 57 fe f1 52 8d ef  |.{.wn.....W..R..|
00000190  bf 35 84 9a 5a 76 55 10  44 ff 6b 70 77 00 9d 60  |.5..ZvU.D.kpw..`|
000001a0  9b b8 dd d5 a6 80 46 da  cc c9 39 2b 68 4f 05 3e  |......F...9+hO.>|
000001b0  b3 a2 30 ea a5 d3 df 53  ce f4 44 0f cb 6d 31 f5  |..0....S..D..m1.|
000001c0  de 5f 15 64 53 fa c6 e3  77 17 39 00 ac 3f 8b 9e  |._.dS...w.9..?..|
000001d0  02 8d 2b d2 ac dc bc 9f  1d aa 89 d9 ea c9 88 b5  |..+.............|
000001e0  aa a9 4e c1 df ff fc 51  40 e8 18 59 82 65 1d 92  |..N....Q@..Y.e..|
000001f0  56 c7 79 57 9a dd 4e 4f  53 b6 b2 e0 8a 76 0c 14  |V.yW..NOS....v..|
00000200

Unknown BootLoader on sda5


Unknown BootLoader on sda6



========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```
Hi, is this installed dual boot or through wubi? From the livecd unmount all drives and partitions right click on them and click check to see if they are in good shape or failed.

---

### Post by MTO on 2011-06-11
I believe it has latest grub that was upgraded and included with ubuntu 11.4 a few weeks ago (had no issues till now).
It's dual boot, (win7 & ubuntu)


As far as I can tell, no partitions are mounted, I don't have the option to mount them either.

From live CD, I see:
SMART Status: Disk has a few bad sectors

When entering "view SMART data and run self-tests", in attribute ID 5, I get:
Rellocated Sector count: WARNING 
Normalized:89
Worst:89
Threshold: 10
Value: 109 sectors

All other attributes from the test show as Good or N/A.


---
Thanks for your help!

---

### Post by MTO on 2011-06-11
In case it helps:



In Disk Utility, clicking on the partition for windows:
Shows as volume "Unknown" 139 GB
Usage -
Partition type: HPFS/NTFS (0X07)
Partition Flags: Bootable
Device: /dev/sda2
Partition label: -
Capacity: 137 GB

...........

The one for ubuntu:
Shows as volume: "Free" 111GB
Usage: - Unallocated Space
Partition Type: -
Device: /dev/sda
Capacity 111 GB
(only gives option to create partition)


-------------------

In between these two, there is another smaller volume:
"Unknown" 1.0kb (image size as you can see represents much more that what it says there)
usage: -
Partition Type: Unknown ()
Partition Flags: -
Device: /dev/sda3
Partition label: -
Capacity: 1.0kb
Options to format volume, delete partition and edit partition

---

### Post by wildmanne39 on 2011-06-11
> **MTO said:**
> I believe it has latest grub that was upgraded and included with ubuntu 11.4 a few weeks ago (had no issues till now).
It's dual boot, (win7 & ubuntu)


As far as I can tell, no partitions are mounted, I don't have the option to mount them either.

From live CD, I see:
SMART Status: Disk has a few bad sectors

When entering "view SMART data and run self-tests", in attribute ID 5, I get:
Rellocated Sector count: WARNING 
Normalized:89
Worst:89
Threshold: 10
Value: 109 sectors

All other attributes from the test show as Good or N/A.


---
Thanks for your help!
Hi, did you run the test in gparted also as my previous post asked?

---

### Post by MTO on 2011-06-11
Sorry, missed the part where you mentioned gparted.

OK; let's see, I opened Gparted:

Image is of all gray "unallocated 232.89 Gib"

Partition: unallocated
File System: unallocated
Size: 232.89 Gib

Information about unallocated:
First sector: 0
Last sector: 488397168
Total sectors: 488397169

Warning: Invalid partition table on /dev/sda -- wrong signature 140c.


---
No mount, unmount and such options.

---

### Post by wildmanne39 on 2011-06-12
> **MTO said:**
> Sorry, missed the part where you mentioned gparted.

OK; let's see, I opened Gparted:

Image is of all gray "unallocated 232.89 Gib"

Partition: unallocated
File System: unallocated
Size: 232.89 Gib

Information about unallocated:
First sector: 0
Last sector: 488397168
Total sectors: 488397169

Warning: Invalid partition table on /dev/sda -- wrong signature 140c.


---
No mount, unmount and such options.

Hi, according to that everything is gone from that partition, it looks like you need to reinstall, I would totally reformat that partition if you are going to try to use it again, then reinstall.

---

