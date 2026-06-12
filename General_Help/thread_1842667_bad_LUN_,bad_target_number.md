---
title: "bad LUN ,bad target number"
date: 2011-09-11
forum: General Help
---

### Post by craigbett on 2011-09-11
Hi I'm trying to install Ubuntu on my DV7 laptop, I'm using wubi on a windows 7 ult x64. After the install I try to boot into ubuntu but I keep getting 
Bad LUN
Bad target number # (this error is repeated several times)
and then it shows a command line, How can i fix this?

---

### Post by craigbett on 2011-09-11
I'm using the latest ver of Ubuntu/Wubi on a windows 7 Ult x64 system. I have no idea why it's not starting. See the attached pics for more info.

---

### Post by Rubi1200 on 2011-09-13
Thread Merged.

Hi and welcome to the forums craigbett :)

Since both threads you started seem to have the same end result (inability to boot into Ubuntu), I have merged them.

In this situation, it would be helpful if you could post the full specifications for the computer and the boot info script (there is a link at the bottom of my post with instructions).

Thanks.

---

### Post by Curix on 2011-09-20
Hello, I have the same problem.
Just got my new laptop and it has been a while that I wanted to try ubuntu.

Computer specifications: 
	
---------------------------------------------------------------
 
Operating System new – server roles	 	System Model
Windows 7 Home Premium (x64) Service Pack 1 (build 7601)
Install Language: Nederlands (Nederland)
System Locale: Nederlands (België)
IPavilion dv7 Notebook PC 058F110000244610000620100
System Serial Number: 5CH1282AMF
Enclosure Type: Notebook
Processor a	 	Main Circuit Board b
2,00 gigahertz Intel Core i7-2630QM
No memory cache
64-bit ready
Multi-core (4 total)
Hyper-threaded (8 total)	 	Board: Hewlett-Packard 1659 10.25
Serial Number: PBZBQ02HT0X0W2
BIOS: Hewlett-Packard F.13 04/25/2011
new USB Storage Use in past 30 Days (mouse over last used for details)	 	new Hosted Virtual Machines (mouse over name for details)
 	Last Used


Drives new – drive encryption	 	Memory Modules c,d
499,79 Gigabytes Usable Hard Drive Capacity
424,32 Gigabytes Hard Drive Free Space

hp DVDRAM GT31L [Optical drive]

Hitachi HTS725050A9A364 [Hard drive] (500,11 GB) -- drive 0, s/n 110627PCK404GLHUH2ZK, rev PC4OCH0A, SMART Status: Healthy
----------------------------------------------------------------

need to know something more?


I have just downloaded ubuntu and installed it. Rebooted the computer and chose to launch with ubuntu instead of windows.
It continued installing (while reading the tour).
Then (probablay when finished) the computer rebooted  and I got the same evil messages as the person who started this thread.

And about that boot script, I haven't directly found where your link is, but since it is getting late I will try that tomorrow.


(I wanted to use linux to become a little more accustomed with computers well solving problems is part of the learning process I guess, but I hoped it wouldn't start that soon)


Thank you!

---

### Post by mao3 on 2011-09-20
I also have the same problem.  The detailed computer specifications for my computer may be found here **[http://tinyurl.com/66efcdp](http://tinyurl.com/66efcdp) **and here is my results.txt                  ```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /wubildr /wubildr.mbr

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600 1,187,858,431 1,187,448,832   7 NTFS / exFAT / HPFS
/dev/sda3       1,187,858,432 1,219,313,663    31,455,232   7 NTFS / exFAT / HPFS
/dev/sda4       1,219,315,649 1,250,050,047    30,734,399   f W95 Extended (LBA)
/dev/sda5       1,219,315,712 1,250,050,047    30,734,336   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        76767C79767C3C45                       ntfs       SYSTEM
/dev/sda2        86CC53E1CC53CA57                       ntfs       
/dev/sda3        140053E80053CF7C                       ntfs       Ubuntu
/dev/sda5        A0B6909BB690740E                       ntfs       RECOVERY

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200

Unknown BootLoader on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 01  |................|
000001c0  c1 ff 07 fe ff ff 3f 00  00 00 00 f8 d4 01 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 
```

---

### Post by Rubi1200 on 2011-09-20
Hi and welcome to the forums mao3 :-)

This is what you need to do from the LiveCD/USB:

go to the terminal and run these commands one at a time hitting Enter each time:

     ```
sudo mkdir /media/win 
sudo mount /dev/sda3 /media/win 
sudo fsck /media/win/ubuntu/disks/root.disk 
```

Once the last command has completed, try and mount the Wubi install:
     
     ```
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt 
```

If this works, you should be able to access all your files and be able to reboot into Ubuntu.

---

### Post by mao3 on 2011-09-21
Hey, when I type the last command in the first code block, this is what I get ```
sudo fsck /media/win/ubuntu/disks/root.disk
fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /media/win/ubuntu/disks/root.disk

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

---

### Post by Curix on 2011-09-21
And what do you do if you have just downloaded and installed it?

---

### Post by Rubi1200 on 2011-09-21
Hi mao3,
after consulting with forum member bcbc, a Wubi expert, I have the following comments to make.

It seems likely that the Wubi install did not complete and that you are facing a possible graphics issue.

Please post the full specifications for the computer, especially RAM and graphics card and then we can take it from there.

Thanks.

---

### Post by mao3 on 2011-09-21
I'm not sure what you mean, but you have to have a ubuntu livecd and click try ubuntu when you boot from cd, then you have to download that boot info script, run it, and it should return a text file you can post on here.

---

### Post by mao3 on 2011-09-21
My previous post was a reply to curix.  I posted a link in my first post that gives the system specs, I haven't added any ram or anything, so the link should have everything you need to know.  I have 6 gigs of ram.

---

### Post by Rubi1200 on 2011-09-21
Sorry, wasn't paying attention there.

Take a look at this thread (posts # 1 and 8) and try setting some boot options:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If you have a dual GPU you may want to try switching it to a single and see if that helps too.

---

### Post by mao3 on 2011-09-22
Hey Rubi1200,

I don't have a dual GPU, but I wanted to update you on something interesting I found.  So, I just got a chance to look at the thread from the computer I'm trying to install Ubuntu on, and I looked at the 8th reply on the thread, which has to do with wubi install boot options.  So the first thing I did was what bcbc suggested, which is edit the normal boot option and add nomodeset before booting, but that didn't work, it just resulted in the same error.

Then I tried booting in safe graphic mode, and here is where I run into something interesting because it would show me command line text of what the installation was doing and the last lines of text it showed were this

```
*PulseAudio configured for per-user sessions saned disabled; edit /etc/defaults/saned
*Starting restore sound card(s') mixer state(s)        [fail]
bad LUN, bad target number stuff
*Enabling additional executable binary formats binfmt-support        [ok]
```And then it just stops and stays there.  I still think there is a problem with the graphics, because when I booted from the livecd the graphics were glitchy when ubuntu was loading, like a game of brick breaker, but this command line text makes me think the problem is the sound card maybe?  Idk, I just thought it would be useful info for you to have to make it easier to help me.  Btw, I appreciate all the help I received thus far.  I feel like I'm making progress even though I'm still not using linux.

---

### Post by mao3 on 2011-09-22
I wanted to give another update.  Most of the boot options described in the thread do not seem to work for me.  I tried simply editing the grub in normal boot mode, but adding nomodeset acpi_osi= or nomodeset acpi_osi="Linux" after quick splash did not work for me (the first one just froze up the command line prompt and the second one resulted in the same error I've been having, which is the ubuntu loading screen would pause and show the bad LUN, bad target number stuff).  I didn't try Windows 2006 since my computer came with Windows 7. 

I then tried editing in safe graphics mode.  The first time, I just added acpi_osi= after xforcevesa and this paused the prompt after the following line ```
[        3.5328] hpet0: 32 comparators, 64-bit 0.232831 MHz counter
```.  Then I tried adding acpi_osi="Linux" after xforcevesa, and that went a bit further, but the bad LUN, bad target number error actually came before the PulseAudio line described in my previous post and it came after something having to do with bluetooth.

I'm scared to try acpi=off, noapic and nolapic seems to be for older computers, and [SIZE=1]vmalloc=xxxM[/SIZE] doesn't seem like it would make sense for my 64 bit machine, so I didn't try those.

So yeah, I'm not really sure what's going on.

---

### Post by Rubi1200 on 2011-09-22
I am not sure what to suggest.

Perhaps try another version of Ubuntu such as 10.10 or 10.04 and see if the same problems occur.

---

### Post by mao3 on 2011-09-24
Hey, yeah, I think I'm going to resort to installing an earlier version and wait for an update to the current version 11 and see if the same error occurs.  So, I got a question.  When I was downloading Ubuntu 11, I was doing so using Wubi, and the partition was created using Windows disk management as opposed to GParted (which I didn't know about at the time).  Would that have any effect on it?  I'm booting from a live CD of Ubuntu 11 now, and I'm considering just creating the partition using GParted and installing from CD, but I don't think that would fix the bad LUN, bad target number error.  I will, however, find out. 

Here is my current boot info script, before installing, if that helps you help me out in any way.
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => MS-DOS 3.30 through Windows 95 (A) is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600 1,187,048,272 1,186,638,673   7 NTFS / exFAT / HPFS
/dev/sda3       1,219,670,926 1,250,258,624    30,587,699   f W95 Extended (LBA)
/dev/sda5       1,219,670,928 1,250,258,624    30,587,697   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        76767C79767C3C45                       ntfs       SYSTEM
/dev/sda2        01CC793C2BFE8180                       ntfs       
/dev/sda5        01CC793C1BE6A200                       ntfs       RECOVERY

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  00 de 00 d8 01 f0 03 60  08 a0 11 00 26 7d 75 3c  |.......`....&}u<|
00000010  5b 29 e9 01 28 05 18 02  f0 06 b8 04 10 3b 80 7b  |[)..(........;.{|
00000020  00 fc 00 14 02 a0 04 c0  09 da 06 af 5a 0b 80 0b  |............Z...|
00000030  48 0c b8 05 08 0c 70 32  a0 33 20 35 20 20 e0 71  |H.....p2.3 5  .q|
00000040  40 4a 00 eb 00 37 80 ab  7c 00 54 40 5a 40 5d 80  |@J...7..|.T@Z@].|
00000050  27 00 5c 00 d6 07 a8 1a  a0 1b f0 1c 80 1c 10 1d  |'.\.............|
00000060  80 13 00 0f e0 d5 74 80  3e c0 2d c0 12 00 28 00  |......t.>.-...(.|
00000070  5b 01 d6 06 dc 06 8c 04  bc 0e 08 09 10 1d 50 1d  |[.............P.|
00000080  00 03 b0 f4 74 00 ba 80  b9 80 c1 00 52 01 b8 01  |....t.......R...|
00000090  94 05 30 3d 40 7f 00 10  01 34 02 30 07 4c 07 f8  |..0=@....4.0.L..|
000000a0  04 fd 03 68 45 00 9c 00  b7 01 4a 00 81 01 a4 03  |...hE.....J.....|
000000b0  70 0c 68 07 a8 1a a0 10  d0 38 c0 39 e0 3a c0 0d  |p.h......8.9.:..|
000000c0  a0 35 b5 60 62 a8 0b 00  05 e0 0b 20 32 c0 1d 00  |.5.`b...... 2...|
000000d0  3d 01 7d 01 bf 01 c8 00  d0 aa 6d 24 a9 6e 01 7d  |=.}.......m$.n.}|
000000e0  01 a8 00 84 01 88 03 a8  0c 18 0d a8 0d e8 0d 28  |...............(|
000000f0  0e c0 09 b0 1d 75 03 94  74 7c 01 a2 00 8c 01 30  |.....u..t|.....0|
00000100  01 40 19 d0 19 d0 1a 80  1b 10 1c 00 06 80 50 6b  |.@............Pk|
00000110  af 93 2a 2e 00 14 a0 2d  00 67 80 e2 00 dc 01 84  |..*....-.g......|
00000120  06 e8 03 f8 0d 63 0f 18  8e f6 9f a9 61 8a 19 91  |.....c......a...|
00000130  9a e6 fb 0d 9f 3c 4a d4  54 c5 9e 4c 4d 55 b4 b4  |.....<J.T..LMU..|
00000140  de 02 8b b0 01 6a 00 e2  69 a4 a6 2a 62 56 6a a6  |.....j..i..*bVj.|
00000150  62 f6 a5 6a 2a e2 4e 2a  ba d0 38 7b 00 f8 00 50  |b..j*.N*..8{...P|
00000160  03 34 03 32 03 e4 01 c0  03 52 03 15 d1 d5 bb 06  |.4.2.....R......|
00000170  9c 3e a3 a9 f9 51 03 15  99 51 d7 a0 c7 0d a7 cc  |.>...Q...Q......|
00000180  47 d5 54 c5 01 53 4d 54  24 c5 d4 6b 45 e4 70 a3  |G.T..SMT$..kE.p.|
00000190  a9 3e d4 90 6d 15 d4 62  c5 7c 80 86 ad 01 94 72  |.>..m..b.|.....r|
000001a0  a9 c7 8a ad 00 4f 62 34  9b 34 35 cd 57 7c b8 c7  |.....Ob4.45.W|..|
000001b0  bc be ca 3b 1a e6 8f 0d  c7 c6 1d b2 56 95 00 01  |...;........V...|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 31 bb d2 01 00 00  |..........1.....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 
```

---

### Post by mao3 on 2011-09-24
Just an update, installed ubuntu, here is the results from boot info script now.
```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos4)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600 1,187,048,272 1,186,638,673   7 NTFS / exFAT / HPFS
/dev/sda3       1,219,670,926 1,250,258,624    30,587,699   f W95 Extended (LBA)
/dev/sda5       1,219,670,928 1,250,258,624    30,587,697   7 NTFS / exFAT / HPFS
/dev/sda4       1,187,049,472 1,219,670,015    32,620,544  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        76767C79767C3C45                       ntfs       SYSTEM
/dev/sda2        01CC793C2BFE8180                       ntfs       
/dev/sda4        63186779-1c70-4c2b-8d2b-725709c636f7   ext4       Ubuntu
/dev/sda5        01CC793C1BE6A200                       ntfs       RECOVERY

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos4)'
search --no-floppy --fs-uuid --set=root 63186779-1c70-4c2b-8d2b-725709c636f7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos4)'
search --no-floppy --fs-uuid --set=root 63186779-1c70-4c2b-8d2b-725709c636f7
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
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 63186779-1c70-4c2b-8d2b-725709c636f7
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=63186779-1c70-4c2b-8d2b-725709c636f7 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 63186779-1c70-4c2b-8d2b-725709c636f7
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=63186779-1c70-4c2b-8d2b-725709c636f7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 63186779-1c70-4c2b-8d2b-725709c636f7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 63186779-1c70-4c2b-8d2b-725709c636f7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 76767C79767C3C45
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 01CC793C2BFE8180
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda5)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 01CC793C1BE6A200
    drivemap -s (hd0) ${root}
    chainloader +1
}
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

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=63186779-1c70-4c2b-8d2b-725709c636f7 /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 574.293712616 = 616.643178496  boot/grub/core.img                             1
 574.400562286 = 616.757907456  boot/grub/grub.cfg                             1
 569.802734375 = 611.821027328  boot/initrd.img-2.6.38-8-generic               5
 574.389804840 = 616.746356736  boot/vmlinuz-2.6.38-8-generic                  1
 569.802734375 = 611.821027328  initrd.img                                     5
 574.389804840 = 616.746356736  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  00 de 00 d8 01 f0 03 60  08 a0 11 00 26 7d 75 3c  |.......`....&}u<|
00000010  5b 29 e9 01 28 05 18 02  f0 06 b8 04 10 3b 80 7b  |[)..(........;.{|
00000020  00 fc 00 14 02 a0 04 c0  09 da 06 af 5a 0b 80 0b  |............Z...|
00000030  48 0c b8 05 08 0c 70 32  a0 33 20 35 20 20 e0 71  |H.....p2.3 5  .q|
00000040  40 4a 00 eb 00 37 80 ab  7c 00 54 40 5a 40 5d 80  |@J...7..|.T@Z@].|
00000050  27 00 5c 00 d6 07 a8 1a  a0 1b f0 1c 80 1c 10 1d  |'.\.............|
00000060  80 13 00 0f e0 d5 74 80  3e c0 2d c0 12 00 28 00  |......t.>.-...(.|
00000070  5b 01 d6 06 dc 06 8c 04  bc 0e 08 09 10 1d 50 1d  |[.............P.|
00000080  00 03 b0 f4 74 00 ba 80  b9 80 c1 00 52 01 b8 01  |....t.......R...|
00000090  94 05 30 3d 40 7f 00 10  01 34 02 30 07 4c 07 f8  |..0=@....4.0.L..|
000000a0  04 fd 03 68 45 00 9c 00  b7 01 4a 00 81 01 a4 03  |...hE.....J.....|
000000b0  70 0c 68 07 a8 1a a0 10  d0 38 c0 39 e0 3a c0 0d  |p.h......8.9.:..|
000000c0  a0 35 b5 60 62 a8 0b 00  05 e0 0b 20 32 c0 1d 00  |.5.`b...... 2...|
000000d0  3d 01 7d 01 bf 01 c8 00  d0 aa 6d 24 a9 6e 01 7d  |=.}.......m$.n.}|
000000e0  01 a8 00 84 01 88 03 a8  0c 18 0d a8 0d e8 0d 28  |...............(|
000000f0  0e c0 09 b0 1d 75 03 94  74 7c 01 a2 00 8c 01 30  |.....u..t|.....0|
00000100  01 40 19 d0 19 d0 1a 80  1b 10 1c 00 06 80 50 6b  |.@............Pk|
00000110  af 93 2a 2e 00 14 a0 2d  00 67 80 e2 00 dc 01 84  |..*....-.g......|
00000120  06 e8 03 f8 0d 63 0f 18  8e f6 9f a9 61 8a 19 91  |.....c......a...|
00000130  9a e6 fb 0d 9f 3c 4a d4  54 c5 9e 4c 4d 55 b4 b4  |.....<J.T..LMU..|
00000140  de 02 8b b0 01 6a 00 e2  69 a4 a6 2a 62 56 6a a6  |.....j..i..*bVj.|
00000150  62 f6 a5 6a 2a e2 4e 2a  ba d0 38 7b 00 f8 00 50  |b..j*.N*..8{...P|
00000160  03 34 03 32 03 e4 01 c0  03 52 03 15 d1 d5 bb 06  |.4.2.....R......|
00000170  9c 3e a3 a9 f9 51 03 15  99 51 d7 a0 c7 0d a7 cc  |.>...Q...Q......|
00000180  47 d5 54 c5 01 53 4d 54  24 c5 d4 6b 45 e4 70 a3  |G.T..SMT$..kE.p.|
00000190  a9 3e d4 90 6d 15 d4 62  c5 7c 80 86 ad 01 94 72  |.>..m..b.|.....r|
000001a0  a9 c7 8a ad 00 4f 62 34  9b 34 35 cd 57 7c b8 c7  |.....Ob4.45.W|..|
000001b0  bc be ca 3b 1a e6 8f 0d  c7 c6 1d b2 56 95 00 01  |...;........V...|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 31 bb d2 01 00 00  |..........1.....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by mao3 on 2011-09-25
Update: My problem has been solved, Ubuntu 11.04 has been installed.  I just did not use Wubi an installed from CD.  That may help anyone else who has the problem.  Also, GParted should be used to make Ubuntu partition from space made in Windows.  That is all :).  But I won't set this thread to solved as I don't know if the other posters have solved their problems.

---

