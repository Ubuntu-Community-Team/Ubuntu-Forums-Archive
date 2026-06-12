---
title: "Dual Boot Problems"
date: 2011-03-29
forum: General Help
---

### Post by vorinoch on 2011-03-29
Hi folks.

I'm running a Win7/Ubuntu dual boot.  Windows is on sda1, Linux is on sda2.  For awhile, both were bootable off the GRUB menu.  Somehow, recently, Windows 7 was removed from the options.  Is there any way to easily get it back?  I'm nervous about using the Windows install disk to rescue Windows, as I'm fairly sure that would wipe out GRUB.  I feel this must be an easy problem, but I'm new to Linux in general.  Any advice?

---

### Post by Zookalicious on 2011-03-29
The recovery disk will wipe grub. You can use it, but you'll have to reinstall grub from a liveCD later (which is a bit of a pain).

Have you tried updating your grub list?

You do this by entering "sudo update-grub" in the terminal. It should automatically return Windows to that list.

---

### Post by vorinoch on 2011-03-29
Tried that, no dice.  And the walkthroughs online all mention making edits to /boot/grub/menu.lst.... which is unfortunate, because for some reason I do not have that file (I'm running Lucid.)

---

### Post by drs305 on 2011-03-29
You are most likely using Grub 2, which doesn't use menu.lst.

If you will download and run the boot info script from the following site we can see what has happened to your boot files. Post the contents of the file it generates: RESULTS.txt
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by vorinoch on 2011-03-29
Thanks.  Here's the output:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows Vista/7
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
224 heads, 19 sectors/track, 114754 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   409,602,047   409,600,000   7 HPFS/NTFS
/dev/sda2    *    409,602,048   481,867,672    72,265,625  83 Linux
/dev/sda3         481,867,774   488,396,799     6,529,026   5 Extended
/dev/sda5         481,867,776   488,396,799     6,529,024  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        7cb73726-e01b-4846-8760-ca3cc75297e8   ext2       LFS                           
/dev/sda3: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9CC082FEC082DE40                       ntfs       Storage Disk                  
/dev/sdb: PTTYPE="dos" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
cryptswap1

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext2       (rw,errors=remount-ro)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 7cb73726-e01b-4846-8760-ca3cc75297e8
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 7cb73726-e01b-4846-8760-ca3cc75297e8
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 7cb73726-e01b-4846-8760-ca3cc75297e8
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=7cb73726-e01b-4846-8760-ca3cc75297e8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 7cb73726-e01b-4846-8760-ca3cc75297e8
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=7cb73726-e01b-4846-8760-ca3cc75297e8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 7cb73726-e01b-4846-8760-ca3cc75297e8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 7cb73726-e01b-4846-8760-ca3cc75297e8
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/ll_Windows ###
menuentry &#8220;Windows 7&#8243; {
set root=(hd0,1)
chainloader +1
}
EOF 
### END /etc/grub.d/ll_Windows ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=7cb73726-e01b-4846-8760-ca3cc75297e8 /               ext2    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=61c28b81-e385-482b-93d4-9128866e1753 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0

=================== sda2: Location of files loaded by Grub: ===================


 222.9GB: boot/grub/core.img
 222.9GB: boot/grub/grub.cfg
 223.0GB: boot/initrd.img-2.6.32-24-generic
 222.9GB: boot/vmlinuz-2.6.32-24-generic
 223.0GB: initrd.img
 222.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  e7 7a b2 71 1b 44 a9 c8  ea 44 b8 17 fe e1 d7 cd  |.z.q.D...D......|
00000010  73 fb 27 f8 00 6d 59 c7  92 53 bd 59 e8 83 3e 47  |s.'..mY..S.Y..>G|
00000020  9b b7 21 52 70 88 0e 9e  44 8d ba 3d 1c 70 6f 97  |..!Rp...D..=.po.|
00000030  d1 f3 da ac 47 95 d3 c1  37 1d 08 d9 22 c0 96 d3  |....G...7..."...|
00000040  11 0f 02 7b 3b b2 39 bf  7d 62 13 fd 4a d3 37 ef  |...{;.9.}b..J.7.|
00000050  4a 3e 87 c6 ce c5 af 06  79 38 7f d4 9a c7 b2 cf  |J>......y8......|
00000060  88 be 63 08 20 74 ed 5b  42 02 88 42 2a c0 2f b7  |..c. t.[B..B*./.|
00000070  17 63 9e 5c 0c 8c fa ec  60 94 ce ca fc a2 1c bd  |.c.\....`.......|
00000080  4c e7 5d e4 f2 27 1c 26  b5 5a 7e 03 17 fd 3a 1b  |L.]..'.&.Z~...:.|
00000090  b4 54 a9 1f f1 41 e0 1a  de 0f 6a 90 05 b1 ad 86  |.T...A....j.....|
000000a0  4a d6 7e 62 20 10 25 98  78 eb 3d f9 3b fe 66 37  |J.~b .%.x.=.;.f7|
000000b0  7b 5b 76 69 b7 ba 0c 4f  5d cb e6 b8 3b 4b 93 2e  |{[vi...O]...;K..|
000000c0  18 31 22 9c e3 b6 08 1f  bb 10 2c e4 4d 33 aa 2a  |.1".......,.M3.*|
000000d0  6e 92 b7 20 29 2c 57 5b  b9 b0 52 49 a6 88 9b 56  |n.. ),W[..RI...V|
000000e0  b4 0a de b3 36 ed 3c 55  9c 46 0c 00 5e 74 ce 29  |....6.<U.F..^t.)|
000000f0  d7 57 f0 29 cb 53 2b 35  df 59 1a b3 bc f8 22 8a  |.W.).S+5.Y....".|
00000100  b9 9d 3d 30 55 b1 e2 37  77 d2 05 9b b6 13 a1 b2  |..=0U..7w.......|
00000110  8e e0 c4 e3 a6 d0 00 dd  c9 bf 62 a3 95 18 d8 95  |..........b.....|
00000120  9b 43 31 39 e7 3a 4e 68  09 3f 81 3d 75 4f 89 81  |.C19.:Nh.?.=uO..|
00000130  85 9b d2 2f ae 56 9e 9c  80 18 89 68 f4 c4 ef 0f  |.../.V.....h....|
00000140  09 f4 50 ac 9f d7 37 26  d8 e7 06 33 39 40 8d de  |..P...7&...39@..|
00000150  61 08 cf 3c 26 4d ac 3e  bf 9a 20 b2 3a 8a 1b 41  |a..<&M.>.. .:..A|
00000160  e7 e5 92 54 ea bc 66 05  97 df a9 f7 4e 06 1e a8  |...T..f.....N...|
00000170  55 76 a2 05 19 26 09 ec  e7 f7 75 2d e1 5c 65 85  |Uv...&....u-.\e.|
00000180  04 11 a2 ed d0 29 bc 25  7e 53 b3 50 99 df bf c6  |.....).%~S.P....|
00000190  b9 01 be 71 36 75 3d b9  81 98 17 41 f7 e8 11 05  |...q6u=....A....|
000001a0  b9 81 27 22 4b d8 75 bd  4f 5b fe 59 25 5d 16 fb  |..'"K.u.O[.Y%]..|
000001b0  f6 e8 c4 28 94 09 89 6c  8e d4 62 38 c5 d9 00 df  |...(...l..b8....|
000001c0  d3 ff 82 df d3 ff 02 00  00 00 00 a0 63 00 00 00  |............c...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

That "Windows 7" menuentry in /etc/grub.d/ll_Windows was from the last piece of advice I tried that didn't work.

---

### Post by vorinoch on 2011-03-29
Also, if this makes a difference, this problem SEEMED to happen right after I booted off a LiveCD.  I'm not sure what a LiveCD would be doing tinkering with GRUB, but the timing was right.

---

### Post by drs305 on 2011-03-29
Neither your Win7 sda1 or XP sdb1 contain any of the boot folders/files ( /bootmgr /Boot/BCD /Windows/System32/winload.exe) Grub2 would normally find therein.

Where these files should reside depends on the order you installed Windows. Grub2 looks for those folders, didn't find them, and thus didn't construct a menuentry.

You will need to use a Windows repair/installation disk to repair Windows (most likely using fixmbr and fixboot, but I'll leave that to you Windows guys).

Here are forum member *oldfred's* Windows repair links (Post 7):
[http://ubuntuforums.org/showthread.php?p=9826152]("http://ubuntuforums.org/showthread.php?p=9826152")

Once you repair Windows and get it booting, you can install Grub2 to the MBR to get it working again:
```

sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Don't use the partition number in the second command.

---

### Post by vorinoch on 2011-03-29
Thanks for the tip, I'll take a look at it.

---

