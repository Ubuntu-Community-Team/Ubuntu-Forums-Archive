---
title: "win7/ubuntu dual boot problems"
date: 2011-07-18
forum: General Help
---

### Post by flyingsliverfin on 2011-07-18
Basic setup:
two harddrives, 
/dev/sda1 with windows XP [now win7]
/dev/sdb1 with ubuntu (/dev/sdb2&5 = swap space) 

what i had done three days ago is used the windows 7 CD to install onto the previous windows XP hard drive (sda). For a day I could then use windows 7 without a problem, except that i now had no GRUB menu since windows had overwritten the MBR for itself... For some reason i wanted to use ubuntu yesterday, so i got myself an Ultimate boot CD and ran Super GRUB2 Disk from that. From there I could boot ubuntu.

For some reason, when i then shut down the computer to try something in windows, it then started giving me the error:
```
A disk read error occurred. Ctr+Alt+Del to restart
```

Not really knowing what to do, I attempted to reinstall GRUB2 (i think the command i used from a 10.04 livecd was: grub-install /dev/sdb )

then it started giving me a different error:
```
No Boot device available
```

Now I don't know what to do, though it sounds like the MBR isn't doing its job properly.

Thanks!

---

### Post by oldfred on 2011-07-18
With two drives you have two MBRs. I would keep windows in sda, have grub2's boot loader in sdb and set BIOS to boot sdb so you can from the grub menu boot either system. If for any reason sdb has issues you could still boot windows from its MBR.

If you have an Intel motherboard, you may have the problem of no boot flag. Windows has to have a boot flag. Grub does not use a boot flag. But some BIOS will not let you boot unless you have a boot flag on a primary partition. No boot device sounds more like a BIOS error.

To see where everything is at now:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by flyingsliverfin on 2011-07-18
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Mounting failed:   
sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   156,248,189   156,248,127   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   146,485,247   146,483,200  83 Linux
/dev/sdb2         146,487,294   156,248,063     9,760,770   5 Extended
/dev/sdb5         146,487,296   156,248,063     9,760,768  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        4670CC2670CC1F15                       ntfs       
/dev/sdb1        2f1c51c2-9989-4990-b978-665939646cf9   ext4       
/dev/sdb5        b8d20875-060d-47c4-a54c-dfb8219bc361   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 2f1c51c2-9989-4990-b978-665939646cf9
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 2f1c51c2-9989-4990-b978-665939646cf9
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
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2f1c51c2-9989-4990-b978-665939646cf9
	linux	/boot/vmlinuz-2.6.32-32-generic root=UUID=2f1c51c2-9989-4990-b978-665939646cf9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2f1c51c2-9989-4990-b978-665939646cf9
	echo	'Loading Linux 2.6.32-32-generic ...'
	linux	/boot/vmlinuz-2.6.32-32-generic root=UUID=2f1c51c2-9989-4990-b978-665939646cf9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2f1c51c2-9989-4990-b978-665939646cf9
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=2f1c51c2-9989-4990-b978-665939646cf9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2f1c51c2-9989-4990-b978-665939646cf9
	echo	'Loading Linux 2.6.32-31-generic ...'
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=2f1c51c2-9989-4990-b978-665939646cf9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2f1c51c2-9989-4990-b978-665939646cf9
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=2f1c51c2-9989-4990-b978-665939646cf9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2f1c51c2-9989-4990-b978-665939646cf9
	echo	'Loading Linux 2.6.32-30-generic ...'
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=2f1c51c2-9989-4990-b978-665939646cf9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2f1c51c2-9989-4990-b978-665939646cf9
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=2f1c51c2-9989-4990-b978-665939646cf9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2f1c51c2-9989-4990-b978-665939646cf9
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=2f1c51c2-9989-4990-b978-665939646cf9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2f1c51c2-9989-4990-b978-665939646cf9
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 2f1c51c2-9989-4990-b978-665939646cf9
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 4670CC2670CC1F15
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=2f1c51c2-9989-4990-b978-665939646cf9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=b8d20875-060d-47c4-a54c-dfb8219bc361 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   8.127738953 = 8.727093248    boot/grub/core.img                             1
  20.298191071 = 21.795016704   boot/grub/grub.cfg                             1
   8.195896149 = 8.800276480    boot/initrd.img-2.6.32-24-generic              1
   8.265815735 = 8.875352064    boot/initrd.img-2.6.32-30-generic              1
  25.402927399 = 27.276185600   boot/initrd.img-2.6.32-31-generic              2
  16.082874298 = 17.268854784   boot/initrd.img-2.6.32-32-generic              2
   8.144767761 = 8.745377792    boot/vmlinuz-2.6.32-24-generic                 1
   8.150833130 = 8.751890432    boot/vmlinuz-2.6.32-30-generic                 1
  10.036190033 = 10.776276992   boot/vmlinuz-2.6.32-31-generic                 1
  10.055870056 = 10.797408256   boot/vmlinuz-2.6.32-32-generic                 1
  16.082874298 = 17.268854784   initrd.img                                     2
  25.402927399 = 27.276185600   initrd.img.old                                 2
  10.055870056 = 10.797408256   vmlinuz                                        1
  10.036190033 = 10.776276992   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  b0 71 91 b5 8b b5 0f da  21 63 14 76 bd 01 e7 65  |.q......!c.v...e|
00000010  5f 7d 78 ea 68 83 ca 45  27 39 27 e1 bd 8a eb 09  |_}x.h..E'9'.....|
00000020  c4 96 76 d7 66 b5 dd 56  ea 31 27 83 1e bb 82 1c  |..v.f..V.1'.....|
00000030  9c f4 90 d7 2a 40 c5 8e  40 15 c4 96 e7 fd 01 3b  |....*@..@......;|
00000040  0b 70 1e 49 93 8b 04 58  cc 42 c2 45 8c bb f9 bd  |.p.I...X.B.E....|
00000050  9b 17 ea 30 3e ee 92 d8  a3 51 9f 35 c4 e1 39 21  |...0>....Q.5..9!|
00000060  5e 5d ee 16 ae 82 db 77  e5 f9 8e b0 6a 83 56 6e  |^].....w....j.Vn|
00000070  fe a2 d4 da 8f 2a cf 9c  eb a7 c4 1a d3 9b f5 ec  |.....*..........|
00000080  67 9c 3f 1a 91 9a de 0b  d7 e1 92 22 18 de d5 72  |g.?........"...r|
00000090  7c 39 fb 3b 77 60 ca 48  1d d7 99 16 21 4a 40 07  ||9.;w`.H....!J@.|
000000a0  4f 56 fc 07 61 be e4 b8  ba 00 1b 31 40 9f a7 68  |OV..a......1@..h|
000000b0  6f 9c 5c 36 bf 3c cf 8e  87 3a dd a5 2f b7 7b e1  |o.\6.<...:../.{.|
000000c0  ee 8e 5a 19 fc c4 53 4f  1e 6d 29 d7 5b 1f 1d b7  |..Z...SO.m).[...|
000000d0  78 79 30 f7 c3 ac a9 ae  e5 ac ac 0f 38 d3 11 e2  |xy0.........8...|
000000e0  ac 24 4e 33 21 c0 ec ad  58 dc 7e 2b 50 77 8b 03  |.$N3!...X.~+Pw..|
000000f0  53 46 26 28 d4 50 fb 75  9c 2f 6e 11 7b 0c cc e1  |SF&(.P.u./n.{...|
00000100  07 3d 3e ae 84 e6 03 f6  18 5f de fb 2b 2e 1b aa  |.=>......_..+...|
00000110  87 b7 26 b4 fa 9a 89 00  f7 af ee 6e 9f 1d a7 c8  |..&........n....|
00000120  26 f6 73 3d de 72 e4 2e  18 f9 53 bf 9d a3 ab 66  |&.s=.r....S....f|
00000130  c3 8b 70 89 52 f6 34 74  22 7f bc f7 29 0a f1 4b  |..p.R.4t"...)..K|
00000140  a5 12 37 b5 1f cf fd 22  c7 16 d0 5b d0 c9 a3 d1  |..7...."...[....|
00000150  aa cc 90 10 04 9d 75 7a  74 ea 2a 01 84 53 47 e3  |......uzt.*..SG.|
00000160  3c b4 b1 da 05 5e 7e 65  44 3f 06 71 8d ee b9 92  |<....^~eD?.q....|
00000170  bf 6c 52 e8 2e b2 55 92  fe 42 49 f7 a6 51 1b b1  |.lR...U..BI..Q..|
00000180  7b b2 2f 31 ac 82 d4 d7  d5 29 22 85 70 b0 6b cb  |{./1.....)".p.k.|
00000190  c0 db 7b e6 46 71 7d 31  86 f7 5a 87 9b 8e b5 f9  |..{.Fq}1..Z.....|
000001a0  a5 9e 85 b2 3a 95 81 4f  5a 4d 84 37 fa 72 ef 2d  |....:..OZM.7.r.-|
000001b0  12 3b 93 2c e0 12 8e de  a1 38 99 f3 27 c6 00 fe  |.;.,.....8..'...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f0 94 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

./boot_info_script.sh: line 1997:  5727 Segmentation fault      ntfs-3g -o ro ${part} "${mountname}" 2>> ${Mount_Error}

```

I can understand the first part but not the last... :/

---

### Post by oldfred on 2011-07-18
You have the windows boot loader in sda & grub2's boot loader in sdb. You have a grub menu boot stanza for XP, but the script was not able to mount sda1 where XP is. It also says the boot sector is Vista/7??

The error on mounting is often some issue with the NTFS partition. If the chkdsk flag is set Ubuntu will not mount it to prevent damage that chkdsk might not then be able to fix.

I would try chkdsk first. You can use any windows repair CD to run the chkdsk.

To repair windows with mounting issues from your Windows XP CD - Do not run fixMBR unless you want windows boot loader in the MBR.
fixboot C:
XP CHKDSK command:
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

If you are booting XP but have the PBR - partition boot sector set for Vista/7 it will not boot as then it is looking to boot with bootmgr not XP's ntldr. You may then also need the fixBoot command from a XP disk.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by flyingsliverfin on 2011-07-18
yea sorry, the grub entry for XP is older, from when i still had that. I installed windows 7 over the place where windows XP was, which explains why there's a windows 7 loader.

---

### Post by Mark Phelps on 2011-07-19
> **flyingsliverfin said:**
> yea sorry, the grub entry for XP is older, from when i still had that. I installed windows 7 over the place where windows XP was, which explains why there's a windows 7 loader.

But ... the script result shows no Win7 boot loader files (bootmgr and the /boot directory). That's probably why the message "mounting failed" is there.

So, it looks like you've somehow clobbered the Win7 boot loader files.

---

### Post by flyingsliverfin on 2011-07-19
can i fix that from a windows 7 DVD?

how did u decipher that from the script result? :)

"Boot sector type:  Windows Vista/7" doesn't that mean a windows7 MBR is present?

---

### Post by oldfred on 2011-07-19
There is not really much if any difference between any windows boot loaders in the MBR. They all look for a primary partition with the boot flag and jump to that partition to continue to boot. The PBR - partition boot record or first sector of a partition is where Windows had different versions.

Without the mounting we cannot see what files you have. Have you run chkdsk? You can run chkdsk from any windows repairCD,windows full install/bootCD etc.

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. [COLOR=Red]Rerun until no errors.[/COLOR]
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

---

### Post by flyingsliverfin on 2011-07-19
I'll test that tomorrow, im working on something else right now.

Just wonderin: why can't ubuntu mount windows? fdisk recognizes it as ntfs...

error from nautilus:
```
Unable to mount 80 GB Filesystem
Error mounting: mount exited with exit code 2: 
```

EDIT:
interesting, when I [try to] mount the windows hdd w/ the 'mount' command, it does nothing:
```
root@joshua-desktop:/media# mkdir win
root@joshua-desktop:/media# ls
cdrom  data  floppy  floppy0  win
root@joshua-desktop:/media# mount -t auto /dev/sda1 win
root@joshua-desktop:/media# ls
cdrom  data  floppy  floppy0  win
root@joshua-desktop:/media# cd win
root@joshua-desktop:/media/win# ls
root@joshua-desktop:/media/win# cd ..
root@joshua-desktop:/media# ls
cdrom  data  floppy  floppy0  win
root@joshua-desktop:/media# umount /dev/sda1
umount: /dev/sda1: not mounted
root@joshua-desktop:/media# umount win
umount: win: not mounted
root@joshua-desktop:/media# ls
cdrom  data  floppy  floppy0  win
root@joshua-desktop:/media# mount -t ntfs /dev/sda1 win
root@joshua-desktop:/media# ls
cdrom  data  floppy  floppy0  win
root@joshua-desktop:/media# cd win
root@joshua-desktop:/media/win# ls
root@joshua-desktop:/media/win# cd ..

```

---

### Post by oldfred on 2011-07-19
If a NTFS system is damaged and needs chkdsk Ubuntu will not mount it to prevent further damage. As I said in post #4.

---

### Post by flyingsliverfin on 2011-07-21
Wow..... I ran chkdsk C: /r /f... booting into ubuntu. Now it manages to mount the drive, BUT windows is gone! only 80 mb of the drive are being used (of 80 gb)... and the only things there are "/System Volume Information/Chkdsk/[two Chkdsk logs files here]" 

Any options besides reinstalling?

Phew, good thing I had only had that install for 1 day and there wasn't anything important on it...

BTW it's also still giving me that "No boot device available". How would i get it to load grub again?

---

### Post by oldfred on 2011-07-22
I think chkdsk puts info into temp files with chkdsk in the name, But if you have not lost anything then it is not an issue.

Have you change the BIOS ( or one time boot key - f12 on my system) to boot sdb as the grub in that drive looked ok?

---

### Post by flyingsliverfin on 2011-07-22
Hm... haven't found an option in the bios to boot sdb. However, I can totally disable the sda HDD from the BIOS and then magically it finds and loads GRUB! After re-enabling sda (& I also have the boot flag set to sdb1) its still telling me "No Boot device found".

---

### Post by oldfred on 2011-07-22
Is it starting grub or where are you seeing no boot device found, that is usually before grub or windows boot loaders start. Perhaps you have another device in boot order like CD and have a non-bootable CD in drive?

---

### Post by flyingsliverfin on 2011-07-23
Here's what's happening:
I start the computer with both HDD's enabled through the BIOS: it gives me the 'No boot device' error

I disable the windows HDD through the BIOS, then restart, and it loads GRUB seeming as normal...

I'll try shuffling the boot order to put the HDD's first (to exclude anything else) and see if the same thing comes up

---

### Post by oldfred on 2011-07-23
I know one user I was trying to help had a older Dell and its bios would only boot from the first drive. it had an early SATA port but was configured more like the old IDE/PATA where jumpers on the drive set primary master and you only boot from primary master. In his case we just installed grub to the first drive. I normally prefer to have the boot loader in the same drive as the system.

---

### Post by flyingsliverfin on 2011-07-23
What i ended up doing is installing XP again (my brother has the win7 cd and hes away). Now that boots ok, and hopefully I can just do another grub-install and have grub be restored. Later i'll try installing win7 again

---

### Post by flyingsliverfin on 2011-07-31
Im back!
anyway, I've got win7 installed (erased XP again)...

so now to restore GRUB2 i would need to run the command
sudo grub-install --root-directory=/media/ubuntu /dev/sdb?
(from live cd)

also it looks like my BIOS doesn't have an option to boot the second hdd (no options, so maybe i'd just have to change boot flag?), so i'd have to replace the last part with /dev/sda? 

I've had problems a couple years ago as well

---

### Post by zero244 on 2011-07-31
There is a iso file you can download from a program called Super Grub2 Disk.
You can google it.

After you burn the small iso onto a cd you can boot from the cd and it will locate any grub2.cfg files and allow you to get the grub2 menu back and then you can restore it after you boot up.
Just thought I would mention it....it has saved my bacon a couple of times.

Since day one Windows has not played well with others. Windows even today does not support Linux file systems out of the box.

---

### Post by oldfred on 2011-08-01
You have to mount partition before the install command:

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
[COLOR=DarkRed]sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda[/COLOR]
#If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by flyingsliverfin on 2011-08-09
thanks got it all working

---

