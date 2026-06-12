---
title: "GRUB2 won't boot Windows"
date: 2011-01-09
forum: General Help
---

### Post by I&#9829;HTML5 on 2011-01-09
I have a Windows Vista-Ubuntu 11.04 dual-boot. However, I have lost the ability to boot Windows Vista. I can select Windows in the GRUB menu, but GRUB says > error: symbol not found: 'grub_err_printed_errors' I have repeatedly searched Google for any help, but have found nothing that applies to my situation. I need Windows because I have an iPod Touch with a tethered jailbreak and can't use it right now. :(

---

### Post by TeoBigusGeekus on 2011-01-09
There's a [bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/681280") with the same characteristics.

---

### Post by I&#9829;HTML5 on 2011-01-09
Thanks, but I already saw that bug. At the end of that bug, one person states that GRUB could have been installed to their USB drive. However, I ran ```
sudo debconf-show grub-pc
``` and compared my computer's output to the attachment on there, and found they were identical, except that my "install_devices" was different. My "install_devices" was the name of my computer's internal HDD, no doubt about it.

---

### Post by oldfred on 2011-01-09
Run this to see if something looks out of place. Does grub boot Ubuntu ok? Just the windows gives the error?

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by I&#9829;HTML5 on 2011-01-09
Here it is:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 9cem.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 243415888 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,290,079   156,290,017   7 HPFS/NTFS
/dev/sda2         156,291,070   312,580,095   156,289,026   5 Extended
/dev/sda5         156,291,072   306,124,799   149,833,728  83 Linux
/dev/sda6         306,126,848   312,580,095     6,453,248  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        572C8DDF568B4261                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        2b4dd827-075c-47bb-b4b2-fd6299d077d3   ext4                                     
/dev/sda6        76fd8978-b1fd-4278-8108-40770244286e   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /media/572C8DDF568B4261  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 2b4dd827-075c-47bb-b4b2-fd6299d077d3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 2b4dd827-075c-47bb-b4b2-fd6299d077d3
set locale_dir=($root)/boot/grub/locale
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
if [ ${recordfail} != 1 ]; then
  set matches_file=${prefix}/gfxblacklist.lst
  set class_match=3
  if lua ${prefix}/hwmatch.lua; then
    if [ ${match} = 0 ]; then
      set linux_gfx_mode=keep
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=text
  fi
else
  set linux_gfx_mode=text
fi
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.37-7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 2b4dd827-075c-47bb-b4b2-fd6299d077d3
	linux	/boot/vmlinuz-2.6.37-7-generic root=UUID=2b4dd827-075c-47bb-b4b2-fd6299d077d3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.37-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.37-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 2b4dd827-075c-47bb-b4b2-fd6299d077d3
	echo	'Loading Linux 2.6.37-7-generic ...'
	linux	/boot/vmlinuz-2.6.37-7-generic root=UUID=2b4dd827-075c-47bb-b4b2-fd6299d077d3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.37-7-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 2b4dd827-075c-47bb-b4b2-fd6299d077d3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 2b4dd827-075c-47bb-b4b2-fd6299d077d3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 572C8DDF568B4261
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Vista" {
      set root=(hd0,1)
      chainloader +1
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

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
UUID=2b4dd827-075c-47bb-b4b2-fd6299d077d3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=76fd8978-b1fd-4278-8108-40770244286e none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  84.8GB: boot/grub/core.img
  84.8GB: boot/grub/grub.cfg
 113.2GB: boot/initrd.img-2.6.37-7-generic
  84.4GB: boot/vmlinuz-2.6.37-7-generic
 113.2GB: initrd.img
  84.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  4b 9c ca d7 8b 3e 9c 16  90 fe f1 34 a6 83 e3 13  |K....>.....4....|
00000010  b3 9a ec fb be a3 db 7f  35 c5 f8 ca 73 ac b2 0b  |........5...s...|
00000020  46 83 54 cb 28 68 2b 8f  11 96 f1 2f c7 83 df c8  |F.T.(h+..../....|
00000030  d5 94 7a 69 e8 06 ca 8f  05 96 9b 4a ec b4 ba 4e  |..zi.......J...N|
00000040  b3 f4 f7 38 11 a4 15 55  c8 35 6f 20 6f f9 96 fd  |...8...U.5o o...|
00000050  45 ce 3c 59 6d 27 f2 f8  05 aa 0d 26 ad fe 5f 21  |E.<Ym'.....&.._!|
00000060  72 c4 3b eb e6 50 bf dc  b8 35 0a 93 1b 2e 21 09  |r.;..P...5....!.|
00000070  31 37 e3 27 62 71 c6 75  d7 f5 19 0b 46 71 76 4e  |17.'bq.u....FqvN|
00000080  c3 86 68 37 d8 78 37 54  9a 05 b4 9a 25 d2 f5 41  |..h7.x7T....%..A|
00000090  90 88 ac 95 a8 11 44 70  5f b4 96 fc b3 d6 d5 4f  |......Dp_......O|
000000a0  51 e4 b5 dc 6c 0b 10 63  8a 73 99 53 7b c2 ad 84  |Q...l..c.s.S{...|
000000b0  4c df 1b 2c a2 b7 e1 b2  3b d5 1a 76 59 a7 6e 15  |L..,....;..vY.n.|
000000c0  de ad b1 a7 ad 97 f8 61  e1 bb 85 0a db ab 9c 49  |.......a.......I|
000000d0  8d a3 b8 4f d1 e6 d9 7b  04 5f 4a 0e 19 c9 0c f7  |...O...{._J.....|
000000e0  9d 00 9f ed d9 f5 ef 25  d8 d3 b8 72 94 70 5f 40  |.......%...r.p_@|
000000f0  31 59 53 c9 7b 2e 01 37  01 4e 31 57 40 62 70 34  |1YS.{..7.N1W@bp4|
00000100  d6 2e 64 fc c8 53 f8 85  2a 2b e1 a7 13 88 e5 86  |..d..S..*+......|
00000110  f5 60 6f 77 eb d5 fa ef  e9 8c e4 50 c4 b3 92 7f  |.`ow.......P....|
00000120  a2 7d b9 4b af 53 e3 4d  35 b3 4b 96 1d 56 50 9b  |.}.K.S.M5.K..VP.|
00000130  0d 1c 98 ce 86 36 bc 09  2c 16 8c 5a 59 82 ec 58  |.....6..,..ZY..X|
00000140  5e 76 a8 6c a0 45 f9 5f  2c c8 1f 05 39 d9 d1 77  |^v.l.E._,...9..w|
00000150  c4 04 d6 97 13 ea c3 fa  ed 75 61 5c 69 59 d0 2c  |.........ua\iY.,|
00000160  f9 6b 75 ce f4 84 c8 08  ff a5 f2 86 b5 5a d7 8b  |.ku..........Z..|
00000170  b2 3c c6 4d e6 a9 c7 a0  a1 66 d1 75 1a d6 82 e1  |.<.M.....f.u....|
00000180  2f 1c 72 24 50 f4 3c 28  02 ef 67 d9 90 10 9b 19  |/.r$P.<(..g.....|
00000190  43 aa 6c d6 38 8e dc 22  26 7b 2a 61 ae 65 2c 09  |C.l.8.."&{*a.e,.|
000001a0  e0 31 6c 70 70 ca 23 11  fa d6 f7 8e 6d ed 66 87  |.1lpp.#.....m.f.|
000001b0  0e 3d 7c b1 62 d7 1a a9  dc 18 33 8a b0 11 00 fe  |.=|.b.....3.....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 48 ee 08 00 fe  |...........H....|
000001d0  ff ff 05 fe ff ff 02 48  ee 08 00 80 62 00 00 00  |.......H....b...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

GRUB boots Ubuntu perfectly fine, but Windows gives an error.

---

### Post by efflandt on 2011-01-09
The correct forum for Natty until it is released is [http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

How did grub2 end up in the boot sector of sda1 partition?  I have see people in that situation, but not sure why or what they did to fix it.  Do you or did you have a Wubi install?

I guess the boot info script is not really up to speed on the grub version used for Natty because mine works fine for Win7 or Maverick on sda or Natty on sdb booting from sdb with:

 => Grub 2 is installed in the MBR of /dev/sdb and looks for |e.

---

### Post by wilee-nilee on 2011-01-09
Same question or point as last post.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type: ** Grub 2**
    **Boot sector info:  Grub 2 is installed in the boot sector of sda1 and **
                       looks at sector 243415888 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

Use this link to remove.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by I&#9829;HTML5 on 2011-01-10
Many replies:[LIST]
[*]No, I have not ever used Wubi on this computer.
[*]I followed the instructions on the page you linked to, but there was no BackupBS button. Any suggestions?
[*]Thanks for the help so far :)
[/LIST]

---

### Post by I&#9829;HTML5 on 2011-01-12
Thanks for trying to help, but I have made my final decision: I am going to completely reformat my hard drive, install Ubuntu 10.10, and then install Windows in Virtualbox. Wish me luck!

---

