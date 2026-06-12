---
title: "Error at start"
date: 2011-01-25
forum: General Help
---

### Post by Dsky on 2011-01-25
i just finished installing ubuntu 10.10, sometimes occurr this error

[IMG]http://img716.imageshack.us/img716/5261/errcq.jpg[/IMG]

what could be caused by?

---

### Post by Smart Viking on 2011-01-25
Would be very useful to see a boot info script here.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Where is grub installed?

---

### Post by matt_symes on 2011-01-25
Hi

> sometimes occurr this error

Is it an intermittent problem ? Does it boot sometimes and not others ? Do you have raid or something like that ? Any special setup?

If it is an intermittent problem then you can increase the root delay by editing the kernel boot line.

Try this...

Press ALT and F2 together and in the run dialog box type

```
gksudo gedit /etc/default/grub
```

Find the line GRUB_CMDLINE_LINUX_DEFAULT="....."

To any existing values try this rootdelay=100

so mine would become...

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash rootdelay=100"
```

then open a terminal and type

```
sudo update-grub
```

and enter your password as normal.

Does this fix it?

Kind regards

---

### Post by Dsky on 2011-01-25
now i try. this is my actual grub

> GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

@smart viking sorry what have i to do with that?

---

### Post by Smart Viking on 2011-01-25
> **Dsky said:**
> 
@smart viking sorry what have i to do with that?
You just download the .sh file, give it permissions to execute as a program and then run it in the terminal.

---

### Post by Dsky on 2011-01-25
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 20.4 GB, 20411080704 byte
255 testine, 63 settori/tracce, 2481 cilindri, totale 39865392 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    37,912,575    37,910,528  83 Linux
/dev/sda2          37,914,622    39,864,319     1,949,698   5 Extended
/dev/sda5          37,914,624    39,864,319     1,949,696  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 100.3 GB, 100256292864 byte
255 testine, 63 settori/tracce, 12188 cilindri, totale 195813072 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   195,800,219   195,800,157   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        c8fbfa62-d6f2-427f-8238-11e470d4d31e   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        95a37b86-f504-4c8f-b200-0b6b6d1b5a6f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        72FC12A5FC12641F                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/72FC12A5FC12641F  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c8fbfa62-d6f2-427f-8238-11e470d4d31e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c8fbfa62-d6f2-427f-8238-11e470d4d31e
set locale_dir=($root)/boot/grub/locale
set lang=it
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=2
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c8fbfa62-d6f2-427f-8238-11e470d4d31e
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=c8fbfa62-d6f2-427f-8238-11e470d4d31e ro   quiet splash rootdelay=100
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c8fbfa62-d6f2-427f-8238-11e470d4d31e
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=c8fbfa62-d6f2-427f-8238-11e470d4d31e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c8fbfa62-d6f2-427f-8238-11e470d4d31e
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=c8fbfa62-d6f2-427f-8238-11e470d4d31e ro   quiet splash rootdelay=100
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c8fbfa62-d6f2-427f-8238-11e470d4d31e
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=c8fbfa62-d6f2-427f-8238-11e470d4d31e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c8fbfa62-d6f2-427f-8238-11e470d4d31e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c8fbfa62-d6f2-427f-8238-11e470d4d31e
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
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=95a37b86-f504-4c8f-b200-0b6b6d1b5a6f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   6.8GB: boot/grub/core.img
  13.0GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-22-generic
    .9GB: boot/initrd.img-2.6.35-24-generic
   6.9GB: boot/vmlinuz-2.6.35-22-generic
   6.9GB: boot/vmlinuz-2.6.35-24-generic
    .9GB: initrd.img
    .9GB: initrd.img.old
   6.9GB: vmlinuz
   6.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  b0 97 0f bf b5 8a 06 fd  3a 75 94 7c 9c be 88 a5  |........:u.|....|
00000010  59 95 49 db e9 10 cb fb  c5 e1 aa e0 cd 42 6e 74  |Y.I..........Bnt|
00000020  1d a6 58 3f 6d d4 f0 7e  c0 e5 8f fd ba 10 7e 7b  |..X?m..~......~{|
00000030  7f 25 86 b7 e5 66 73 92  61 3a 20 3f e2 a5 54 a1  |.%...fs.a: ?..T.|
00000040  5d d3 06 54 31 97 c2 33  51 ce d1 54 b4 0f 15 b2  |]..T1..3Q..T....|
00000050  bf 14 5f 08 cd 7f 4d 67  0d a2 d7 09 d9 41 64 e9  |.._...Mg.....Ad.|
00000060  37 62 41 a1 07 58 09 21  e8 d5 29 af 19 cc c6 f6  |7bA..X.!..).....|
00000070  0f fd 05 ae 79 d5 5b 07  75 a9 79 ab 9a 85 84 12  |....y.[.u.y.....|
00000080  80 ff 9e b2 ee 19 b5 c3  fe 29 0a ec 26 8c db 9f  |.........)..&...|
00000090  0b f0 f1 cb d7 6c f7 a9  aa 07 88 35 f2 2d 8f 5e  |.....l.....5.-.^|
000000a0  52 aa 56 67 26 c7 de e8  91 5a d4 2c 4b 35 d4 d5  |R.Vg&....Z.,K5..|
000000b0  2c 0b 42 66 dc c3 17 75  5b 7a 71 cb 76 79 82 96  |,.Bf...u[zq.vy..|
000000c0  e6 1c 0c 53 a8 ea 93 06  d5 ea 24 00 d0 5f 59 a4  |...S......$.._Y.|
000000d0  a6 02 11 a5 ca 9a 43 23  cd 88 47 c0 94 2a 46 4c  |......C#..G..*FL|
000000e0  da c9 00 6b fe 9b c8 0a  83 87 ce 2e b3 77 50 fa  |...k.........wP.|
000000f0  d6 14 c2 66 1c e3 0e 16  fa ef 33 4d f2 1d 7d 3a  |...f......3M..}:|
00000100  83 e0 2d 3f 7c ba e6 a5  0e a4 11 a5 29 51 a4 a1  |..-?|.......)Q..|
00000110  9a 89 88 74 82 fa 50 ab  b6 b1 e4 c3 69 a3 72 82  |...t..P.....i.r.|
00000120  1b a1 2c 7c 00 00 2b 03  62 06 ea 31 8a 97 e0 26  |..,|..+.b..1...&|
00000130  43 6c 8e 69 0c f0 e4 4c  e3 48 16 3a a0 4b 14 97  |Cl.i...L.H.:.K..|
00000140  56 e0 a9 62 b8 09 a0 13  ee f4 88 47 25 55 b3 a4  |V..b.......G%U..|
00000150  55 f6 85 75 be 7c e0 f4  50 7c 9c 16 0b d3 40 88  |U..u.|..P|....@.|
00000160  a9 15 5a b2 bb 4d 99 6e  e3 03 3d 79 48 ef f0 a6  |..Z..M.n..=yH...|
00000170  37 3c 6b 6f 39 1a 02 69  e0 97 03 f3 11 dc 1d 9c  |7<ko9..i........|
00000180  29 b4 c4 f4 ad 46 db bd  c7 07 d6 eb 4a 2c 4a e2  |)....F......J,J.|
00000190  9c 3c df bb af 64 84 23  c9 66 dd 77 ec f2 46 1d  |.<...d.#.f.w..F.|
000001a0  2b de e9 5e 38 98 99 06  f3 9b 3c 8c 6a 93 db 21  |+..^8.....<.j..!|
000001b0  0d b2 e6 3a fa 5f 91 33  40 4b ee 95 e3 d9 00 fe  |...:._.3@K......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 c0 1d 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by matt_symes on 2011-01-25
Hi

I would change your fstab so your root mount point uses UUID's

At the moment it is

> proc            /proc           proc    nodev,noexec,nosuid 0       0
**/dev/sda1**       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=95a37b86-f504-4c8f-b200-0b6b6d1b5a6f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

I would change it to

> proc            /proc           proc    nodev,noexec,nosuid 0       0
**UUID=c8fbfa62-d6f2-427f-8238-11e470d4d31e**       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=95a37b86-f504-4c8f-b200-0b6b6d1b5a6f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Are you always getting the error or is it every so often ? Are you still getting the error ?

Kind regards

---

