---
title: "Win7 404 yet found, Grub self-defaulting"
date: 2012-07-10
forum: General Help
---

### Post by Faziri on 2012-07-10
Yes yes, another Windows-related topic... MS will never learn how to properly write an OS, I suppose. :p

I'm new to everything about the techy parts of  a computer in the sense that I have had to teach myself everything I know. On the other hand, my understanding of all of it has gotten pretty far and I'm plenty comfortable messing with partitions, bootloaders, Grub, Ubuntu, etc. I've learned well and plenty on my own, thanks to places like this, and I'll probably be bored to death the first few months of my first Application Development year in college. :P

My latest adventure has been to prep my computer for college.
I have a laptop with Win7, to which I added Ubuntu after a fatal crash (that I recovered from, but it took a while so Ubuntu made a nice way to keep on computering in the meantime) and ever since I've been getting familiar with the Linux way of life. Ubuntu, Boot-repair-disk and Gparted Livedisc have become indispensible for my maintenance work.
For college, I didn't want to have to throw out several gigabytes of stuff to make some space for the workload and then cram it full to the brim nor did I want to drag an external around. So instead, I went to buy a 90GB SSD today and just decided I'd swap the drives between home and college: SSD with the bare essentials for all my college stuff and nothing else, the normal HDD for my personal use.

The plan (with help from this forum and some creativity):
-make an image of my Win7 with Macrium
-burn it to the blank SSD (didn't use the livecd but just used an in-Windows session, which worked much better than when I used the livecd at first and failed to make it work...)
-trim it down and throw out everything but the essentials (less work than reinstalling and configuring the essentials again, I don't have any way to install a blank Win7 anyway)
-use the remaining space to make partitions for Ubuntu and a few for storing college-specific stuff like programs and products

So far so good:
-I've made the image and burned it to the SSD, resulting in an exact copy of my C: (infamous System partition has been taken care of, the Windows Bootloader is on C: as well thanks to EasyBCD, so there just is no System partition anymore) complete with the blank space from the Recovery partition in front and a copy of the MBR from the HDD
-used Gparted to move Windows partition to the front of the disc and split the remaining space into a few partitions
-used the Ubuntu 11.04 livecd to install Grub and Ubuntu in the remaining partitions (it displayed the option to "install alongside Windows 7" so clearly Windows was at least detected, bootable most likely)
-reboot showed all entries in a functional Grub (including Windows)
-went into Ubuntu, updated to 11.10 (12.04 crashes itself every time I run it so no thanks), threw out some gadgets and just set it up as usual
-not sure about the Windows entry in Grub at this reboot (see problem down below)
-back into Ubuntu, used Grub Customizer to set up a personalized Grub (works flawlessly every time on the HDD install), everything looking fine
-reboot showed Grub **without Windows and without the customizations I had only just made using GC as I've done a thousand times before**
-booted into Boot-repair-disk and repaired my Grub, rebooted and **got the same default Grub without Windows and without the freshly-made customizations**
-"sudo os-prober" shows no Windows
-BootInfoScript shows Windows and no problems detected in boot
-GC shows no Windows (of course not, it uses os-prober for that...)

So there's my problem. TLDR: cloned Win7 to new drive, installed Ubuntu alongside it, everything fine. Booted into Ubuntu, started working on it, rebooted, Windows gone. Grub Customizer and Boot-repair-disk can not detect nor restore Windows entry (or anything else in Grub for that matter, it continues to default back to white-on-purple and such every time), Bootinfoscript shows Windows entry with no problems detected and hooking up the SSD to a SATA->USB adapter (currently running from HDD again) shows no problems either.

**Edit:** I just noticed I forgot to use Gparted to put the 3 Ubuntu partitions as logicals under the extended after the livecd setup decided to make all 3 of them primaries... Most likely that's the problem here, I've got 4 primaries and an extended on 1 disc...
**Edit edit:** Windows Disk Management says they're all primaries, partitioning tools on Windows say they're logicals... Looks like this'll be more of a Windows issue and I bet the Grub issue stops existing once this is fixed too... I'll see if Fixparts can do the job for me tomorrow.
Rubber duck method ftw xD

Sorry if it's a bit confusing but I'm running two instances of a dual-boot on 2 different discs (1 disc at a time of course) so it will probably never be easy. :D The HDD is my trusted home (back on it right now), the SSD is the testing-stage experiment where things are currently not working right.

If anyone can figure out why os-prober can't find Windows while BIS can and why Grub keeps resetting to defaults despite being edited by 2 dedicated Grub editors, you'll have my eternal thanks!

Also, here's a results.txt 'cause I know you like those so much. :P
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos8)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 90.0 GB, 90028302336 bytes
255 heads, 63 sectors/track, 10945 cylinders, total 175836528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    62,914,559    62,912,512   7 NTFS / exFAT / HPFS
/dev/sda2          62,916,606   175,835,135   112,918,530   5 Extended
/dev/sda5          98,574,336   140,517,375    41,943,040   7 NTFS / exFAT / HPFS
/dev/sda6         140,519,424   175,835,135    35,315,712   7 NTFS / exFAT / HPFS
/dev/sda7          90,574,848    98,574,335     7,999,488  82 Linux swap / Solaris
/dev/sda8          62,916,608    78,915,583    15,998,976  83 Linux
/dev/sda9          78,917,632    90,572,799    11,655,168  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        6288816E88814191                       ntfs       Windows 7
/dev/sda5        0DF742AE64286A26                       ntfs       KdG System
/dev/sda6        3BEF1C63190D8BBF                       ntfs       KdG
/dev/sda7        fbbe4266-acb9-42c5-a45d-e4fe917d432c   swap       
/dev/sda8        e2c39494-d96d-48c8-92ca-94e39d553410   ext4       
/dev/sda9        dabc9698-1d6b-4767-b00b-7d59db12e6ce   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/Windows 7         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda8        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda9        /home                    ext4       (rw,commit=0)


=========================== sda8/boot/grub/grub.cfg: ===========================

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
set default="${saved_entry}"
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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set=root e2c39494-d96d-48c8-92ca-94e39d553410
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1600x900x24
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos8)'
  search --no-floppy --fs-uuid --set=root e2c39494-d96d-48c8-92ca-94e39d553410
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set=root e2c39494-d96d-48c8-92ca-94e39d553410
insmod jpeg
if background_image /boot/grub/grub.jpg; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_os-prober_proxy ###
### END /etc/grub.d/10_os-prober_proxy ###

### BEGIN /etc/grub.d/11_linux_proxy ###
menuentry 'Ubuntu, with Linux 3.0.0-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    savedefault
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root e2c39494-d96d-48c8-92ca-94e39d553410
    linux    /boot/vmlinuz-3.0.0-22-generic-pae root=UUID=e2c39494-d96d-48c8-92ca-94e39d553410 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-22-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root e2c39494-d96d-48c8-92ca-94e39d553410
    echo    'Loading Linux 3.0.0-22-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-22-generic-pae root=UUID=e2c39494-d96d-48c8-92ca-94e39d553410 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-22-generic-pae
}
### END /etc/grub.d/11_linux_proxy ###
--------------------------------------------------------------------------------

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=e2c39494-d96d-48c8-92ca-94e39d553410 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=dabc9698-1d6b-4767-b00b-7d59db12e6ce /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=fbbe4266-acb9-42c5-a45d-e4fe917d432c none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-8-generic               2
               =                boot/initrd.img-3.0.0-22-generic               2
               =                boot/initrd.img-3.0.0-22-generic-pae           3
               =                boot/vmlinuz-2.6.38-8-generic                  1
               =                boot/vmlinuz-3.0.0-22-generic                  1
               =                boot/vmlinuz-3.0.0-22-generic-pae              1
               =                initrd.img                                     3
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  83 66 8d d9 3d 5d b6 0c  63 73 2e 42 67 f3 29 e1  |.f..=]..cs.Bg.).|
00000010  dc b1 19 3d 9f 48 de e1  26 b9 7e 82 64 2d a0 d8  |...=.H..&.~.d-..|
00000020  e7 f6 b9 92 c6 b1 88 d4  2a 54 40 b5 37 16 51 84  |........*T@.7.Q.|
00000030  0c f4 a8 50 3f df 5f af  c7 20 a1 b8 6f 11 7c 25  |...P?._.. ..o.|%|
00000040  de cb 80 2e bc cd 51 a4  67 0e 39 76 4f e3 4b 5f  |......Q.g.9vO.K_|
00000050  87 66 99 e7 40 34 8a 58  d4 5b 3b 45 37 54 97 b1  |.f..@4.X.[;E7T..|
00000060  31 33 70 70 6a 68 8a 5d  7f 5e 8e ee 6f 3c 19 b3  |13ppjh.].^..o<..|
00000070  b0 78 ca 7e bc f3 74 86  2d ff 08 66 44 3d ae 69  |.x.~..t.-..fD=.i|
00000080  8f cf 24 c7 2d 7c 0e f2  f9 98 23 fb ab f4 a2 49  |..$.-|....#....I|
00000090  ac 37 88 f5 46 b1 3e 5d  ac cf 10 61 e8 d5 67 89  |.7..F.>]...a..g.|
000000a0  f5 b3 c5 fa f9 62 bd 59  ac 2f 90 0e 89 f5 45 2c  |.....b.Y./....E,|
000000b0  e3 59 c5 d7 8b 81 8d 7f  56 71 96 6b 64 a9 cf 2a  |.Y......Vq.kd..*|
000000c0  ce 72 d3 99 fc 0c 5e 1a  51 da 98 fb 62 10 a4 ad  |.r....^.Q...b...|
000000d0  f4 ad d6 e2 6d 96 8c ad  d6 12 29 d1 d7 cc 99 c9  |....m.....).....|
000000e0  44 11 98 72 6b ba 54 64  30 1d f5 24 42 5b 94 f9  |D..rk.Td0..$B[..|
000000f0  eb e7 03 b6 7d cf 60 fb  63 74 b3 d2 2c f6 f6 33  |....}.`.ct..,..3|
00000100  7c 36 a3 46 ff bc 17 69  41 ab 19 26 56 73 ca 48  ||6.F...iA..&Vs.H|
00000110  24 18 47 ba e0 ca 76 b2  1a 58 98 c6 66 e2 f9 43  |$.G...v..X..f..C|
00000120  03 f2 b2 06 7f fd 00 92  3c 1e 7c 43 b2 1b 80 cc  |........<.|C....|
00000130  6a c9 68 c5 66 63 97 cf  c5 bd 76 68 58 ed 92 32  |j.h.fc....vhX..2|
00000140  f2 98 14 02 fa b6 09 58  9b 35 d2 2a 43 d3 49 4f  |.......X.5.*C.IO|
00000150  8a b4 4a 0f 4b 6d 69 c3  a6 b1 82 fb 67 68 3f cd  |..J.Kmi.....gh?.|
00000160  0f 2a 5c 1a 97 ca 39 4a  8d f6 75 06 1b 4f 7e 8a  |.*\...9J..u..O~.|
00000170  cc 3d 75 4d 3b 91 cf db  68 98 4a 51 d0 ba 49 1f  |.=uM;...h.JQ..I.|
00000180  69 44 e6 59 f0 28 81 64  98 57 a7 03 6f 90 4e 8e  |iD.Y.(.d.W..o.N.|
00000190  43 72 e7 2a ae a4 2c 5d  7d a8 e6 d5 b0 69 8c e0  |Cr.*..,]}....i..|
000001a0  5e 88 9a fe ee 8c 1a 9f  d7 a0 71 4f 24 83 e8 43  |^.........qO$..C|
000001b0  52 82 bf c4 50 26 6f d0  00 93 f5 08 46 ef 00 fe  |R...P&o.....F...|
000001c0  ff ff 07 fe ff ff 02 18  20 02 00 00 80 02 00 fe  |........ .......|
000001d0  ff ff 05 fe ff ff 02 18  a0 04 00 e8 1a 02 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
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
```

---

### Post by oldfred on 2012-07-10
Did you resize Windows from inside Windows? That usually prevents issues that resizing using gparted often creates.

Windows NTFS partitions have to have the same type of partition info as the partition table on start and size. If that does not match Windows has issues. Sometimes it is other issues, but usually it can be fixed with a Windows repairCD and running chkdsk until no errors and possibly fixBoot.

In Ubuntu you have this as your mount point:
> 
/media/Windows 7 

I learned to stop using spaces with LInux as you have to use quotes or other delimiters \040 to create a space. Easier just not to use space at all , use CamelCase, or Under_score. Otherwise confusion often exists.

---

### Post by Faziri on 2012-07-12
Sorry, I forgot to get back to this.

I got it all fixed, the problem was indeed that the Ubuntu livecd had made its partitions all primaries and thus there was an illegal number of primaries and an extended partition on the disk. Erasing all partitions except the one with Win7, making them a second time (to have a clean partition table written from scratch) and then using the livecd to install Ubuntu into existing partitions rather than creating them out of unallocated space fixed the problem.

As for moving Windows around: there were actually no problems. I could move the Win7 partition's (including its starting sector) around with gparted without problems, changing its size, properties and neighboring partitions has no negative effect at all, etc. Windows 7 is actually not such a nagging, disoriented idiot at all, in my experience.

The only (quite expectable) problem that popped up when booting into Windows was that the bootloader could not find Windows itself. Of course, its boot entry uses the hardware ID of the disk to refer to winload.exe's location, but when cloning everything to a new disk, the hardware ID changes and the reference becomes invalid. I booted into the Windows recovery disc (the small one that you can make from within Windows at any time) and it auto-detected the missing boot entry, fixed it and didn't even interfere with Grub at all.

So all's fixed, just gotta remember that the livecd makes partitions created with it primaries by default.

Thanks for the help anyway, the good old rubber duck method is not something to underestimate :lolflag:

---

