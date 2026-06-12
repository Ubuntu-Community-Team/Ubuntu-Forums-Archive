---
title: "Error loading operating system. [Can I salvage my files?]"
date: 2010-10-13
forum: General Help
---

### Post by Axlswe on 2010-10-13
[SOLVED:]I solved it myself by following the information on:
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)

Greetings.

I just managed to majorly mess up my laptop and I, ofcourse, did this after a full day of writing an essay and no file backup.

What happened was that I suddenly got this bright idea to install xp on that /windows partition I made when installing Ubuntu (10,10). Suffice to say that windows would have nothing to do with my partition and thus I deleted(through windows installer on CD) it for the windows installer to repartition. Well that didn't work either, so after giving up trying I restarted my computer to boot back in to Ubuntu, right?

Wrong... The nice message in topic greeted me with a smile and now I'm clueless  what to do to salvage my files. I tried to boot ubuntu through a CD I made but that didn't give me access to the folder that I needed.

Any thoughts on how to fix this, or atleast salvage my work?

Thanks in advance!

[Edit:] I got another computer with ubuntu on if that helps in any way.

---

### Post by Axlswe on 2010-10-13
Is it perhaps possible to switch to root/admin from the Ubuntu CD "Try Ubuntu" option?

[Edit:] Ran a boot info script, results:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

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

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   126,953,471   126,951,424  83 Linux
/dev/sda2         126,955,518   156,301,311    29,345,794   5 Extended
/dev/sda5         126,955,520   130,859,007     3,903,488  82 Linux swap / Solaris
/dev/sda6         130,865,553   156,296,384    25,430,832   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2021 MB, 2021654528 bytes
255 heads, 63 sectors/track, 245 cylinders, total 3948544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     3,935,924     3,935,862   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        757161cd-e615-420b-aefe-88b939111a90   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        a52d68e3-97c2-4f2b-9423-8a65272e933b   swap                                     
/dev/sda6        5B79249D3F388563                       ntfs       Windows                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6C88-8ED3                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


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
search --no-floppy --fs-uuid --set 757161cd-e615-420b-aefe-88b939111a90
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 757161cd-e615-420b-aefe-88b939111a90
set locale_dir=($root)/boot/grub/locale
set lang=sv
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 757161cd-e615-420b-aefe-88b939111a90
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=757161cd-e615-420b-aefe-88b939111a90 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 757161cd-e615-420b-aefe-88b939111a90
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=757161cd-e615-420b-aefe-88b939111a90 ro single 
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
	search --no-floppy --fs-uuid --set 757161cd-e615-420b-aefe-88b939111a90
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 757161cd-e615-420b-aefe-88b939111a90
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
# /windows was on /dev/sda6 during installation
UUID=69E5-EA1C  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
UUID=a52d68e3-97c2-4f2b-9423-8a65272e933b none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.2GB: boot/grub/core.img
  45.2GB: boot/grub/grub.cfg
  20.0GB: boot/initrd.img-2.6.35-22-generic
    .3GB: boot/vmlinuz-2.6.35-22-generic
  20.0GB: initrd.img
    .3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  b6 42 72 aa 35 5d 95 2f  4e 81 29 40 6b 22 33 5a  |.Br.5]./N.)@k"3Z|
00000010  23 34 5a 1e 2d 50 1e 2c  4f 20 30 52 1f 2f 51 1f  |#4Z.-P.,O 0R./Q.|
00000020  2e 5b 1d 2b 5b 27 3c 68  28 3d 67 28 3d 66 28 3d  |.[.+['<h(=g(=f(=|
00000030  66 29 3e 67 2a 41 6a 29  41 6a 2b 42 6e 2b 45 74  |f)>g*Aj)Aj+Bn+Et|
00000040  2b 48 7e 2e 4f 88 2e 51  8c 2b 4e 89 2d 4f 8b 2d  |+H~.O..Q.+N.-O.-|
00000050  4f 88 2e 51 8b 2c 52 8e  26 41 79 1d 2d 72 21 38  |O..Q.,R.&Ay.-r!8|
00000060  9a 21 37 9c 22 3a 9d 25  42 84 27 45 7d 27 42 7a  |.!7.":.%B.'E}'Bz|
00000070  26 3f 77 24 3c 73 25 3e  76 25 3f 77 24 3c 6f 21  |&?w$<s%>v%?w$<o!|
00000080  34 60 20 33 5c 20 33 5c  20 32 59 1f 2f 53 1d 2c  |4` 3\ 3\ 2Y./S.,|
00000090  51 19 25 48 19 25 59 1e  2c 78 1c 29 69 12 1d 3a  |Q.%H.%Y.,x.)i..:|
000000a0  15 21 3f 18 26 46 1b 2b  4c 1d 2e 51 1e 2e 51 1f  |.!?.&F.+L..Q..Q.|
000000b0  2f 54 1e 2f 52 1f 32 53  20 33 57 20 31 56 20 33  |/T./R.2S 3W 1V 3|
000000c0  57 21 34 58 1d 2f 52 1b  2b 4d 19 28 49 1b 29 4d  |W!4X./R.+M.(I.)M|
000000d0  1d 2e 53 20 32 59 21 34  5d 24 39 64 25 3c 67 24  |..S 2Y!4]$9d%<g$|
000000e0  3b 66 2a 44 74 32 54 89  40 6b a1 4d 80 b8 5d 94  |;f*Dt2T.@k.M..].|
000000f0  c9 6c a3 d3 74 a9 d7 83  b3 dc 80 b3 dd 85 b7 de  |.l..t...........|
00000100  8c ba e0 98 c2 e4 95 c1  e3 a0 c7 e6 a9 c8 e5 bc  |................|
00000110  ca d9 cc cc cd d7 cc c1  dd cd bc df cc b6 e0 cb  |................|
00000120  b3 e1 cc b4 e0 cb b2 df  cb b3 df cc b4 e0 cd b5  |................|
00000130  e2 ce b7 e1 cd b5 e1 cd  b4 e2 d0 ba e6 d5 c1 e7  |................|
00000140  da c8 e7 d8 c5 e4 d1 b9  e2 cf b6 e3 cf b7 e2 cf  |................|
00000150  b6 e3 cf b7 cb ca c9 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000180  00 1f 1f 1f ec ec eb ec  ec eb ec ec eb 6e 6e 6e  |.............nnn|
00000190  00 00 00 bd bd bc ec ec  eb ec ec eb 8e 8e 8d 00  |................|
000001a0  00 00 6e 6e 6e ec ec eb  dc dc db ec ec eb ec ec  |..nnn...........|
000001b0  eb bd bd bc ec ec eb ec  ec eb 6e 6e 6e 00 00 fe  |..........nnn...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 90 3b 00 00 fe  |............;...|
000001d0  ff ff 05 fe ff ff 54 a9  3b 00 6f 0b 84 01 00 00  |......T.;.o.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by Axlswe on 2010-10-13
Apparently it thinks windows is mixed in on this (though I do not have any windows installation).

I tried the following command:
sudo grub-install --root-directory=/mnt/ /dev/sda

in a valiant effort to somehow make it disappear (I have no idea what I'm doing but I got the idea from a similar thread.)

got the answer:
/usr/sbin/grub-probe: error: cannot find a device for /mnt//boot/grub (is /dev mounted?).

and my hard drive (with ubuntu) is mounted. Ideas?

[Edit:] I managed to salvage my essay through the gksu nautilus command, so that is no longer an issue. So what I'm looking for now is a way to make my ubuntu installation work properly again.

---

### Post by Quackers on 2010-10-13
I suspect you need to re-install grub to sda.
It is possible to chroot into your installed system while working from the Live CD desktop.
I think all the details you require are in this guide by drs305.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Axlswe on 2010-10-13
Thanks, that was the problem. I manage to sort it out before I saw your post but thanks anyway!

---

### Post by Quackers on 2010-10-13
Glad to see you've got things sorted. Very nice :-)

---

### Post by Axlswe on 2010-10-13
Thanks, hehe yeah got me worried there for a while. Now I need to find out how to install XP on a partition without messing it up. ;)

---

