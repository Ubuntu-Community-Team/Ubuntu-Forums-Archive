---
title: "Grub2 failure after attempting dual boot"
date: 2011-05-22
forum: General Help
---

### Post by kiltedwonder on 2011-05-22
Today I attempted to install Win 7 on my Ubuntu 11.04 machine so I could dual boot.  The Win 7b install went smoothly, but when I tried to fix grub everything went to hell.

I initially tried to reinstall grub using this walk though [http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7]("http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7")  However, when I start the computer I get:

"GNU GRUB version 1.99~rc1-13ubuntu3

Minimal BASH-like line editing is supported....

grub>   "

I tried to use the technique in [http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099") to solve the problems, but when I try to run chroot I get a bin/bash error (I don't have the full error handy, but can rerun the steps if needed).  The only potential cause that I can find doesn't apply to me since I am using a 11.04 64 bit live usb on a 11.04 64 bit install.

At this point I'm stumped.  I've tried a handful of other solutions that failed very quickly and am afraid that at this point I'm only making things worse.

I've run [http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/") and included the results below.  Any help would be greatly appreciated.


[PHP]                                                                    
                                             
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid af159828-5231-4124-9058-95120e719b71 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda1 and looks at sector 872839614 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Operating System:  
    Boot files:        /grub/core.img

sdb1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdb1 and looks at sector 872837086 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>........H.9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 1087896 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdc1 starts at sector 
                       0. But according to the info from fdisk, sdc1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63 3,907,024,064 3,907,024,002  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   778,284,989   778,284,927  83 Linux
/dev/sdb2    *    778,284,990   872,522,279    94,237,290   7 NTFS / exFAT / HPFS
/dev/sdb3         872,522,404   976,768,064   104,245,661   f W95 Extended (LBA)
/dev/sdb5         957,024,243   976,768,064    19,743,822  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4013 MB, 4013948928 bytes
124 heads, 62 sectors/track, 1019 cylinders, total 7839744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             62     7,834,071     7,834,010   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        09ccaf47-1c68-4c86-be0b-aea895720a70   ext3       
/dev/sdb1        af159828-5231-4124-9058-95120e719b71   ext3       
/dev/sdb2        765FCB484DC9B834                       ntfs       
/dev/sdb5        d47fa886-e3e3-4b6c-97f8-f365b02ad6c9   swap       
/dev/sdc1        57CD-E451                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt/boot                ext3       (rw)
/dev/sdb1        /media/af159828-5231-4124-9058-95120e719b71 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /mnt                     ext3       (rw)
/dev/sdb2        /media/765FCB484DC9B834  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,umask=0077,dmode=0500)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  63.128913403 = 67.784154624   grub/core.img                                  1

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdc1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

label ubnentry6
menu label Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry7
menu label Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --

label ubnentry8
menu label Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --

--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb3

00000000  49 4c 26 bb c6 80 72 02  06 5a 4c e8 a0 4b 5c f7  |IL&...r..ZL..K\.|
00000010  b3 ca 7f a1 69 d3 a7 71  6c 70 4e 50 71 f3 17 5a  |....i..qlpNPq..Z|
00000020  ed 8e d3 2b 99 db 34 ff  12 03 90 c8 51 2e 9c c9  |...+..4.....Q...|
00000030  c1 9e 6a c6 35 10 39 cd  03 62 c5 84 f8 ee a6 c9  |..j.5.9..b......|
00000040  91 59 09 c6 88 2c d8 84  f6 01 0d 3b c4 6e 39 e0  |.Y...,.....;.n9.|
00000050  d9 a5 08 2a f4 1f 2f fe  0b 57 75 85 ac 34 cf db  |...*../..Wu..4..|
00000060  51 b2 43 6c ec 0a 55 5e  91 33 23 96 94 e4 e9 4d  |Q.Cl..U^.3#....M|
00000070  5b c9 93 f6 5b 1c d1 20  94 50 e9 db 92 86 3f 26  |[...[.. .P....?&|
00000080  0e 83 fc 62 8b 85 0a 2d  8d ac 8f fe ad a0 99 1b  |...b...-........|
00000090  56 2a 63 91 a3 31 56 54  74 4d 2f 57 0b 8f 19 6d  |V*c..1VTtM/W...m|
000000a0  4a 46 35 4d 23 6a b3 28  1f 29 41 29 a8 9d 0e 0f  |JF5M#j.(.)A)....|
000000b0  0f 0e a2 07 e7 05 38 87  c0 d7 c3 f8 78 78 78 60  |......8.....xxx`|
000000c0  02 10 66 a6 49 25 4d a0  42 53 a0 ad c9 43 d9 40  |..f.I%M.BS...C.@|
000000d0  31 3f fb 52 01 c0 6f 52  f3 24 d2 9e d7 7c 0e 4f  |1?.R..oR.$...|.O|
000000e0  62 c8 9f d5 57 c8 b0 58  e7 a2 36 e2 0d 60 6d 45  |b...W..X..6..`mE|
000000f0  29 91 7a 58 d2 57 cd 8a  b7 12 d3 8c ca ac 11 2d  |).zX.W.........-|
00000100  f5 a6 72 61 c3 db 48 97  20 57 48 f4 d9 16 c8 d2  |..ra..H. WH.....|
00000110  cb 75 f5 26 c0 b5 fb 54  87 14 c2 4e d7 68 81 4c  |.u.&...T...N.h.L|
00000120  42 c6 35 7f 61 5b 9f b9  38 c3 16 9f 91 25 da 06  |B.5.a[..8....%..|
00000130  b2 5f 7a 99 21 5a df 96  31 9a 21 83 52 61 dd 00  |._z.!Z..1.!.Ra..|
00000140  76 08 c8 6c c7 4b 53 29  a6 2e 3f 99 ce 5e 00 59  |v..l.KS)..?..^.Y|
00000150  87 74 8d ff d2 7b 4f ec  3f 74 bf e2 87 d1 99 61  |.t...{O.?t.....a|
00000160  8c 5d a0 0c 81 cc 11 ea  c2 66 b1 18 21 d2 55 72  |.].......f..!.Ur|
00000170  63 68 54 c7 1b 4a 9a 45  4a 70 5b 2a 6b 09 06 b4  |chT..J.EJp[*k...|
00000180  1f 29 71 f9 a0 ad 0e 0f  0f 0d a2 24 46 a2 5f c3  |.)q........$F._.|
00000190  c3 c3 c3 f8 78 17 f8 60  01 d7 a9 7b 4a ae 37 60  |....x..`...{J.7`|
000001a0  25 43 b0 a5 bc ba 28 0d  e3 d2 0b 06 eb c0 b0 b9  |%C....(.........|
000001b0  cb d5 2a b4 ff 6f 72 f2  01 94 cc c9 bf e5 00 fe  |..*..or.........|
000001c0  ff ff 82 fe ff ff 4f 65  09 05 4e 44 2d 01 00 00  |......Oe..ND-...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg sdh 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 2457: cd: /media/af159828-5231-4124-9058-95120e719b71
/mnt/: No such file or directory
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
[/PHP]

---

### Post by Hedgehog1 on 2011-05-22
Thanks for including the script output in your first post. Save so much time. :KS  :KS

You may have a little clean up to do because you installed some of grub in the Windows partition:

```
sdb2: __________________________________________________________________________ 

    File system:       ntfs 
    Boot sector type:  Windows Vista/7 
    Boot sector info:   No errors found in the Boot Parameter Block. 
    Operating System:  Windows 7 
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe  
                       **/boot/grub/core.img**
```

But to get you booting correctly, please do the following:

Boot from the **11.04** LiveCD/LiveUSB.

Then do:

```
sudo mount /dev/sda1 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sda
```

Then reboot into Ubuntu from the hard disk and do this to add windows to the grub menu:

```
sudo update-grub
```


***The Hedge***

:KS

---

### Post by kiltedwonder on 2011-05-22
Thanks for the help!  Unfortunately, I've already tried that set of commands.  I believe that is how I ended up with the boot record in the windows partition, because I tried several variations to see if I accidently installed to the wrong drive.

When I run those commands and restart I get:

> GNU GRUB version 1.99~rc1-13ubuntu3

Minimal BASH-like line editing is supported. For the first word, TAB listspossible command completions. Anywhere else tab lists possible device or file completions.

grub>

---

### Post by kiltedwonder on 2011-05-22
I also tried to use the solution here: [http://techgage.com/news/repairing_a_broken_grub_2_boot-loader_on_ubuntu/]("http://techgage.com/news/repairing_a_broken_grub_2_boot-loader_on_ubuntu/").

When I run 

```
grub> ls
``` 

I get:

```
(hd0) (hd0,msdos5) (hd0,msdos2) hd0,msdos1) (hd1) (hd1,msdos1)
```

I don't know if that matters, but the other references I've seen list them as (hd0,1) etc.

Then when I get to 

```
grub> ls /boot
```

with 
```
prefix=(hd0,msdos1)/boot/grub
root=hd0,msdos1
```

I get ```
grub/
```

and with 
```
prefix=(hd0,msdos2)/boot/grub
root=hd0,msdos2
```

I get 
```
fi-FI/ BCD BCD.LOG BCD.LOG1 BCD.LOG2 BOOTSTAT.DAT cs-CZ/ da-DK/ de-DE/ el-GR/ en-US/ es-ES/ Fonts/ fr-FR/ hu-HU/ it-IT/ ja-JP/ ko-KR/ memtest.exe nb-NO/ nl-NL/ pl-PL/ pt-BR/ pt-PT/ ru-RU/ sv-SE/ tr/TR/ zh-CN/ zh-HK/zh-TW/
```

Don't know if that helps, but it might.

---

### Post by AlmightyHeretic on 2011-05-22
I probably won't be much help here but can't you run Ubuntu 11.04 Live and do a "reinstall"? I'm pretty sure there's an option during the install that allows you to preserve your files.

---

### Post by oldfred on 2011-05-22
You seem to have parts of grub2 installed, but no kernels or fstab are shown. Or you do not have a full install.

You have to remove the grub entry from windows as Hedgehog1 mentioned.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

Windows gets confused with /Boot and /boot as it is not case sensitive.

---

### Post by kiltedwonder on 2011-05-22
I saw some references to that strategy and remember the option from way back, but couldn't figure out how to do it when I tried to install.  I was using a usb made via unetbootin... would there be a different set of initial options with the live cd or a usb made through the Ubuntu utility?

---

### Post by kiltedwonder on 2011-05-22
Oldfred - Thanks for the link.  I renamed /boot on my windows partition.  When I restarted I got the same "grub>" prompt that I have been getting all along.  

To avoid unintentionally screwing things up further, which procedure should I try next?

Edit:  I probably should add that currently the results for "grub> set" is:

```
color_highlight=black/white
color_normal=white/black
pager=
prefix=(hd1,msdos1)/boot/grub
root=hd1,msd1
```

---

### Post by oldfred on 2011-05-22
I think you have to reinstall Ubuntu as it looks like major parts are missing. If you just want to boot windows for now, then reinstall a windows boot loader to the MBR.

Grub has to have a grub.cfg file in the / (root) partition (or boot partition but it is not normally recommended for desktops). Then grub.cfg has to find the kernel & init files to boot. It also does not show an fstab. All those are not shown in boot script in any Linux partition.

I would just try a reinstall. Use manual or 'Something Else' to reuse existing partitions.

---

### Post by linuxinstalledfromhdd on 2011-05-22
What you needed to do was install Windows first and then install Ubuntu. I've never tried it with Windows last. I've read that it is nearly impossible.

---

### Post by kiltedwonder on 2011-05-23
Oldfred - Thanks for the help.  Is there a way to save all my current settings when I reinstall?  That's my biggest concern about nuking the install.

linuxinstalledfromhdd - I've done it several times in the past, but that was before grub2 and with XP not Win 7.  So far for me grub2 has been a huge pain in the ***.   I think I've experience every major bug that was reported.  I know it's more advanced, but I wish they'd waited until it was more mature before switching to it.

---

### Post by linuxinstalledfromhdd on 2011-05-23
I hear you. But I think you would have better results if you installed Windows first and then Ubuntu.  That always works for me.  The worst it has ever been is I need to run a sudo os-prober and fdisk it again just to make sure everything looks perfect.  Horse before the cart.

---

### Post by oldfred on 2011-05-23
If you put the windows boot loader back in and can boot windows then you do not have to reinstall that.

You can copy all your data with a liveCD to another device.


Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing testdisk with Synaptic.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by kiltedwonder on 2011-05-23
Oldfred - Your last comment lost me a bit.  In theory I understand how to pull my files (not config type files though) off via the liveCD.  However, my Ubuntu partition won't mount and is showing up as unallocated in gparted.  Will your procedure take care of this?

> Restore basic windows boot loader - universe enabled
 Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing testdisk with Synaptic.
 sudo apt-get install lilo
 sudo lilo -M /dev/sda mbr
 May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

Just to be clear, am I supposed to be doing this via the liveCD after moving the files I need to save to another disk?

---

### Post by dragonfly41 on 2011-05-23
> 
What you needed to do was install Windows first and then install Ubuntu.  I've never tried it with Windows last. I've read that it is nearly  impossible.

I would second this since I've just gone through this .. I tried installing ubuntu first, then Win XP second and boot was screwed up .

I had to then reinstall ubuntu to get back to the Grub dual boot menu.

You might find **[COLOR=black]grub customizer[/COLOR]** useful to view the Grub menu options..

---

### Post by linuxinstalledfromhdd on 2011-05-23
I keep seeing messages from users doing it the wrong way constantly.  I don't get it.  Just make a rule and say this is the right way to do this.

---

### Post by kiltedwonder on 2011-05-23
Installing Windows first wasn't really an option.  This computer has been an Ubuntu machine since Breezy and two motherboards and two hdd later I only had to reinstall once... prior to this.

---

### Post by dragonfly41 on 2011-05-23
e.g. if Windows crashes in a dual boot configuration and has to be reinstalled?   Should this scenario demand a reinstallation of ubuntu running in separate partitions?

---

### Post by kiltedwonder on 2011-05-23
Exactly.  Or in my case I had a perfectly functional long running Ubuntu installation.  Why would I expect to have to reinstall Ubuntu so I can dual boot.  I didn't have to back with XP and grub.  

At this point for me it's just crying over spilled milk.  I just need to get things back up and running.

---

### Post by linuxinstalledfromhdd on 2011-05-23
If your windows crashes that often, I wouldn't use it anymore.

---

### Post by kiltedwonder on 2011-05-23
Thanks for the tip.  I just tried grub customizer, but it's no help at this point because my original ubuntu partition is listed as unallocated.  I'll try it once I get the ubuntu installation working.

---

### Post by oldfred on 2011-05-23
The lilo boot loader will only let you directly boot windows if it is bootable. If gparted will not see the windows NTFS partition, it may mean it is damaged and needs chkdsk from a windows repairCD. Linux will not mount NTFS partitions with chkdsk flag set to prevent more damage that chkdsk may not then be able to repair.

If the partition you cannot mount is linux then you may need to run e2fsck.

---

### Post by kiltedwonder on 2011-05-23
Lilo got my Win 7 install working!! (I never thought I'd be that excited about a Windows install).  

The partition I can't mount is my primary Ubuntu partition.  I've never used e2fsk and haven't found a reference that points me in the right direction (so far).

Looking at [this reference]("http://linux.die.net/man/8/e2fsck"), it appears I need to use the -p option.  Is that correct?  Should my code be:```
e2fsk -p /dev/sda3
```

---

### Post by oldfred on 2011-05-23
This is what I have in my notes:

From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by kiltedwonder on 2011-05-23
Both of those return:
```
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda3
Could this be a zero-length partition?

```

checking with fdisk yields:

```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda3
ubuntu@ubuntu:~$ sudo fdisk -s /dev/sda3
1

```

If I'm correct this means that it thinks there are no partitions and the size of the drive is 1.  Am I reading that correctly?

I checked /etc/fstab:

```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
```

Looking at gparted, it appears that the swap partition (/dev/sda5) is inside /dev/sda3 and so is the unallocated ubuntu partition that contains the OS itself.  Is that normal?

Also the device information in case it is helpful:

```
Device Information
Model:     ATA ST300630A
Size:      465.76 GiB
Path:      /dev/sda

Partition table:  msdos
Heads:            255
Sectors/track:    63
Cylinders:        60801
Total Sectors:    976773168
Sector size:      512
```

---

### Post by oldfred on 2011-05-23
According to the boot script sdb3 was the extended partition. You cannot run e2fsck on an extended partition as it is just a container for logical partitions. You have to run it on any of the ext2, ext3 or ext4 family of formats for Linux partitions.

---

### Post by kiltedwonder on 2011-06-16
Sorry I've taken so long to say thank you for your help.  I finally gave up and reinstalled Ubuntu.  thanks again for all the help.

---

