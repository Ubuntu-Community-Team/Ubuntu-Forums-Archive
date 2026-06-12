---
title: "ubuntu loads straight away"
date: 2010-10-12
forum: General Help
---

### Post by tralph on 2010-10-12
I just installed ubuntu netbook remix onto my acer aspire 1. Before installing I had windows xp installed. Once ubuntu  was installed it now loads straight away rather than giving me an option to boot windows.
i did not format the drive when i installed ubuntu and i asked it to install "side by side"
does anyone know why this would happen?

ty for any advice given

---

### Post by Quackers on 2010-10-12
Welcome to UbuntuForums.
Try opening a terminal and typing sudo update-grub.
It will ask for your password and then configure grub.cfg
Watch to see if your XP installation is included.
You may need to re-install your windows bootloader from your Windows repair cd.
If you need help with anything just ask again.

---

### Post by tralph on 2010-10-13
thanks alot for your reply, i will try this as soon as i get home :)

---

### Post by tralph on 2010-10-13
i i tried this but when i put in configure grub.cfg i get the message configure: command not found.

any ideas?

---

### Post by Quackers on 2010-10-13
In the terminal type
sudo update-grub
then hit enter then watch as grub.cfg is configured to see if the windows loader is detected.
Don't repair the windows bootloader at this stage.

---

### Post by tralph on 2010-10-13
this is what i get

tralph@tralph-laptop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done

---

### Post by Quackers on 2010-10-13
Ok, can you go to the site below and download the boot script file to your desktop then run the command shown on the same site. This will produce a results.txt file on your desktop. Please copy the contents of that file between code tags in your next post (click on New Reply rather than quick reply and click on the # symbol in the tool bar to get the code tags)

oops forgot the link
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by tralph on 2010-10-13
ok cool i cant see a link though :)

---

### Post by Quackers on 2010-10-13
Lol, look again. I just edited it. Sorry :-)

---

### Post by tralph on 2010-10-13
results below

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

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

/dev/sda1    *          2,048   303,603,711   303,601,664  83 Linux
/dev/sda2         303,605,758   312,580,095     8,974,338   5 Extended
/dev/sda5         303,605,760   305,474,394     1,868,635  82 Linux swap / Solaris
/dev/sda6         305,475,584   312,152,063     6,676,480  83 Linux
/dev/sda7         312,154,112   312,580,095       425,984  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2: PTTYPE="dos" 
/dev/sda5        111fa77f-62b3-459a-ba9e-f4c2e29efc0b   swap                                     
/dev/sda6        654d5763-783d-4bf9-b11d-13da50a61c82   ext4                                     
/dev/sda7        f842efcc-85ce-466d-a1ef-fefa77cbd044   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 654d5763-783d-4bf9-b11d-13da50a61c82
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 654d5763-783d-4bf9-b11d-13da50a61c82
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 654d5763-783d-4bf9-b11d-13da50a61c82
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=654d5763-783d-4bf9-b11d-13da50a61c82 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 654d5763-783d-4bf9-b11d-13da50a61c82
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=654d5763-783d-4bf9-b11d-13da50a61c82 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 654d5763-783d-4bf9-b11d-13da50a61c82
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=654d5763-783d-4bf9-b11d-13da50a61c82 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 654d5763-783d-4bf9-b11d-13da50a61c82
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=654d5763-783d-4bf9-b11d-13da50a61c82 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 654d5763-783d-4bf9-b11d-13da50a61c82
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 654d5763-783d-4bf9-b11d-13da50a61c82
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=654d5763-783d-4bf9-b11d-13da50a61c82 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=f842efcc-85ce-466d-a1ef-fefa77cbd044 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 156.7GB: boot/grub/core.img
 159.2GB: boot/grub/grub.cfg
 157.1GB: boot/initrd.img-2.6.32-21-generic
 159.5GB: boot/initrd.img-2.6.32-25-generic
 158.4GB: boot/vmlinuz-2.6.32-21-generic
 158.5GB: boot/vmlinuz-2.6.32-25-generic
 159.5GB: initrd.img
 157.1GB: initrd.img.old
 158.5GB: vmlinuz
 158.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  81 d0 03 00 82 d0 03 00  83 d0 03 00 84 d0 03 00  |................|
00000010  85 d0 03 00 86 d0 03 00  87 d0 03 00 88 d0 03 00  |................|
00000020  89 d0 03 00 8a d0 03 00  8b d0 03 00 8c d0 03 00  |................|
00000030  8d d0 03 00 8e d0 03 00  8f d0 03 00 90 d0 03 00  |................|
00000040  91 d0 03 00 92 d0 03 00  93 d0 03 00 94 d0 03 00  |................|
00000050  95 d0 03 00 96 d0 03 00  97 d0 03 00 98 d0 03 00  |................|
00000060  99 d0 03 00 9a d0 03 00  9b d0 03 00 9c d0 03 00  |................|
00000070  9d d0 03 00 9e d0 03 00  9f d0 03 00 a0 d0 03 00  |................|
00000080  a1 d0 03 00 a2 d0 03 00  a3 d0 03 00 a4 d0 03 00  |................|
00000090  a5 d0 03 00 a6 d0 03 00  a7 d0 03 00 a8 d0 03 00  |................|
000000a0  a9 d0 03 00 aa d0 03 00  ab d0 03 00 ac d0 03 00  |................|
000000b0  ad d0 03 00 ae d0 03 00  af d0 03 00 b0 d0 03 00  |................|
000000c0  b1 d0 03 00 b2 d0 03 00  b3 d0 03 00 b4 d0 03 00  |................|
000000d0  b5 d0 03 00 b6 d0 03 00  b7 d0 03 00 b8 d0 03 00  |................|
000000e0  b9 d0 03 00 ba d0 03 00  bb d0 03 00 bc d0 03 00  |................|
000000f0  bd d0 03 00 be d0 03 00  bf d0 03 00 c0 d0 03 00  |................|
00000100  c1 d0 03 00 c2 d0 03 00  c3 d0 03 00 c4 d0 03 00  |................|
00000110  c5 d0 03 00 c6 d0 03 00  c7 d0 03 00 c8 d0 03 00  |................|
00000120  c9 d0 03 00 ca d0 03 00  cb d0 03 00 cc d0 03 00  |................|
00000130  cd d0 03 00 ce d0 03 00  cf d0 03 00 d0 d0 03 00  |................|
00000140  d1 d0 03 00 d2 d0 03 00  d3 d0 03 00 d4 d0 03 00  |................|
00000150  d5 d0 03 00 d6 d0 03 00  d7 d0 03 00 d8 d0 03 00  |................|
00000160  d9 d0 03 00 da d0 03 00  db d0 03 00 dc d0 03 00  |................|
00000170  dd d0 03 00 de d0 03 00  df d0 03 00 e0 d0 03 00  |................|
00000180  e1 d0 03 00 e2 d0 03 00  e3 d0 03 00 e4 d0 03 00  |................|
00000190  e5 d0 03 00 e6 d0 03 00  e7 d0 03 00 e8 d0 03 00  |................|
000001a0  e9 d0 03 00 ea d0 03 00  eb d0 03 00 ec d0 03 00  |................|
000001b0  ed d0 03 00 ee d0 03 00  ef d0 03 00 f0 d0 03 00  |................|
000001c0  f1 d0 03 00 f2 d0 03 00  f3 d0 03 00 f4 d0 03 00  |................|
000001d0  f5 d0 03 00 f6 d0 03 00  f7 d0 03 00 f8 d0 03 00  |................|
000001e0  f9 d0 03 00 fa d0 03 00  fb d0 03 00 fc d0 03 00  |................|
000001f0  fd d0 03 00 fe d0 03 00  ff d0 03 00 00 d1 03 00  |................|
00000200

Unknown BootLoader  on sda2

00000000  3c 24 8b ed 34 45 d9 db  fd b5 d2 6a af 2e 2a bb  |<$..4E.....j..*.|
00000010  b6 fa 7b 1e 69 4b a5 45  ef 69 5c cd ea fc 26 cf  |..{.iK.E.i\...&.|
00000020  e6 23 fa a8 8a fd 6c 99  2a bc 23 6b 38 80 fe ca  |.#....l.*.#k8...|
00000030  d1 85 14 ff 1f 7b f9 d2  6f b9 57 d1 f0 56 df e8  |.....{..o.W..V..|
00000040  dd d8 25 08 35 62 76 2d  f9 4d ae 39 12 b7 76 2f  |..%.5bv-.M.9..v/|
00000050  9d f9 22 c5 1b 23 02 06  68 7e f5 8c ed cd 7f 71  |.."..#..h~.....q|
00000060  df 28 a8 35 02 4c fb 85  d2 16 fe a0 7d ea db c9  |.(.5.L......}...|
00000070  cf bf 41 57 64 50 3d dc  fa cd bf c0 97 2b 13 57  |..AWdP=......+.W|
00000080  2c 12 74 ef b4 9c 48 7c  1c 10 a8 58 e3 5f 61 93  |,.t...H|...X._a.|
00000090  86 51 25 56 2d ac 0b 8f  7f 04 c1 a2 f3 4a 00 03  |.Q%V-........J..|
000000a0  4b ea ac 57 04 4c 8a 01  a2 3e ba 2d f1 30 3f 73  |K..W.L...>.-.0?s|
000000b0  7f 05 a4 a8 5b ad c6 d2  a7 ca 67 e5 36 1b fb a6  |....[.....g.6...|
000000c0  5d b8 b2 5f ce e4 d2 38  f9 2c 50 29 aa e7 eb 03  |].._...8.,P)....|
000000d0  9c 3e 46 07 ca cb 83 a8  1c 18 fe 72 06 5c 8c 0c  |.>F........r.\..|
000000e0  27 1e cb 8c 44 0e 0a 7b  a7 89 0d db 4f 65 17 32  |'...D..{....Oe.2|
000000f0  6c fb 3d db 59 c5 ec ba  25 67 0a 25 56 d8 ba 92  |l.=.Y...%g.%V...|
00000100  e7 50 2e 7a b7 7a d3 97  d6 3e 69 24 47 37 b8 7e  |.P.z.z...>i$G7.~|
00000110  d4 0b e7 ab 42 18 d8 cc  43 55 52 2b 99 b9 c7 57  |....B...CUR+...W|
00000120  21 66 f2 32 e0 48 1a 3e  c6 c6 38 62 c5 d1 a2 b7  |!f.2.H.>..8b....|
00000130  23 89 fc a3 60 f1 bf 2d  e6 02 3a fe 65 2a 19 f2  |#...`..-..:.e*..|
00000140  67 97 4b f7 df fc 8e df  b9 34 0c 9b 5e ec 75 b2  |g.K......4..^.u.|
00000150  fb 41 ed cf af 3e 32 8c  c2 88 e2 48 33 7b d0 ea  |.A...>2....H3{..|
00000160  98 98 a4 db ff f8 5c c1  91 ab 65 99 04 2c 5e 93  |......\...e..,^.|
00000170  2c f2 ff 71 b9 d0 58 23  d6 7b 61 4c 8c 79 a9 53  |,..q..X#.{aL.y.S|
00000180  de 2c f5 8c 54 8d 20 c4  95 a0 c6 8e 94 f6 09 b0  |.,..T. .........|
00000190  33 8b ed b7 4b 7f a2 72  00 10 5a ac 94 b5 cc 9b  |3...K..r..Z.....|
000001a0  1c 15 ac cd a7 39 57 28  bb cd 18 94 e5 84 e2 c4  |.....9W(........|
000001b0  ba c0 7f 43 84 82 2a 8e  3d 20 7b 4f 10 73 00 fe  |...C..*.= {O.s..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 5b 83 1c 00 00 fe  |..........[.....|
000001d0  ff ff 05 fe ff ff 5d 83  1c 00 a5 e4 65 00 00 00  |......].....e...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Quackers on 2010-10-13
Hmm, the script shows no Windows installations specifically.  sda1 shows "mounting failed" and an unknown file system type. The script does show 2 swap partitions and seems to show 2 linux partitions. 
I think you would be better served waiting for somebody with more experience than me to make suggestions. I would hate to lead you in the wrong direction.

---

### Post by tralph on 2010-10-13
ugh that sucks, thanks for all your help though.
do you think i have lost all of my documents, as i cant see them on ubuntu. Is there a program i could use to find them??

---

### Post by Quackers on 2010-10-13
I honestly don't know, but don't give up just yet. Things may not be as they seem. Hopefully somebody else will come along shortly :-)

---

### Post by cholericfun on 2010-10-13
did you previously had problems with the hard drive?
how was it formated before you installed ubuntu on it?

somehow your windows partiton got damaged.
i'd recommend trying gparted
(install e.g. via ```
sudo apt-get install gparted
```)
with this tool you could check and repair the first partition (sda1) which should be your windows partition. This should not cause any more damage but maybe at least allow you to access (and backup!) your files there.

---

### Post by Rubi1200 on 2010-10-13
> **tralph said:**
> ugh that sucks, thanks for all your help though.
do you think i have lost all of my documents, as i cant see them on ubuntu. Is there a program i could use to find them??
In this situation, the best chance is to probably use Testdisk to try and recover the Windows partition.

When you installed it seems as if you may have overwritten the Windows partition rather than installing side-by-side as you intended.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by BbUiDgZ on 2010-10-13
you could also boot using the windows XP cd (any xp cd) and boot recovery console.

When the console has loaded type:
```
fixmbr
```

load windows and shut it down correctly - reinstall grub from the live CD

it looks to me as if your windows install wasn't shut down right hence the reason Ubuntu can't see the NTFS partition.

---

### Post by tralph on 2010-10-13
grrr sorry for being a complete noob im trying to download testdisk but i cant install it, when i  click on the file nothing happens.
downloading from [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by tralph on 2010-10-13
> **BbUiDgZ said:**
> you could also boot using the windows XP cd (any xp cd) and boot recovery console.

When the console has loaded type:
```
fixmbr
```load windows and shut it down correctly - reinstall grub from the live CD

it looks to me as if your windows install wasn't shut down right hence the reason Ubuntu can't see the NTFS partition.

i cant install from an xp cd my netbook doesnt have a diskdrive lol :P

---

### Post by Quackers on 2010-10-13
Testdisk is available in Synaptic Package Manager.
Good luck with your attempts :-)

---

### Post by Rubi1200 on 2010-10-13
> **BbUiDgZ said:**
> you could also boot using the windows XP cd (any xp cd) and boot recovery console.

When the console has loaded type:
```
fixmbr
```load windows and shut it down correctly - reinstall grub from the live CD

it looks to me as if your windows install wasn't shut down right hence the reason Ubuntu can't see the NTFS partition.
How would this help?

With all due respect, take a good look at the script results:

> sda1: _________________________________________________________________________      File system:            Boot sector type:  [COLOR=Red]Unknown     Boot sector info[/COLOR]:       Mounting failed: mount: [COLOR=Red]unknown filesystem[/COLOR] type '' No file system and no boot files.

---

### Post by tralph on 2010-10-13
update guys. using Gparted i got the following info (see screenie) it can clearly see the partion is there, i am unsure however how to recover this. any ideas or shall i just get testdisk :P


thanks to everyone for their updates

---

### Post by Quackers on 2010-10-13
It's the "unknown" flag that is worrying.
I think Testdisk would be the way to go here.
By all means take your time and see if anybody else can come up with anything. Good luck to you :-)

---

### Post by tralph on 2010-10-13
thanks all i'll  see if anyone adds anything else and if not try tomoz night. There isnt much too be lost just bloody annoying lol!

---

### Post by cholericfun on 2010-10-13
it is annoying to see an install going wrong,
there isnt really a reason for this, linux (grub) is pretty good at having as a dual install.
one thing that i find disturbing apart from the fact that your windows is broken:
you have only a tiny scattered amount of diskspace left for linux

this doesnt seem like a very workable option in the first place, not that it shoudlnt work but rather leave your hard disk space retired to a USB-stick type of memory load.

i'd go ahead and try to check and repair sda1 with gparted and as a second option try testdisk

!then you may want to backup your files!

again: how was your computer hard disk partitioned originally:
i.e. there should be a windows recovery partition somewhere


so far i hope you can bear with this with patience,
these things are rather fundamental (in terms of losing data - not in terms of doing anything bad to the laptop as such).

if you wanted to install ubuntu next to windows i would 1st find out where the windows recovery partition is (if there is one an i presume there is)
then partition all the *other* space to suit your needs:
e.g. 
1/2 windows :ntfs
1000 MB swap
rest ubuntu :ext3 or ext4

then install ubuntu on its own partition
(better still to have a seperate partition for /home and the rest of the install but thats up to you - you can chose how and where to mount what partitions in the "expert" 'or whatever they call it now' install menu )

i hope i'm not confusing you here...

---

### Post by tralph on 2010-10-14
Just to update on how my partition was before. I had my windows partition which was the full drive (standard when i bought the laptop) i then partitioned 10 gb off to make a "linux"partition. However when i installed ubuntu it didn't seem to give me an option of where to "create" it (either that or i'm just an idiot lol)

There is not much data to be lost so its not too much of a hastle as the majority is backed up, there are some holiday snaps i would like though :(, but i will have to go through the rigmarole of installing windows off of a USB stick.

I wont be at my laptop until about 6 tonight, so again waiting any other updates people can give. 

Thanks again to everyone

---

### Post by tralph on 2010-10-14
> **cholericfun said:**
> it is annoying to see an install going wrong,
there isnt really a reason for this, linux (grub) is pretty good at having as a dual install.
one thing that i find disturbing apart from the fact that your windows is broken:
you have only a tiny scattered amount of diskspace left for linux

this doesnt seem like a very workable option in the first place, not that it shoudlnt work but rather leave your hard disk space retired to a USB-stick type of memory load.

i'd go ahead and try to check and repair sda1 with gparted and as a second option try testdisk

!then you may want to backup your files!

again: how was your computer hard disk partitioned originally:
i.e. there should be a windows recovery partition somewhere


so far i hope you can bear with this with patience,
these things are rather fundamental (in terms of losing data - not in terms of doing anything bad to the laptop as such).

if you wanted to install ubuntu next to windows i would 1st find out where the windows recovery partition is (if there is one an i presume there is)
then partition all the *other* space to suit your needs:
e.g. 
1/2 windows :ntfs
1000 MB swap
rest ubuntu :ext3 or ext4

then install ubuntu on its own partition
(better still to have a seperate partition for /home and the rest of the install but thats up to you - you can chose how and where to mount what partitions in the "expert" 'or whatever they call it now' install menu )

i hope i'm not confusing you here...


Hi how can I try and recover the disk with gparted, i see no option :(

---

### Post by cholericfun on 2010-10-14
first select sda1, unmount it (right click), then you can right-click and select "check".
then you need to click on the green tick to start

---

### Post by tralph on 2010-10-14
It wont let me press unmount the option is greyed out :(

---

### Post by cholericfun on 2010-10-14
hm
is it mounted in the first place (it shouldnt! - or better it is not possible to mount this partition because something is broken)

so you just go ahead and click on check (right-click - check) and "apply".

---

### Post by tralph on 2010-10-14
cant do that either :( the only options i have are delete, format to, manage flags or info,
any ideas?

---

### Post by nerdy_kid on 2010-10-14
one thing:

to the OP -- I WOULD STRONGLY RECOMMEND COPYING THE PARTITION TO ANOTHER DRIVE.

you will need an external hard drive with at least 150Gb of free space.  Plug it in, and navigate to it with your file manager.  Find out where it is mounted.  You should be able to do that by right clicking the empty space inside the drive folder and clicking properties.  It should be something very similar to /media/disk/   If you can't find it then open a terminal and run "mount" (without quotes) and paste the result here.
Once you know where it is mounted, open a terminal. enter:
```

sudo dd if=/dev/sda1 of=MOUNTPOINT/windows_backup.img  -- EXAMPLE of the mount point was /media/disk then the command would be dd if=/dev/sda1 of=/media/disk/windows_backup.img

```
that will ask you for your password.  Once you give it, be prepared to wait a very very long time -- your windows partition is being copied to a file on your external hard drive.  This way, if it gets broken more we have a backup.

[edit]

everyone else -- anyone know where the partition table is on the disk?  We should back this up.  I know the MBR is the first 512Kb but if I am not mistaken that is different from the partition table?


[edit]
testdisk would probably be the best for this.

But -- before you use it you should back up the partition table.  I can't remember if testdisk does this automatically -- better safe then sorry.  Put your external hard drive back in and open a terminal:  (thanks to the people on IRC for this)
```

sudo sfdisk -d /dev/sda > EXTERNAL_DRIVE_MOUNT_POINT/partition_table.backup

```

To install testdisk:
```

sudo apt-get install testdisk

```
run it:
```

sudo testdisk

```
It is pretty self explanatory -- nice wizard format.  Hit create new log.  Then select /dev/sda.  Then select Intel.  Then select analyze.  After the analyze you will be presented with an editable partition table.  Here you may change the flags of the partition table.  I can't really guide you through this -- if you want post a screenie and I should be able to tell you what to do.  Can't say that I will be on then though, so you might have to leave it open for a while (few days even).

---

### Post by tralph on 2010-10-14
will i be able to do this even though i cannot see my windows "drive" on the file system menu?

---

### Post by nerdy_kid on 2010-10-14
> **tralph said:**
> will i be able to do this even though i cannot see my windows "drive" on the file system menu?

yup.  What it does is it copies the actual bytes off of the drive -- so it will ALWAYS work (unless the drive is physically damaged)

---

### Post by tralph on 2010-10-15
cool thanks I will try this tonight/over the weekend and hope it works. 

Thanks for all the help guys

---

### Post by tralph on 2010-10-15
hi, see results from screen shot attached, do i know just put this into a terminal to make a backup?
```
 dd if=/dev/sda1 of=media/windows_backup.img 
```

---

### Post by nerdy_kid on 2010-10-15
> **tralph said:**
> hi, see results from screen shot attached, do i know just put this into a terminal to make a backup?
```
 dd if=/dev/sda1 of=media/windows_backup.img 
```

Almost the right command :)
the correct one is
```

sudo dd if=/dev/sda1 of=/media/LACIE/windows_backup.img

```

once again, that will take a long long time and it won't tell you what percent it is at either (nasty I know).  If you are like me and simply *need* to know you can go to the LACIE drive and check the free disk space to give you a guesstimate.

---

### Post by tralph on 2010-10-18
Just an update guys, thanks for all your help. I have decided to just nuke the device and reinstall everything and is all working now :) 


cheers again 

tralph

---

### Post by Quackers on 2010-10-18
It's sad that you had to go to those lengths but it's good that you're working fully again :-)
And just think what you've learned!!! :-):-):-)

---

### Post by tralph on 2010-10-18
> **Quackers said:**
> It's sad that you had to go to those lengths but it's good that you're working fully again :-)
And just think what you've learned!!! :-):-):-)


haha so true, I have gone for windows 7 on it as well, and that seems to run surprisingly quick on the little thing! maybe i will try and get another linux working on it sometime.

oh yeah and i might actually backup this time!!

---

