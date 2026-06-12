---
title: "Dual boot of Ubuntu 11.04 with Windows XP leaves XP unmountable, unbootable"
date: 2011-05-02
forum: General Help
---

### Post by Zac280 on 2011-05-02
Installed 11.04 after an existing install of XP on a 500 GB drive. During Ubuntu partition, at first I got an error saying I needed to specify a root partition, then it seemed to go away without me changing anything. I wanted the first 400 GB to be XP, 4 GB swap, and the remaining root. Looking at my partitions, I think my NTFS got changed somehow. 

fdisk -l
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002e28d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48631   390624256   83  Linux
/dev/sda2           48631       60802    97759233    5  Extended
/dev/sda5           48631       60302    93749248   83  Linux
/dev/sda6           60303       60802     4008960   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    c  W95 FAT32 (LBA)

```

blkid
```
/dev/sda5: UUID="d129eb43-9af2-4526-882d-2728304b6c44" TYPE="ext4" 
/dev/sda6: UUID="caa21c2d-0685-4f4d-8763-0255417adb3c" TYPE="swap" 
/dev/sdb1: LABEL="MYLINUXLIVE" UUID="19FC-165F" TYPE="vfat"
```

I can't access my XP partition at all, and it doesn't show up in GRUB. I reverted to legacy GRUB, still doesn't list.

Some info here, but I can't do much without a UUID:
[http://ubuntuforums.org/showthread.php?t=1744029](http://ubuntuforums.org/showthread.php?t=1744029)

I was going to resort to rewriting the mbr from the XP recovery console, but I get BSoD when it goes to launch XP from the cd after everything loads. Next step will be a PE cd if nothing else works. 

I've also tried sudo ntfsfix /dev/sda1, but I guess that wouldn't work if it doesn't recognize it as NTFS. Help is appreciated, thanks in advance!

---

### Post by Hedgehog1 on 2011-05-02
Sadly, I have some bad news for you....
 
There is no XP install left on the 500 gig first disk. You now have an Ubuntu only install:
 
```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48631   390624256   83  [COLOR=red]Linux[/COLOR]
/dev/sda2           48631       60802    97759233    5  [COLOR=deepskyblue]Extended[/COLOR]
/dev/sda5           48631       60302    93749248   83  [COLOR=red]Linux[/COLOR]
/dev/sda6           60303       60802     4008960   82  [COLOR=red]Linux swap / Solaris[/COLOR]

```
 
 
Disk 2, which appeats to be a 120 gig  FAT32 data partition, seems to be OK:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    c  [COLOR=deepskyblue]W95 FAT32 (LBA[/COLOR])
```
 
It appears the reason the **'Need to specify a root partition'** message went away because it defaulted back to the **'wipe the disk and install Ubuntu'** mode.
 
**If you want me to double check this diagnoses, please do the following:**
 
Please boot off the LiveCD/LiveUSB, select 'TRY', and then:
 
[[COLOR=#444444]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")
Follow the instruction on the website and post the results here.
 
Please press the '#' button when posting and place the the script results between the two 'CODE' tags.
 
***The Hedge***
 
:KS

---

### Post by Zac280 on 2011-05-03
I was worried I may have screwed up the partitioning. I tried several things to get rid of the error, then when I did, there was no button to go back and check it. For something that important, you'd think a button to go back to that menu would be desired.

Here are my results from the script:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   781,250,559   781,248,512  83 Linux
/dev/sda2         781,252,606   976,771,071   195,518,466   5 Extended
/dev/sda5         781,252,608   968,751,103   187,498,496  83 Linux
/dev/sda6         968,753,152   976,771,071     8,017,920  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   234,436,544   234,436,482   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2: PTTYPE="dos" 
/dev/sda5        d129eb43-9af2-4526-882d-2728304b6c44   ext4                                     
/dev/sda6        caa21c2d-0685-4f4d-8763-0255417adb3c   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        19FC-165F                              vfat       MYLINUXLIVE                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d129eb43-9af2-4526-882d-2728304b6c44 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d129eb43-9af2-4526-882d-2728304b6c44

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 11.04, kernel 2.6.38-8-generic
uuid		d129eb43-9af2-4526-882d-2728304b6c44
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=d129eb43-9af2-4526-882d-2728304b6c44 ro quiet splash 
initrd		/boot/initrd.img-2.6.38-8-generic
quiet

title		Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
uuid		d129eb43-9af2-4526-882d-2728304b6c44
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=d129eb43-9af2-4526-882d-2728304b6c44 ro  single
initrd		/boot/initrd.img-2.6.38-8-generic

title		Ubuntu 11.04, memtest86+
uuid		d129eb43-9af2-4526-882d-2728304b6c44
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

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
UUID=d129eb43-9af2-4526-882d-2728304b6c44 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=caa21c2d-0685-4f4d-8763-0255417adb3c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 443.1GB: boot/grub/menu.lst
 443.1GB: boot/grub/stage2
 427.1GB: boot/initrd.img-2.6.38-8-generic
 434.5GB: boot/vmlinuz-2.6.38-8-generic
 427.1GB: initrd.img
 434.5GB: vmlinuz

=========================== sdb1/boot/grub/grub.cfg: ===========================


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

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  5b 41 cd ed d5 f2 d3 5a  ea 56 dc 05 20 29 8e d9  |[A.....Z.V.. )..|
00000010  43 3d 93 57 08 75 6a 22  9a bb ef f9 1e cb 22 90  |C=.W.uj"......".|
00000020  cf 31 ab 33 9b 94 00 61  94 43 95 cd 6a b7 7f 5a  |.1.3...a.C..j..Z|
00000030  36 bc af a3 79 23 c8 71  7d c5 37 78 41 eb d2 4a  |6...y#.q}.7xA..J|
00000040  ae 4d 16 55 81 2a 75 24  af 67 c2 d2 5f 38 28 05  |.M.U.*u$.g.._8(.|
00000050  bd e9 01 a9 bf ff 37 37  f8 ca d0 37 d6 18 d8 90  |......77...7....|
00000060  6c 26 aa 2e aa ba a7 80  41 c1 72 8e 31 7d f0 3b  |l&......A.r.1}.;|
00000070  38 e5 94 76 7d 93 40 ff  61 d0 50 5d 9c 2a 45 f2  |8..v}.@.a.P].*E.|
00000080  de 1e 4f 3e 29 a1 ec ef  73 94 88 bf 3c 63 7e a1  |..O>)...s...<c~.|
00000090  97 c7 b0 3b 2a bd a5 01  a2 58 58 bd ae 53 1d 2c  |...;*....XX..S.,|
000000a0  16 c3 c2 f4 4d e7 5d cb  16 6e 13 1e 04 75 43 84  |....M.]..n...uC.|
000000b0  4a 36 6b 5d 69 51 97 dc  b4 d1 52 d8 53 00 d6 a4  |J6k]iQ....R.S...|
000000c0  53 73 8a 31 c9 d1 63 73  66 3a f2 ce d7 4e 44 b2  |Ss.1..csf:...ND.|
000000d0  c8 cd 7c fa 50 73 69 7f  59 97 56 5b 0a 8f 21 6b  |..|.Psi.Y.V[..!k|
000000e0  56 bb 84 e9 59 0b 82 f2  63 5c 75 48 a3 7f c8 8a  |V...Y...c\uH....|
000000f0  a8 8d de 74 14 52 41 82  77 3d 8d b8 a6 52 f1 b0  |...t.RA.w=...R..|
00000100  7f 47 a6 81 56 7d 89 ef  d3 91 10 fb bf 0e 22 38  |.G..V}........"8|
00000110  d8 a0 86 5b 39 54 60 79  e8 b6 62 59 7a 2b c8 e2  |...[9T`y..bYz+..|
00000120  c7 97 62 ab 33 2b 4b 5e  2d 2a 70 96 a4 e0 96 a3  |..b.3+K^-*p.....|
00000130  6c 33 77 5b 29 6e ed ec  a4 c7 f2 d4 89 d1 bd 0f  |l3w[)n..........|
00000140  4c 3f bf da af 84 fa c8  80 2e 61 54 89 fb fe bb  |L?........aT....|
00000150  f0 f3 8e c7 e6 6d 43 c2  ff ac 7b 09 79 2f a3 e2  |.....mC...{.y/..|
00000160  95 df 73 ff b0 31 01 ce  2b ee 1f c0 2a a8 4d 24  |..s..1..+...*.M$|
00000170  9f 78 8c 3f 75 4a d9 54  70 83 dc d9 41 14 21 4c  |.x.?uJ.Tp...A.!L|
00000180  22 c1 9b 89 68 6a 83 9f  c9 df 55 d4 ca 3a 51 a8  |"...hj....U..:Q.|
00000190  42 d8 43 43 cb ed 25 db  f1 f5 b5 85 0c 2f 4f 80  |B.CC..%....../O.|
000001a0  56 5f fd 9f a3 94 0f 13  e7 cb 40 ee 7a b9 26 70  |V_........@.z.&p|
000001b0  b7 c7 1f bd 73 7c 93 50  42 aa 78 08 de c7 35 0d  |....s|.PB.x...5.|
000001c0  f6 08 df 35 7f fb 4c d2  59 8d e2 b0 ef 7f 1c 47  |...5..L.Y......G|
000001d0  93 df f8 a5 83 88 de 1a  27 db a0 41 25 9a 0d ab  |........'..A%...|
000001e0  b4 59 c9 76 c7 96 83 26  d4 05 fb aa 66 77 2c 9b  |.Y.v...&....fw,.|
000001f0  2f ab f2 a4 1c bb d8 fb  48 45 b1 52 1d 07 4f 05  |/.......HE.R..O.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 20 00  |.X.SYSLINUX..@ .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  82 37 f9 0d c3 6f 00 00  00 00 00 00 02 00 00 00  |.7...o..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 5f 16 fc 19 4e  4f 20 4e 41 4d 45 20 20  |..)_...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 a6  fb 16 00 66 ba 00 00 00  |..E}.f.....f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2011-05-03
System cannot mount sda1 which says there is a problem with that partition. Perhaps it is not Linux type 83 but is NTFS type7??

You could try changing it with Disk Utility on a liveCD, but I would probably suggest you use testdisk.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

If it recovers the NTFS partition it may not be bootable and will probably require repairs that may not completely repair it. But then you should be able to backup important data.

How did you install 11.04 and end up with grub legacy. All the new installs would normally have grub2??

---

