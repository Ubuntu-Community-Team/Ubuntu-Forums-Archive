---
title: "OS won't load after grub."
date: 2011-05-01
forum: General Help
---

### Post by ninjaaron on 2011-05-01
So I just did a restart on my computer (so the new keyboard layout I made would load up). After the grub screen, I just got a black screen and a flashing cursor. My caps lock indicator was also flashing for some reason.

Tried booting to recovery mode. Got some messages I didn't understand and then the same thing. I'm posting from my LiveUSB.

I was messing with some files in /usr/share/X11/xkb, but I don't see why that should make a difference.

*Edit: copied from my post below*
So, I copied some of the messages down that I got from trying to boot to the recovery kernel. I didn't copy them all, cause they went by quickly, but here is the stuff from the last page where it starts to look bad.

*There are numbers before each line that look something like this: *```
[        1.344064]
```*I didn't copy those.*

```

   List of all partitions:
   No filesystem could mount root, tried ext3 ext4 fuseblk
   kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)
   Pid: 1, comm: swapper not tainted 2.6.38-8-generic #42 Ubuntu
   Call Trace:

```

and then there were a bunch of lines that looked more or less like this with different specifics:
```
[<c 1507054] ? panic + 0x5c1/0x157
```
I can get the rest if they are important.

There may be small mistakes, as I copied this all by hand (since my damn computer is broken and all).

*Another Edit*
Some "Boot Info Script" results:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2d.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   618,991,615   618,989,568  83 Linux
/dev/sda2         618,993,662   625,141,759     6,148,098   5 Extended
/dev/sda5         618,993,664   625,141,759     6,148,096  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4012 MB, 4012900352 bytes
124 heads, 62 sectors/track, 1019 cylinders, total 7837696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     7,834,071     7,834,010   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       4389149c-38eb-4623-a931-7e8c2bcaf1bb   ext3                                     
/dev/sda1        a031a1f7-a677-4e19-be0d-f76c22c7e5f9   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        cfa8688f-6af1-43af-8637-d00eca4ffaa4   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        038B-31C1                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root a031a1f7-a677-4e19-be0d-f76c22c7e5f9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root a031a1f7-a677-4e19-be0d-f76c22c7e5f9
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a031a1f7-a677-4e19-be0d-f76c22c7e5f9
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a031a1f7-a677-4e19-be0d-f76c22c7e5f9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a031a1f7-a677-4e19-be0d-f76c22c7e5f9
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a031a1f7-a677-4e19-be0d-f76c22c7e5f9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a031a1f7-a677-4e19-be0d-f76c22c7e5f9
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a031a1f7-a677-4e19-be0d-f76c22c7e5f9
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a031a1f7-a677-4e19-be0d-f76c22c7e5f9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cfa8688f-6af1-43af-8637-d00eca4ffaa4 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 124.7GB: boot/grub/core.img
 124.6GB: boot/grub/grub.cfg
 120.6GB: boot/initrd.img-2.6.38-8-generic
 124.6GB: boot/vmlinuz-2.6.38-8-generic
 120.6GB: initrd.img
 124.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  63 6e 01 85 4c b7 e5 18  7b e7 60 65 88 ab 5b 29  |cn..L...{.`e..[)|
00000010  a8 b0 c9 b2 1d 4d 5a e9  30 b1 f1 ad 3b d2 cb 6d  |.....MZ.0...;..m|
00000020  c4 ac e7 c5 67 c9 43 1b  77 f6 af 18 34 ea d6 98  |....g.C.w...4...|
00000030  ef d4 28 13 25 3a d0 7b  a0 1b a5 29 a7 3f 69 dc  |..(.%:.{...).?i.|
00000040  ca e3 cc bb e7 62 3d fd  2f ba 43 3d c9 dc dd 5b  |.....b=./.C=...[|
00000050  35 1a ef 6a be 54 3a 2e  69 bb fa 95 54 da cb 59  |5..j.T:.i...T..Y|
00000060  39 79 4c 75 1d 74 20 14  15 aa 0c 1c f1 b2 ff 93  |9yLu.t .........|
00000070  bd cc 99 ea 69 32 f0 17  53 5e ca 0e 62 48 86 40  |....i2..S^..bH.@|
00000080  2a 73 e6 27 49 dc c9 56  8e 1e 40 5c 37 41 4b 89  |*s.'I..V..@\7AK.|
00000090  50 97 fe a0 8c 7b c9 a6  16 2b b7 c3 93 b7 47 a5  |P....{...+....G.|
000000a0  1d 83 36 49 ec db 2d 4e  97 73 8c e9 c9 dd 9a 26  |..6I..-N.s.....&|
000000b0  04 fe e8 55 d6 ea ad 05  d1 ba a0 ed e7 94 56 c3  |...U..........V.|
000000c0  f5 df 6a 8d 68 82 51 c6  a5 47 25 d2 4c 75 2d 87  |..j.h.Q..G%.Lu-.|
000000d0  a3 dc aa 92 9a 11 ed 6e  39 54 97 39 c8 f7 57 e6  |.......n9T.9..W.|
000000e0  d1 f0 a9 c8 73 0e 73 e2  70 ba cd e7 69 e7 43 b1  |....s.s.p...i.C.|
000000f0  1c d0 6b 75 d2 60 5c 5e  3d 57 5f df 53 04 3d 60  |..ku.`\^=W_.S.=`|
00000100  25 b6 90 d9 11 ef 52 75  a2 76 d3 e7 17 90 f9 f8  |%.....Ru.v......|
00000110  61 68 df 49 eb 6b 8f a5  8e c8 62 7f f7 cb 78 ea  |ah.I.k....b...x.|
00000120  07 64 d7 6e e1 44 f6 aa  a9 ed c8 72 cd 54 61 75  |.d.n.D.....r.Tau|
00000130  2f 60 7a 51 d0 e2 d8 62  21 17 bd 67 36 a1 9e 93  |/`zQ...b!..g6...|
00000140  cc 75 a6 eb 40 82 57 39  d7 63 74 3c 57 ed 99 37  |.u..@.W9.ct<W..7|
00000150  5b f6 f0 f0 42 9d 5d d2  b2 0d 6a 25 db bd 2d cc  |[...B.]...j%..-.|
00000160  c7 d3 bb 6f e9 6b b8 23  6c 58 4a fa 14 c6 59 a5  |...o.k.#lXJ...Y.|
00000170  b9 6d d8 0d 1c e5 26 cd  f0 3b 2b 43 d7 8a c3 2a  |.m....&..;+C...*|
00000180  9f fa b6 d1 e7 1a 75 c1  a9 43 e6 c0 87 38 4d ec  |......u..C...8M.|
00000190  23 f9 e3 0b ac 47 1a 15  55 9a 13 57 0f c9 81 6a  |#....G..U..W...j|
000001a0  f9 8e ef 5a f1 53 cd 40  81 36 92 7d c3 a1 fd 2a  |...Z.S.@.6.}...*|
000001b0  02 0f 99 0e 66 d7 68 ef  14 df 31 c7 6e 66 00 fe  |....f.h...1.nf..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d0 5d 00 00 00  |............]...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 7c 00 00 00 00 00  |........>.|.....|
00000020  9a 89 77 00 d8 1d 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 c1 31 8b 03 20  20 20 20 20 20 20 20 20  |..).1..         |
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
00000100  7d 00 66 b8 b8 a4 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e d2 1d 08 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
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

### Post by LittleJakub on 2011-05-01
BUMP!

also, if U could BUMP! my post, I think we are having similar problem.

If that's true- the more of us, the faster there should be a fix ;)

[http://ubuntuforums.org/showthread.php?t=1746032]("http://ubuntuforums.org/showthread.php?t=1746032")

---

### Post by stuart221 on 2011-05-01
Hi Follow the following link and reinstall grub from live CD hope it helps. 
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

---

### Post by ninjaaron on 2011-05-01
Grub works. It's after grub that I have the problem.

---

### Post by LittleJakub on 2011-05-01
let me just get it straight- do u have only ubuntu, or it's a multi-boot setup?

P.S. lookie here, just say if it's more or less the same (at least with the led diodes): [http://ubuntuforums.org/showthread.php?t=1746032]("http://ubuntuforums.org/showthread.php?t=1746032")

---

### Post by ninjaaron on 2011-05-01
Sounds similar, except mine isn't booting at all, no matter what I do. It's bad.

---

### Post by LittleJakub on 2011-05-01
hmm... have you done any updates, or it has such a problem right after a fresh install?

---

### Post by ninjaaron on 2011-05-01
So, I copied some of the messages down that I got from trying to boot to the recovery kernel. I didn't copy them all, cause they went by quickly, but here is the stuff from the last page where it starts to look bad.

[I]There are numbers before each line that look something like this:
[/i]```
[        1.344064]
```[i]
I didn't copy those.[/I]

```

   List of all partitions:
   No filesystem could mount root, tried ext3 ext4 fuseblk
   kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)
   Pid: 1, comm: swapper not tainted 2.6.38-8-generic #42 Ubuntu
   Call Trace:

```
and then there were a bunch of lines that looked more or less like this with different specifics:
```
[<c 1507054] ? panic + 0x5c1/0x157
```
I can get the rest if they are important.

There may be small mistakes, as I copied this all by hand (since my damn computer is broken and all).

---

### Post by ninjaaron on 2011-05-01
> **LittleJakub said:**
> hmm... have you done any updates, or it has such a problem right after a fresh install?

I did some updates, but I think it was only firefox. I've been using natty since alpha 1 and I haven't had this problem. This is a fresh install of the release, however, but i have used that a couple of days and this is the first time I've seen the problem.

---

### Post by LittleJakub on 2011-05-01
so yup, your messages look kinda familiar to mine, except you cannot boot into system at all :/

the numbers in [         xxxxxxxxx] is time I guess, in which the error came up..

in general- the thing we are experiencing is calle a kernel panic- on a properly operating system it occurs once in a (insert big number here).

I tried to search the net for some solutions. One of them is when being in grub to press "E" on a selected boot option and to add "modeset=0" nex to "quiet splash". Say if it helps, cause in my case it didn't. Cheers.

---

### Post by ninjaaron on 2011-05-01
Well it's worth a shot.

In the meantime, I just ran the "Boot Info Script." These are my "results." Don't know if they help.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2d.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   618,991,615   618,989,568  83 Linux
/dev/sda2         618,993,662   625,141,759     6,148,098   5 Extended
/dev/sda5         618,993,664   625,141,759     6,148,096  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4012 MB, 4012900352 bytes
124 heads, 62 sectors/track, 1019 cylinders, total 7837696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     7,834,071     7,834,010   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       4389149c-38eb-4623-a931-7e8c2bcaf1bb   ext3                                     
/dev/sda1        a031a1f7-a677-4e19-be0d-f76c22c7e5f9   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        cfa8688f-6af1-43af-8637-d00eca4ffaa4   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        038B-31C1                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root a031a1f7-a677-4e19-be0d-f76c22c7e5f9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root a031a1f7-a677-4e19-be0d-f76c22c7e5f9
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a031a1f7-a677-4e19-be0d-f76c22c7e5f9
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a031a1f7-a677-4e19-be0d-f76c22c7e5f9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a031a1f7-a677-4e19-be0d-f76c22c7e5f9
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a031a1f7-a677-4e19-be0d-f76c22c7e5f9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a031a1f7-a677-4e19-be0d-f76c22c7e5f9
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a031a1f7-a677-4e19-be0d-f76c22c7e5f9
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a031a1f7-a677-4e19-be0d-f76c22c7e5f9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cfa8688f-6af1-43af-8637-d00eca4ffaa4 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 124.7GB: boot/grub/core.img
 124.6GB: boot/grub/grub.cfg
 120.6GB: boot/initrd.img-2.6.38-8-generic
 124.6GB: boot/vmlinuz-2.6.38-8-generic
 120.6GB: initrd.img
 124.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  63 6e 01 85 4c b7 e5 18  7b e7 60 65 88 ab 5b 29  |cn..L...{.`e..[)|
00000010  a8 b0 c9 b2 1d 4d 5a e9  30 b1 f1 ad 3b d2 cb 6d  |.....MZ.0...;..m|
00000020  c4 ac e7 c5 67 c9 43 1b  77 f6 af 18 34 ea d6 98  |....g.C.w...4...|
00000030  ef d4 28 13 25 3a d0 7b  a0 1b a5 29 a7 3f 69 dc  |..(.%:.{...).?i.|
00000040  ca e3 cc bb e7 62 3d fd  2f ba 43 3d c9 dc dd 5b  |.....b=./.C=...[|
00000050  35 1a ef 6a be 54 3a 2e  69 bb fa 95 54 da cb 59  |5..j.T:.i...T..Y|
00000060  39 79 4c 75 1d 74 20 14  15 aa 0c 1c f1 b2 ff 93  |9yLu.t .........|
00000070  bd cc 99 ea 69 32 f0 17  53 5e ca 0e 62 48 86 40  |....i2..S^..bH.@|
00000080  2a 73 e6 27 49 dc c9 56  8e 1e 40 5c 37 41 4b 89  |*s.'I..V..@\7AK.|
00000090  50 97 fe a0 8c 7b c9 a6  16 2b b7 c3 93 b7 47 a5  |P....{...+....G.|
000000a0  1d 83 36 49 ec db 2d 4e  97 73 8c e9 c9 dd 9a 26  |..6I..-N.s.....&|
000000b0  04 fe e8 55 d6 ea ad 05  d1 ba a0 ed e7 94 56 c3  |...U..........V.|
000000c0  f5 df 6a 8d 68 82 51 c6  a5 47 25 d2 4c 75 2d 87  |..j.h.Q..G%.Lu-.|
000000d0  a3 dc aa 92 9a 11 ed 6e  39 54 97 39 c8 f7 57 e6  |.......n9T.9..W.|
000000e0  d1 f0 a9 c8 73 0e 73 e2  70 ba cd e7 69 e7 43 b1  |....s.s.p...i.C.|
000000f0  1c d0 6b 75 d2 60 5c 5e  3d 57 5f df 53 04 3d 60  |..ku.`\^=W_.S.=`|
00000100  25 b6 90 d9 11 ef 52 75  a2 76 d3 e7 17 90 f9 f8  |%.....Ru.v......|
00000110  61 68 df 49 eb 6b 8f a5  8e c8 62 7f f7 cb 78 ea  |ah.I.k....b...x.|
00000120  07 64 d7 6e e1 44 f6 aa  a9 ed c8 72 cd 54 61 75  |.d.n.D.....r.Tau|
00000130  2f 60 7a 51 d0 e2 d8 62  21 17 bd 67 36 a1 9e 93  |/`zQ...b!..g6...|
00000140  cc 75 a6 eb 40 82 57 39  d7 63 74 3c 57 ed 99 37  |.u..@.W9.ct<W..7|
00000150  5b f6 f0 f0 42 9d 5d d2  b2 0d 6a 25 db bd 2d cc  |[...B.]...j%..-.|
00000160  c7 d3 bb 6f e9 6b b8 23  6c 58 4a fa 14 c6 59 a5  |...o.k.#lXJ...Y.|
00000170  b9 6d d8 0d 1c e5 26 cd  f0 3b 2b 43 d7 8a c3 2a  |.m....&..;+C...*|
00000180  9f fa b6 d1 e7 1a 75 c1  a9 43 e6 c0 87 38 4d ec  |......u..C...8M.|
00000190  23 f9 e3 0b ac 47 1a 15  55 9a 13 57 0f c9 81 6a  |#....G..U..W...j|
000001a0  f9 8e ef 5a f1 53 cd 40  81 36 92 7d c3 a1 fd 2a  |...Z.S.@.6.}...*|
000001b0  02 0f 99 0e 66 d7 68 ef  14 df 31 c7 6e 66 00 fe  |....f.h...1.nf..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d0 5d 00 00 00  |............]...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 7c 00 00 00 00 00  |........>.|.....|
00000020  9a 89 77 00 d8 1d 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 c1 31 8b 03 20  20 20 20 20 20 20 20 20  |..).1..         |
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
00000100  7d 00 66 b8 b8 a4 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e d2 1d 08 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
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

### Post by ninjaaron on 2011-05-01
> **LittleJakub said:**
> I tried to search the net for some solutions. One of them is when being in grub to press "E" on a selected boot option and to add "modeset=0" nex to "quiet splash". Say if it helps, cause in my case it didn't. Cheers.

didn't work for me either :(

---

### Post by LittleJakub on 2011-05-01
Then we have a problem. Well, U definitely have a "bigger" one- U can't boot into the system in ANY way :/

I just don't get how can such problems occur in newer kernels, which should be an improvement of previous ones, not a fault. :/

---

### Post by ninjaaron on 2011-05-01
> **LittleJakub said:**
> Then we have a problem. Well, U definitely have a "bigger" one- U can't boot into the system in ANY way :/

I just don't get how can such problems occur in newer kernels, which should be an improvement of previous ones, not a fault. :/

I've been using this kernel for a few weeks now, and this is the first I've seen of it.

---

### Post by LittleJakub on 2011-05-01
Ahhh, so it was not appearing from start.. Any specific file operations, some tricky soft installed?

For example, I caught myself once (a long time ago)- getting a similar problem, but that one was due to installing VirtualBox- dunno why, when uninstalled (or I even recall re-installing) all came back to normal.

---

### Post by ninjaaron on 2011-05-01
Alright, I don't have time to solve this problem "for real," so I'm going to backup my stuff, do a fresh install, and add some extra kernels first thing in case I run into this again.

:mad:

---

### Post by LittleJakub on 2011-05-01
well, I wish U luck mate! Hope it helps You. The "fresh install" doesn't jelp me, however.. :/

---

### Post by Kyous on 2011-05-01
Had a similar issue.  If you can boot into one of the older kernels try that and redo the update.  That fixed my CAPS light blinking on a blank screen.  Apparently my laptop was unplugged during the update process.

---

### Post by ninjaaron on 2011-05-02
fixed it, kinda. When I went to reinstall, I had the option to "upgrade 11.04 to 11.04"

This allowed me to reinstall the system files without changing my home folder. I have to redo my third party repos and some tweaks that were in the root filesystem.

> **Kyous said:**
> Had a similar issue.  If you can boot into one of the older kernels try that and redo the update.  That fixed my CAPS light blinking on a blank screen.  Apparently my laptop was unplugged during the update process.

I didn't have any old Kernels. It was a fresh install. I'm putting some extra kernels on now from the ubuntu kernel ppa so I will have more boot options in the future.

---

