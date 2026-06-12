---
title: "Adding windows 7 to GRUB -- Can't autodetect and a manual addition wont boot"
date: 2011-08-22
forum: General Help
---

### Post by camerong on 2011-08-22
I've tried everything I've found in over 10 pages of other threads, and have fiddled/ran boot-repair.

[http://paste.ubuntu.com/672420/](http://paste.ubuntu.com/672420/) 

When I tried to add it manually (I was unsure of X in (hd0,x)) I got a "signature error" message when booting.

Any help would be greatly appreciated.

---

### Post by seawolf167 on 2011-08-22
You tried the process listed [here]("https://help.ubuntu.com/community/Grub2/#Reinstalling%20GRUB2")? What is the exact error you get when attempting to boot your computer?

---

### Post by camerong on 2011-08-22
The error is only a few words long. It says, "signature read error"

Also, in the advanced options of grub-repair, only "Ubuntu (the current OS)" is ever listed as an option. It cannot find/recognize Windows.

---

### Post by raja.genupula on 2011-08-22
edit your grub.cfg in /boot/grub by using any editer with sudo 
then 

do this 
  _Windows system on the first partition of the first hard disk_

```
menuentry "Windows" {
	insmod chain
	insmod ntfs
	set root=(hd0,1)
	chainloader +1
}
```

paste it in the grub.cfg file

---

### Post by raja.genupula on 2011-08-22
> **camerong said:**
> The error is only a few words long. It says, "signature read error"

Also, in the advanced options of grub-repair, only "Ubuntu (the current OS)" is ever listed as an option. It cannot find/recognize Windows.

what you're getting for this

```
sudo os-prober
```

---

### Post by seawolf167 on 2011-08-22
I'm afraid I haven't ever heard of a "Signature read error" before. Hopefully someone else can help with that. 

As for the boot-repair tool, just use the default Ubuntu option, then when you are able to boot, open a terminal and type in

```
sudo update-grub
```

to find your other installations. You *may* need to get

```
sudo apt-get install os-prober
```

first in order to have it detect Windows.

---

### Post by Quackers on 2011-08-22
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by camerong on 2011-08-22
Before I proceed with the rest of the suggestions, here is proof that os-prober/etc cannot find my Windows partition:


```
cameron@Studio-1440:~$ sudo apt-get install os-prober
[sudo] password for cameron: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
os-prober is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 213 not upgraded.
cameron@Studio-1440:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

Fruther, I have taken Raja's suggestion and gotten a potentially interesting error. The config file which I was recommended to edit is not supposed to be edited so I added the function (same code) and then rebuilt the config...

```

cameron@Studio-1440:~$ sudo nano /etc/grub.d/11_Windows (AND THEN PASTED AND SAVED)
cameron@Studio-1440:~$ sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
/etc/grub.d/11_Windows: 1: menuentry: not found
insmod: can't read 'chain': No such file or directory
insmod: can't read 'ntfs': No such file or directory
/etc/grub.d/11_Windows: 4: Syntax error: "(" unexpected

```

---

### Post by Quackers on 2011-08-22
The boot script output should give details of where everything is and what's gone wrong.

---

### Post by camerong on 2011-08-22
I have run the boot info script. The results are below. (I DID NOT BOOT TO A LIVE CD TO DO THIS. IF THIS IS ABSOLUTELY NEEDED LET ME KNOW)

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *     30,801,920   383,628,349   352,826,430   7 NTFS / exFAT / HPFS
/dev/sda3         383,629,312   488,392,703   104,763,392  83 Linux
/dev/sda4              81,918    30,801,919    30,720,002   5 Extended
/dev/sda5              81,920    30,801,919    30,720,000  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda3        1d2dada0-a494-4c5f-b164-364d1437bcf4   ext4       
/dev/sda5        034248cf-4c40-48ec-ba4f-0dd93a84d17e   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root 1d2dada0-a494-4c5f-b164-364d1437bcf4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root 1d2dada0-a494-4c5f-b164-364d1437bcf4
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
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 1d2dada0-a494-4c5f-b164-364d1437bcf4
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=1d2dada0-a494-4c5f-b164-364d1437bcf4 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 1d2dada0-a494-4c5f-b164-364d1437bcf4
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=1d2dada0-a494-4c5f-b164-364d1437bcf4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 1d2dada0-a494-4c5f-b164-364d1437bcf4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 1d2dada0-a494-4c5f-b164-364d1437bcf4
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
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=1d2dada0-a494-4c5f-b164-364d1437bcf4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=034248cf-4c40-48ec-ba4f-0dd93a84d17e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 229.064743042 = 245.956395008  boot/grub/core.img                             1
 229.083003998 = 245.976002560  boot/grub/grub.cfg                             1
 185.359451294 = 199.028195328  boot/initrd.img-2.6.38-8-generic               3
 229.061527252 = 245.952942080  boot/vmlinuz-2.6.38-8-generic                  1
 185.359451294 = 199.028195328  initrd.img                                     3
 229.061527252 = 245.952942080  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  bf d0 d0 0b d3 ac 9f 92  64 23 5d 10 84 42 ec 45  |........d#]..B.E|
00000010  0e 3b 32 3c 60 a2 60 73  67 7e d2 17 ea 32 ca 7a  |.;2<`.`sg~...2.z|
00000020  1a 98 85 1f 32 7d 67 f7  3e 51 c0 b6 8e 16 54 99  |....2}g.>Q....T.|
00000030  05 07 84 26 44 be 59 e4  22 99 9b d9 38 11 f8 7b  |...&D.Y."...8..{|
00000040  80 6e 7d 35 6f 45 24 fa  c4 54 5f cb db e6 e3 d7  |.n}5oE$..T_.....|
00000050  3a 4f ae 17 d1 c8 57 ed  f9 64 3b 56 ae 81 fa 6f  |:O....W..d;V...o|
00000060  42 bc 49 64 8f 70 7c bf  40 d6 37 4f c9 24 78 5f  |B.Id.p|.@.7O.$x_|
00000070  33 8a c3 4a db 05 35 25  2b 1a 8a 48 8a cd 3d 68  |3..J..5%+..H..=h|
00000080  cf 41 13 32 0c b6 7d 19  22 3f 5c ab 82 35 bb 93  |.A.2..}."?\..5..|
00000090  39 e6 37 f2 8c 58 47 06  98 45 97 ec 94 8b 4b 57  |9.7..XG..E....KW|
000000a0  5a 92 ee a4 76 fe 2d c7  62 79 39 d5 36 64 30 99  |Z...v.-.by9.6d0.|
000000b0  1c 71 30 13 ee 35 98 44  06 e3 f2 44 ef 5b 84 1a  |.q0..5.D...D.[..|
000000c0  dc a1 f9 72 61 0b 1e b2  f4 f3 2a 73 c2 5b 49 1b  |...ra.....*s.[I.|
000000d0  70 ea 2d 57 a2 53 05 89  8b 71 2d 0b dd 2c 78 21  |p.-W.S...q-..,x!|
000000e0  e4 b2 c0 72 e5 52 de 55  ee 48 1f bc f3 c5 12 20  |...r.R.U.H..... |
000000f0  9f 57 c5 f6 67 d3 8f c2  0f 2e b3 0a d9 44 6b 02  |.W..g........Dk.|
00000100  b4 ec cd c0 cc 64 0f 71  2f c4 5b 8d 59 fa 54 0d  |.....d.q/.[.Y.T.|
00000110  d0 ac dc fe eb 88 b7 6d  dd 93 02 99 3a ea e0 3a  |.......m....:..:|
00000120  8b 8c a5 be 57 b8 44 65  9c e4 7b 06 a6 eb 7b 12  |....W.De..{...{.|
00000130  31 7e f4 4d 25 94 16 90  ee 8c d4 fa b1 80 76 ad  |1~.M%.........v.|
00000140  bf 5c 55 b2 00 ef a4 a6  a9 3a f4 53 ba 75 9d 0f  |.\U......:.S.u..|
00000150  e4 25 b0 78 0f 72 f7 d0  e1 83 86 12 6e 8e 53 c8  |.%.x.r......n.S.|
00000160  d8 99 fb 15 67 7e 05 f3  40 25 6e 06 97 83 f6 26  |....g~..@%n....&|
00000170  74 f2 a5 a9 e2 1b 62 5c  00 74 38 7c 04 51 a4 62  |t.....b\.t8|.Q.b|
00000180  44 0a c8 30 52 a6 0d 76  3c d7 a4 3b 09 ae f4 cb  |D..0R..v<..;....|
00000190  4a d5 a5 dd 64 45 89 9f  2c 56 9b 43 be b7 3d 51  |J...dE..,V.C..=Q|
000001a0  9a de 34 35 d9 42 6d 04  5c 2e 33 32 7f 8a e4 cc  |..45.Bm.\.32....|
000001b0  92 2b 3f c9 2a b3 23 40  54 bc d7 fc 35 ef 6d 6e  |.+?.*.#@T...5.mn|
000001c0  7b 3a e0 cd a7 3f 04 2e  1f af ae 31 35 b8 00 e1  |{:...?.....15...|
000001d0  9c 65 2b 94 21 8e 74 4f  72 75 17 cf ee 7e 2d 1e  |.e+.!.tOru...~-.|
000001e0  fc 2f b3 70 d2 25 e9 79  25 02 54 7c be 14 e9 5d  |./.p.%.y%.T|...]|
000001f0  92 54 a5 fb 9c 05 28 af  0c 83 e7 62 89 b5 7b fc  |.T....(....b..{.|
00000200

Unknown BootLoader on sda2

00000000  3f b2 6b a6 0b 4c cf 34  73 cd 1a 9b 6b 87 43 19  |?.k..L.4s...k.C.|
00000010  db cf 20 98 45 f8 a8 75  22 67 ed c8 ec ea 2d b5  |.. .E..u"g....-.|
00000020  af 26 70 29 d9 eb 0e 10  e6 ef 04 a0 4a 3d b5 59  |.&p)........J=.Y|
00000030  57 3d f1 25 b5 e2 55 cf  9b a3 9e ec 48 29 a0 74  |W=.%..U.....H).t|
00000040  a3 1b c8 29 cb 68 44 06  ed 52 f3 08 bf 7e f0 12  |...).hD..R...~..|
00000050  99 46 87 4b 6a ea a3 d6  cd 2e ae 5a 0d d9 48 e5  |.F.Kj......Z..H.|
00000060  58 08 26 50 69 87 d5 4e  93 49 2d 47 41 6c c1 d1  |X.&Pi..N.I-GAl..|
00000070  4d b6 6a 23 f7 20 cf 73  97 2e 21 45 bf 5f 17 37  |M.j#. .s..!E._.7|
00000080  e6 ec 31 f2 a1 c0 82 f2  41 7f a3 a5 d7 8f 08 79  |..1.....A......y|
00000090  ff 45 6f 0a fe 0e c3 fe  f9 e7 f6 c9 74 1b d7 1c  |.Eo.........t...|
000000a0  a7 01 aa 19 ff 04 d7 5e  f5 cf b9 8c 54 bd bc 04  |.......^....T...|
000000b0  9e 88 4a 72 8d 51 ef 7c  ae 6b 0a 85 4d 14 f1 5d  |..Jr.Q.|.k..M..]|
000000c0  6f 35 36 a5 75 b8 d9 94  cc 16 12 94 31 3e 68 a4  |o56.u.......1>h.|
000000d0  d1 1e 57 4f 67 a3 99 fd  25 02 67 3e 7d 3d 15 79  |..WOg...%.g>}=.y|
000000e0  d9 ba 15 5c a7 6e 58 9b  15 ad a7 b9 47 35 19 0e  |...\.nX.....G5..|
000000f0  d2 fd 8d 06 b2 d6 9b 20  37 f2 b6 fa 5a 61 f0 72  |....... 7...Za.r|
00000100  dc f8 fa 14 7b b7 c1 4d  ae ee 97 b3 cb 13 65 2a  |....{..M......e*|
00000110  57 41 23 7d 5d a2 10 4e  d6 f8 6c e5 bb 86 c0 13  |WA#}]..N..l.....|
00000120  42 fe 5c b2 ca 62 23 18  17 0a a3 25 e8 98 b8 41  |B.\..b#....%...A|
00000130  62 71 37 32 19 c2 d3 1d  ed 90 1d 84 2a f0 4f ab  |bq72........*.O.|
00000140  26 c7 e5 a3 fc a6 84 c0  c9 e8 5c 92 17 0d 3e 90  |&.........\...>.|
00000150  1e dc d5 4d 93 1f 37 88  f1 96 39 e1 e5 91 1f 36  |...M..7...9....6|
00000160  6f bb 2a bf ed 24 03 43  b0 5a 0f 87 0f 77 44 f6  |o.*..$.C.Z...wD.|
00000170  4d b3 64 3f 82 75 24 7f  bb 3b 12 df 1d 7e 01 1b  |M.d?.u$..;...~..|
00000180  83 73 28 d0 6e be 9d 73  6d 7b 14 a1 3e 24 46 09  |.s(.n..sm{..>$F.|
00000190  dd d1 bc 6c 4e 82 5f 35  af 09 5c 1d 22 4c b7 8f  |...lN._5..\."L..|
000001a0  7c 1e a4 34 fe 64 56 e5  d7 75 f3 0c 7e 28 7c 35  ||..4.dV..u..~(|5|
000001b0  00 ba 3c ed bf 55 38 f3  4c 46 6f 4f ba 45 23 b5  |..<..U8.LFoO.E#.|
000001c0  c3 e5 58 56 44 2c c6 7c  97 5f 20 10 30 9f 75 00  |..XVD,.|._ .0.u.|
000001d0  dc 08 7a 45 97 c6 eb 42  03 70 b8 2d ed ea 0e 30  |..zE...B.p.-...0|
000001e0  68 23 2a 3a 72 66 2a 5e  e9 b1 8c 4c 3b 8d dc 13  |h#*:rf*^...L;...|
000001f0  df ff 9c 9c 04 47 48 ec  22 4b d7 27 ea 4c 8c bc  |.....GH."K.'.L..|
00000200

Unknown BootLoader on sda4

00000000  0e 8d 61 2b 92 60 67 0e  5c 0a 60 0d a1 b8 d7 8c  |..a+.`g.\.`.....|
00000010  14 eb e6 9a 51 ed e6 a6  1f d5 d4 51 5c 71 04 2f  |....Q......Q\q./|
00000020  a6 d0 fe b0 01 f1 3a bd  2e 27 a0 f6 50 55 7e 42  |......:..'..PU~B|
00000030  40 3d be 6e 28 db cb f5  ed de 51 7d 23 b5 8e d8  |@=.n(.....Q}#...|
00000040  e1 c2 31 25 e7 57 7b 0f  d8 5a 98 5a a0 af 42 b7  |..1%.W{..Z.Z..B.|
00000050  e9 48 be ad 89 5b 51 e3  6f 0a c9 e3 84 f9 3e 21  |.H...[Q.o.....>!|
00000060  60 2b 8c 74 ec 29 90 b7  e7 c3 f0 48 4b e8 85 1f  |`+.t.).....HK...|
00000070  e1 3e 7c e0 2b 7b 60 1b  9c 0b 7a 4f ee cd e4 ec  |.>|.+{`...zO....|
00000080  f1 f3 69 92 6f 54 82 e8  e9 c7 86 f8 f9 73 bb 1a  |..i.oT.......s..|
00000090  66 0e bd 7b 32 42 6f c5  63 6a 23 40 9b 5d 41 60  |f..{2Bo.cj#@.]A`|
000000a0  ee df ca b7 2e 0c f1 c6  d7 90 7f c8 95 bb 00 3c  |...............<|
000000b0  db cf 92 03 27 93 1f d0  2f 79 80 56 36 83 14 bd  |....'.../y.V6...|
000000c0  78 20 f6 f3 d4 25 c7 40  4b 8b 17 19 cc 14 51 98  |x ...%.@K.....Q.|
000000d0  d6 19 a2 4d be c4 d2 30  61 ce 9c fa df e5 21 00  |...M...0a.....!.|
000000e0  cf cf ab 95 58 c2 2a e2  f6 47 8f 0e 24 14 0e fc  |....X.*..G..$...|
000000f0  28 fa be 00 e5 54 57 d4  a1 aa 3a 24 2d 2f c3 74  |(....TW...:$-/.t|
00000100  5c 48 5c a1 7f d5 7d 20  15 de d7 3c 3f 71 67 cb  |\H\...} ...<?qg.|
00000110  c2 04 8a 1a 6c c8 e0 c6  c8 5c f9 a6 8b 24 3f 74  |....l....\...$?t|
00000120  7f 1a 11 8c d1 2a 42 29  4f 6f aa be 14 b2 0f bf  |.....*B)Oo......|
00000130  7a f4 0a ed 5f a0 ea 63  5e 83 08 51 0c 50 c2 a3  |z..._..c^..Q.P..|
00000140  41 15 38 fd 4a 47 66 74  63 7c 37 17 09 18 f2 dd  |A.8.JGftc|7.....|
00000150  8a 1e 87 ef 3d 55 e5 7e  4b c3 20 73 48 fb 82 81  |....=U.~K. sH...|
00000160  8d 0d 67 e9 43 4c 0c dd  7b 64 51 cd 2d da 5b e9  |..g.CL..{dQ.-.[.|
00000170  ba 82 9c 5d 4c 77 2b ea  d7 78 90 3c 74 e4 bc f7  |...]Lw+..x.<t...|
00000180  61 93 4e db 51 49 b3 81  e3 b0 3d 22 82 eb 0b 21  |a.N.QI....="...!|
00000190  7c 93 0b 8b f1 74 22 68  2b 48 13 9a a0 c7 44 c3  ||....t"h+H....D.|
000001a0  aa 57 99 0a 3b 5f 62 a5  38 33 3b 73 dc 9e 3a d7  |.W..;_b.83;s..:.|
000001b0  7e 46 66 9c bd 3d 7a 07  5f d2 63 2e ff ab 00 19  |~Ff..=z._.c.....|
000001c0  15 05 82 fe ff ff 02 00  00 00 00 c0 d4 01 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

I greatly appreciate your help.

---

### Post by Quackers on 2011-08-22
Thanks.
Before installing Ubuntu did you resize any partitions or delete any? If so, with what programme?

---

### Post by raja.genupula on 2011-08-22
> **camerong said:**
> Before I proceed with the rest of the suggestions, here is proof that os-prober/etc cannot find my Windows partition:


```
cameron@Studio-1440:~$ sudo apt-get install os-prober
[sudo] password for cameron: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
os-prober is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 213 not upgraded.
cameron@Studio-1440:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

Fruther, I have taken Raja's suggestion and gotten a potentially interesting error. The config file which I was recommended to edit is not supposed to be edited so I added the function (same code) and then rebuilt the config...

```

cameron@Studio-1440:~$ sudo nano /etc/grub.d/11_Windows (AND THEN PASTED AND SAVED)
cameron@Studio-1440:~$ sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
/etc/grub.d/11_Windows: 1: menuentry: not found
insmod: can't read 'chain': No such file or directory
insmod: can't read 'ntfs': No such file or directory
/etc/grub.d/11_Windows: 4: Syntax error: "(" unexpected

```

can you paste here your grub.cfg file

---

### Post by Quackers on 2011-08-22
The grub.cfg contents are listed in the boot script output.

---

### Post by camerong on 2011-08-22
I used Acronis Disk Manager (?) to create the new Ubuntu Partition. I may have re-sized the windows partition but I do not believe that I did.

EDIT: to clarify: I believe that I had the 50gb for my Ubuntu install already free due to the fact that I also used to have Ubuntu installed.

---

### Post by Quackers on 2011-08-22
Sorry, I missed your reply.
Windows Vista and Windows 7 do not like to be resized by anything other than Windows Disk Management console and should always be defragmented first. I realise that you're not sure whether you did that or not.
The point is that your first 2 partitions (dell utility and what is probably your Windows partition) are not decipherable by Ubuntu.
This can mean that a chkdsk needs to be run.
Do you have a Windows installation disc or a repair disc (NOT a recovery dvd)?

---

### Post by oldfred on 2011-08-22
At the end of the boot script it shows the PBRs for sda1 & sda2 which just look like random data. Not sure what Dell's looks like, but the NTFS partition has to have a NTFS signature or boot sector that is NTFS. 

If partition was moved then backup will not be valid. But it has to have .R.NTFS at the beginning and some code with 055aa at the end.

  Attachedtestdisk output to show my NTFS which is still XP but the first part is the same for XP & Vista/7. One difference is just which file is used to continue booting.

You may have to run fixBoot and chkdsk several times to clean up the partition boot sector.

oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)

Edit - another thought.
Since the boot sector is so corrupt, it may pay to use testdisk to create a "basic" NTFS partition (Rebuild BS shown in my attachedment at bottom). That probably will not create a bootable boot sector, but then it may be valid enough for windows to see it and repair it.

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)



@Quackers
yannubuntu's repair program copies the results.txt to pastebin which was in the first post. His program will do many repairs but cannot fix this type of problem as I think only windows programs will.

---

### Post by camerong on 2011-08-22
Again, I greatly appreciate the help.

I do not have a win7 CD (**nor do I have a CD drive**) so I extracted a win7 ISO to a usb drive and attempted to boot with it but it said "disk error." and then just went to the HD/ubuntu.

I will continue to work at this in the meantime but:

Is there any easier way to simply extract data from the partition? I would be very happy to simply wipe + reinstall windows except I need certain data from it.

Thanks,

Cameron

---

### Post by oldfred on 2011-08-22
If you rebuild the NTFS partition boot sector with testdisk from Ubuntu, you may then be able to mount it. But if the chkdsk flag gets set it will not let you mount it to prevent further damage that then chkdsk could not fix. I think you can force mount it, but it still is better to get a working repair USB to fix it.

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

More links to testdisk, it is in Ubuntu's repository, so you can easily download it.
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by Jose Catre-Vandis on 2011-08-22
Having similar problems after removing two partitions from my logical partition and resizing my main xubuntu 11.04 (sda8), with Windows 7 on sda2 (and W7 recovery on sda1), and a 10.10 xubuntu on sda5. Had to use the Boot Repair tool with a live cd to get grub up and running but grub is not finding either the W7 or 10.10.

If I run os-prober it shows that they are there, ```
/dev/sda1:Windows Recovery Environment (loader):Windows:chain
/dev/sda2:Windows 7 (loader):Windows1:chain
/dev/sda5:Ubuntu 10.10 (10.10):Ubuntu:linux
```but update-grub only finds the 11.04 installation and kernel updates.

I tried reinstalling grub but I get a Flexnet on Sector 51 error (which I understand shouldn't get in the way?)

W7 will boot using a stock entry in grub.cfg, and no I didn't resize W7 partitions (learnt the hard way a while ago ;))

Any tips or pointers?

---

### Post by camerong on 2011-08-23
Updates:

I ran chkdsk + scandisk - no issues.
Ran through all the commands for the windows 7 repair CD despite it not being able to find my Windows partition.

Now I can't even boot into Linux because it "repaired" my boot and it just gives an error and says, "Hit ctrl+alt+del to restart."

New information that I forgot: **_My windows partition was/is encrypted by TrueCrypt_**

I'm attempting TestDisk recovery now.

---

### Post by oldfred on 2011-08-23
Truecrypt changes everything. I usually try to avoid that issue as I do not know much about encryption, but as I understand it, it has to have it controling MBR and entering password to unencrypt everything. It is not compatible with dual boots. I do not think test disk will then help.

With encryption you have to have good backups as usually any system issue with encryption is then not easily repaired.

@Jose Catre-Vandi
Please start a new thread and post the boot script or the link that boot repair gave you to your copy of boot script.If you have not rebooted /tmp/clean or /var/log/clean have the boot-repair info and a copy of results.txt.
Edit - Most of the info I know on dynamic repair is in this thread among others:
[http://ubuntuforums.org/showthread.php?t=1825567](http://ubuntuforums.org/showthread.php?t=1825567)

---

### Post by camerong on 2011-08-23
As I did not create a recovery disk as prompted, there seems to be no way to recover the boot loader/data. I'm going to wipe the HD and start fresh.

Live and learn.

---

### Post by Jose Catre-Vandis on 2011-08-23
Apologies for crashing the party ;)

---

