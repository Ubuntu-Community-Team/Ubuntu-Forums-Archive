---
title: "Minimal BASH-like...."
date: 2011-12-07
forum: General Help
---

### Post by Zelda Hunter on 2011-12-07
This is the second occurrence of this problem; I simply reinstalled Ubuntu using WUBI previously as I found no solution. I do not feel like repeating that process. >.>

First, I boot the computer. The computer loads a GNOME bootmenu, which by the way is a remnant of a broken 11.10 that stopped working after upgrading from 11.04. I choose "Windows" and further choose "Ubuntu" on a... monochromatic bootloader thing--of what I'm not sure. Boom, problem.

The screen shows the GNOME version number (something like 1.99-12ubuntu5); then says, "Minimal BASH-like line editing supported". Don't know what to do even though I'm using an OS assuming I know what I'm doing....

Note: if any of the things I desperately Google after this post does not work, this will serve as an even more desperate fallback. Which I hope isn't necessary. :<
Note 2: I don't have a USB drive to boot with. Sorry.

Your help is greatly appreciated.

---

### Post by bcbc on 2011-12-07
This is likely the cause of the wubi issue: [http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html)

Your boot goes: Grub -> broken old direct Ubuntu install -> Windows Boot Manager (your "monochromatic" menu) -> Wubi grub (fails to find root.disk and falls to grub prompt)

---

### Post by Zelda Hunter on 2011-12-07
But neither root.disk nor /ubuntu/disks is missing.... I tried the instructions anyway--no success; same grub> menu.

---

### Post by bcbc on 2011-12-07
> **Zelda Hunter said:**
> But neither root.disk nor /ubuntu/disks is missing.... I tried the instructions anyway--no success; same grub> menu.

Did you run chkdsk?

---

### Post by Zelda Hunter on 2011-12-07
I just did. Nothing happened.

As in, no files were changed.

---

### Post by bcbc on 2011-12-07
Type in the following from the grub prompt:

```
search --set=diskroot -f -n /ubuntu/disks/root.disk
set root=$diskroot
loopback loop0 /ubuntu/disks/root.disk
probe --set=diskuuid -u $diskroot
set root=(loop0)
linux /vmlinuz root=UUID=$diskuuid loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```

You could create a file that contains the instructions and load it direct. But it's probably better to do it step by step and see where the failure is (if it fails).

---

### Post by Zelda Hunter on 2011-12-07
On the linux /vmlinuz root=uuid... command, Grub produces an "unknown filesystem" error.

---

### Post by bcbc on 2011-12-07
I don't think you can get around this without an Ubuntu CD/USB. It looks like you'll have to fsck the root.disk to repair this problem.

Have you been doing forced shutdowns or has your system been hanging at all (just trying to understand why you are having problems)? Did you try repairing the failed upgrade that's directly installed (not with wubi)?
(if you can boot this then you can probably fsck the root.disk from it - even just a recovery prompt will do).

---

### Post by Zelda Hunter on 2011-12-07
I may be able to make a Boot CD. Let me try.

I'm not sure what you mean by force shutdowns, but I have been using the button on the actual computer case (couldn't find another way); no hanging, though. I have not tried repairing the failed upgrade; I got lazy on that.... D:

---

### Post by bcbc on 2011-12-07
> **Zelda Hunter said:**
> I may be able to make a Boot CD. Let me try.

I'm not sure what you mean by force shutdowns, but I have been using the button on the actual computer case (couldn't find another way); no hanging, though. I have not tried repairing the failed upgrade; I got lazy on that.... D:
Okay ... avoid using the button on the computer to shut it down. You can damage the file system if it's in the middle of writes. Instead, shutdown normally by clicking on the Cog (type right) and the selecting Shutdown from the drop down menu, or safely reboot with Alt+SysRq R-E-I-S-U-B.

---

### Post by Zelda Hunter on 2011-12-07
I should be able to boot this CD I'm nearly done burning. What shall I do once I boot it, though?

---

### Post by bcbc on 2011-12-07
You need to mount the partition that the root.disk is on, and then fsck it.

E.g. if the root.disk is on /dev/sda2
```
sudo mount /dev/sda2 /mnt
sudo fsck /mnt/ubuntu/disks/root.disk
```

If you want to know the partition it's on, you can run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and check the results. Or you could mount each partition until you find it. If you mount partitions from nautilus (the icon top left on the Unity dock that looks like a house) they'll be mounted under /media by either the drive label or UUID if no label.

---

### Post by Zelda Hunter on 2011-12-07
> fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /mnt/ubuntu/disks/root.disk

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


Problems after another. >.>

---

### Post by Rubi1200 on 2011-12-07
I suggest posting the results of the boot info script at this point so we can see what is where on your system:
 [bootinfoscript]("http://bootinfoscript.sourceforge.net/")

Thanks.

---

### Post by bcbc on 2011-12-07
> **Zelda Hunter said:**
> Problems after another. >.>

This guide describes how to go about repairing this, but note it's not for a loopmounted device. So the parts about mounting it won't work. The parts about finding the alternate superblocks will work replacing /dev/sda2 with /mnt/ubuntu/disks/root.disk

[http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/)

---

### Post by Zelda Hunter on 2011-12-07
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    83,888,127    83,886,080  83 Linux
/dev/sda2          83,888,128    83,890,175         2,048  83 Linux
/dev/sda3    *     83,891,430   615,916,034   532,024,605   7 NTFS / exFAT / HPFS
/dev/sda4         615,931,902   625,141,759     9,209,858   5 Extended
/dev/sda5         615,931,904   625,141,759     9,209,856  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0453debb-8f7e-4b7b-9285-e0de314d2d7b   ext4       
/dev/sda2        924f2fde-29a0-424a-9868-e91a83f14efb   ext2       
/dev/sda3        0F1DEC2F7B0D3607                       ntfs       
/dev/sda5        ac3b847b-deaa-4f0d-969b-48fc990c224f   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 0453debb-8f7e-4b7b-9285-e0de314d2d7b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 0453debb-8f7e-4b7b-9285-e0de314d2d7b
insmod jpeg
background_image -m stretch /usr/share/backgrounds/Touch_the_light_by_Matt_Katzenberger.jpg
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 0453debb-8f7e-4b7b-9285-e0de314d2d7b
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 0453debb-8f7e-4b7b-9285-e0de314d2d7b
insmod jpeg
if background_image /usr/share/backgrounds/Touch_the_light_by_Matt_Katzenberger.jpg; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 0453debb-8f7e-4b7b-9285-e0de314d2d7b
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=0453debb-8f7e-4b7b-9285-e0de314d2d7b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 0453debb-8f7e-4b7b-9285-e0de314d2d7b
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=0453debb-8f7e-4b7b-9285-e0de314d2d7b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 0453debb-8f7e-4b7b-9285-e0de314d2d7b
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=0453debb-8f7e-4b7b-9285-e0de314d2d7b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 0453debb-8f7e-4b7b-9285-e0de314d2d7b
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=0453debb-8f7e-4b7b-9285-e0de314d2d7b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 0453debb-8f7e-4b7b-9285-e0de314d2d7b
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=0453debb-8f7e-4b7b-9285-e0de314d2d7b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 0453debb-8f7e-4b7b-9285-e0de314d2d7b
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=0453debb-8f7e-4b7b-9285-e0de314d2d7b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 0453debb-8f7e-4b7b-9285-e0de314d2d7b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 0453debb-8f7e-4b7b-9285-e0de314d2d7b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 0F1DEC2F7B0D3607
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Grub for Dos" {
insmod ntfs
set root=(hd0,1)
linux /grub.exe
}

### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc       /proc  proc  nodev,noexec,nosuid  0  0  
/dev/sda1  /      ext4  errors=remount-ro    0  1  
/dev/sda5  none   swap  users,sw,owner       0  0  

UUID=0F1DEC2F7B0D3607 /media/Windows ntfs defaults,nls=utf8,uid=1000,umask=000 0 0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-10-generic              2
               =                boot/initrd.img-2.6.38-11-generic              1
               =                boot/initrd.img-2.6.38-8-generic               2
               =                boot/vmlinuz-2.6.38-10-generic                 2
               =                boot/vmlinuz-2.6.38-11-generic                 1
               =                boot/vmlinuz-2.6.38-8-generic                  1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     1
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3/Wubi

00000000  02 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000010  00 00 00 00 9c 00 00 00  d0 03 00 00 14 00 00 00  |................|
00000020  00 00 00 00 fc 00 00 00  49 44 45 4e 54 49 54 59  |........IDENTITY|
00000030  43 52 4c 5f 43 45 52 54  5f 43 4f 4e 54 41 49 4e  |CRL_CERT_CONTAIN|
00000040  45 52 5f 63 61 30 61 30  63 35 62 2d 66 62 38 31  |ER_ca0a0c5b-fb81|
00000050  2d 34 63 62 37 2d 62 33  32 66 2d 32 63 66 64 38  |-4cb7-b32f-2cfd8|
00000060  63 31 62 65 37 31 31 00  00 00 00 00 00 00 00 00  |c1be711.........|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 52 53 41 31  |............RSA1|
00000080  88 00 00 00 00 04 00 00  7f 00 00 00 01 00 01 00  |................|
00000090  03 f5 1f 29 57 90 3c 61  fc a7 51 b5 f5 a4 39 fb  |...)W.<a..Q...9.|
000000a0  31 90 52 98 09 a0 fe 5b  f6 cb 02 ea b5 79 a2 1a  |1.R....[.....y..|
000000b0  25 ed 57 e5 43 6c ed 3a  c4 6f bc 24 06 da 42 84  |%.W.Cl.:.o.$..B.|
000000c0  ac e5 ab b2 e1 26 3c b9  5c a6 a1 1f 3a db 6c d9  |.....&<.\...:.l.|
000000d0  f8 ab 9d bd 56 f1 5c 0c  cc ca 3f 82 75 c5 12 cb  |....V.\...?.u...|
000000e0  1d 79 50 07 c1 83 3d 41  a1 1a 28 f7 5a e3 da b1  |.yP...=A..(.Z...|
000000f0  66 72 6a 7e 5d 1a e7 bf  ff 43 1b 09 5a ec 65 13  |frj~]....C..Z.e.|
00000100  5a b4 4d b5 03 5a 55 92  0d 19 04 1a b6 d0 c4 c2  |Z.M..ZU.........|
00000110  00 00 00 00 00 00 00 00  01 00 00 00 d0 8c 9d df  |................|
00000120  01 15 d1 11 8c 7a 00 c0  4f c2 97 eb 01 00 00 00  |.....z..O.......|
00000130  be dd 42 78 be 7a d6 4a  8c 53 02 5d 98 15 47 bf  |..Bx.z.J.S.]..G.|
00000140  00 00 00 00 2c 00 00 00  43 00 72 00 79 00 70 00  |....,...C.r.y.p.|
00000150  74 00 6f 00 41 00 50 00  49 00 20 00 50 00 72 00  |t.o.A.P.I. .P.r.|
00000160  69 00 76 00 61 00 74 00  65 00 20 00 4b 00 65 00  |i.v.a.t.e. .K.e.|
00000170  79 00 00 00 10 66 00 00  00 01 00 00 20 00 00 00  |y....f...... ...|
00000180  01 d4 c3 7c db ac b6 0f  1c 9d f3 37 9f 71 f1 10  |...|.......7.q..|
00000190  ba 3c f3 ea 4f 36 56 46  42 80 59 1d fc 3c 4c d6  |.<..O6VFB.Y..<L.|
000001a0  00 00 00 00 0e 80 00 00  00 02 00 00 20 00 00 00  |............ ...|
000001b0  a3 b4 de f8 1a 40 b9 8a  cf c4 06 13 b8 63 1f a1  |.....@.......c..|
000001c0  ba e4 fe 41 d0 e7 9e 88  8a 60 0f fe 7d dd 6d c8  |...A.....`..}.m.|
000001d0  d0 02 00 00 ec 2b d3 0f  26 ee 21 57 43 2a c9 e3  |.....+..&.!WC*..|
000001e0  e6 0d f2 da e3 95 13 e2  52 3d d7 71 ce 98 b8 bd  |........R=.q....|
000001f0  53 a1 28 14 d7 d9 51 54  b8 34 9e 3e d6 ff 14 18  |S.(...QT.4.>....|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```To be honest, this looks like gibberish. D:

And to be even more honest, this is a lot of trouble to go through. Hopefully I can have this solved within the hour.

---

### Post by Zelda Hunter on 2011-12-07
For the superblock problem, it says there isn't a valid superblock in my partition.... Erm.... I'd hate to say this, but I am reinstalling Ubuntu without WUBI. This took way too long but I thank you for your diligent help. It's awesome that someone actually bothered to help for... six hours. :P

...Speaking of that, how would I get rid of the old, broke 11.10 upgrade?

---

### Post by bcbc on 2011-12-07
> **Zelda Hunter said:**
> For the superblock problem, it says there isn't a valid superblock in my partition.... Erm.... I'd hate to say this, but I am reinstalling Ubuntu without WUBI. This took way too long but I thank you for your diligent help. It's awesome that someone actually bothered to help for... six hours. :P

...Speaking of that, how would I get rid of the old, broke 11.10 upgrade?

You can just reinstall over /dev/sda1 which is your old install. When you get to the point where it asks you how you want to install, select "Something else" and then click on "/dev/sda1", then click "Change", set the Mountpoint as "/" (root), set the file system as ext4. Then you can either check the "Format" box to completely replace what's there or you can also try to install without formatting (this will leave your data from your old install intact but replace the OS bits). The swap on /dev/sda5 should be selected automatically, but check it. 
That's about it.

---

