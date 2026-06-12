---
title: "Partitions"
date: 2011-07-15
forum: General Help
---

### Post by jmacx81 on 2011-07-15
Ok here is what I want to do. I want to make a new partition that I can read and write to from Ubuntu 11.04 and Windows 7. I haven't used Ubuntu much since 8.10 and it seems that I remember it being much easier to do then. I'm using this partition to store my music, pictures and videos on if that is of any relevance. I also need this to be something that can't mess up my windows side of my computer as I need that for work... Thanks in advance!

---

### Post by Blasphemist on 2011-07-15
I've done just what you are asking about. You'll need a ntfs partition for this as windows can't read and write to a EXTx (where x is 2, 3 or 4) partition that we normally use for linux. If necessary your existing windows would suffice but isn't what I recommend. Please post a screen shot from GParted to provide some detail. I've posted mine here. sda6 is my shared data partition. Also, please tell me if you are using normal dual boot or wubi.

---

### Post by dabl on 2011-07-15
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

In the left topic list, under "Next Steps", see "Mount Windows".

---

### Post by jmacx81 on 2011-07-15
I am running a normal dual boot through grub

---

### Post by jmacx81 on 2011-07-15
> **dabl said:**
> [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

In the left topic list, under "Next Steps", see "Mount Windows"..

Tried that and it isn't working out.. Not quite sure why, This is the way I remember doing it in 8.10 though.

---

### Post by Blasphemist on 2011-07-15
Are you sure about the normal dual boot? Do you have a second drive? This drive looks like it's all windows. Please download and run this bootinfoscript and post its results in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by jmacx81 on 2011-07-15
```
mac@ubuntu:~$  sudo bash ~/Desktop/boot_info_script.sh
[sudo] password for mac: 

boot_info_script version: 0.60        [17 May 2011]

Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda2/Wubi for information... 
Searching sda3 for information... 
Searching sda4 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/mac/Desktop/".

mac@ubuntu:~$ 

```

I'm pretty sure it's normal boot... I didn't do anything special when I set it up.

---

### Post by jmacx81 on 2011-07-15
```
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
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   944,406,527   943,996,928   7 NTFS / exFAT / HPFS
/dev/sda3         944,406,528   976,560,127    32,153,600   7 NTFS / exFAT / HPFS
/dev/sda4         976,560,128   976,771,119       210,992   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       7441344b-c3f9-492f-af52-3e4efc18ab68   ext4       
/dev/sda1        4426AC9826AC8C8C                       ntfs       SYSTEM
/dev/sda2        3CBE3ED2BE3E8484                       ntfs       
/dev/sda3        CEB8B630B8B61745                       ntfs       RECOVERY
/dev/sda4        9060-EADB                              vfat       HP_TOOLS

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /media/SYSTEM            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda3        /media/RECOVERY          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


======================== sda2/Wubi/boot/grub/grub.cfg: =========================

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
insmod ntfs
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 3CBE3ED2BE3E8484
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ntfs
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 3CBE3ED2BE3E8484
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-10-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 3CBE3ED2BE3E8484
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-10-generic root=UUID=3CBE3ED2BE3E8484 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, Linux 2.6.38-10-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 3CBE3ED2BE3E8484
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-10-generic root=UUID=3CBE3ED2BE3E8484 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, Linux 2.6.35-30-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 3CBE3ED2BE3E8484
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-30-generic root=UUID=3CBE3ED2BE3E8484 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.35-30-generic
}
menuentry "Ubuntu, Linux 2.6.35-30-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 3CBE3ED2BE3E8484
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-30-generic root=UUID=3CBE3ED2BE3E8484 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.35-30-generic
}
menuentry "Ubuntu, Linux 2.6.32-32-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 3CBE3ED2BE3E8484
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-32-generic root=UUID=3CBE3ED2BE3E8484 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-32-generic
}
menuentry "Ubuntu, Linux 2.6.32-32-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 3CBE3ED2BE3E8484
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-32-generic root=UUID=3CBE3ED2BE3E8484 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-32-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 3CBE3ED2BE3E8484
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=3CBE3ED2BE3E8484 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 3CBE3ED2BE3E8484
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=3CBE3ED2BE3E8484 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 4426AC9826AC8C8C
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 3CBE3ED2BE3E8484
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root CEB8B630B8B61745
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

============================= sda2/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
/dev/sda2	/host	fuseblk	defaults,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096	0	0
/dev/sda3	/media/RECOVERY	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
/dev/sda1	/media/SYSTEM	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
/host/ubuntu/disks/root.disk	/	ext4	loop,errors=remount-ro	0	1
/host/ubuntu/disks/swap.disk	none	swap	loop,sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0


--------------------------------------------------------------------------------

================= sda2/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

   1.939384460 = 2.082398208    boot/grub/grub.cfg                             1
   0.831676483 = 0.893005824    boot/initrd.img-2.6.31-14-generic              2
   4.769084930 = 5.120765952    boot/initrd.img-2.6.32-32-generic              2
   6.469051361 = 6.946091008    boot/initrd.img-2.6.35-30-generic              2
   5.379455566 = 5.776146432    boot/initrd.img-2.6.38-10-generic              2
   2.314220428 = 2.484875264    boot/vmlinuz-2.6.31-14-generic                 1
   5.430709839 = 5.831180288    boot/vmlinuz-2.6.32-32-generic                 1
   5.316535950 = 5.708587008    boot/vmlinuz-2.6.35-30-generic                 1
   7.758125305 = 8.330223616    boot/vmlinuz-2.6.38-10-generic                 1
   5.379455566 = 5.776146432    initrd.img                                     2
   6.469051361 = 6.946091008    initrd.img.old                                 2
   7.758125305 = 8.330223616    vmlinuz                                        1
   5.316535950 = 5.708587008    vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 ce 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 20 35 3a  |........?.... 5:|
00000020  30 38 03 00 19 03 00 00  00 00 00 00 02 00 00 00  |08..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 db ea 60 90 4e  4f 20 4e 41 4d 45 20 20  |..)..`.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200



```

---

### Post by westie457 on 2011-07-15
At the moment you have 4 primary partitions and that unfortunately is the limit. To make another partition you are going to have to lose one and create an extended partition. This is not strictly necessary as you have a Wubi installation inside Windows even if the Ubuntu installation is on a separate hard drive. One work around for you could be to create a directory in for example the /host partition (sda2) and move all your personal files to here.

                    =================================================================
Scrub all of the above. It does not apply at all.

---

### Post by Blasphemist on 2011-07-15
That is a wubi install. Just goes to show how long ago 2008 is, that you don't remember doing that.

The answer for you is this, when you are using wubi. [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
> **How do I access the Windows drives?**
The Windows partition where you installed Wubi is available as /host within Ubuntu (Places > Computer > File System > Host) All the other partitions will be available under Places > Removable Media

**How can I access the Wubi files from Windows?**
There are a few Windows applications that can mount ext2-based file systems. See for instance:

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

[http://www.fs-driver.org/](http://www.fs-driver.org/)

[http://ext2read.sf.net](http://ext2read.sf.net) (has ext4 support)

The relevant Wubi files you need to access are located under C:\ubuntu\disks\


The better answer to me is to migrate to dual boot. That is a fairly involved thing to do and there are options for doing it. Before we go that way, please comment.

---

### Post by jmacx81 on 2011-07-15
Yeah man I didn't think I had ever heard of wubi. I found all my stuff on my windows partition now, next question is if I move songs around from my download folder to my music folder or download more music through Ubuntu and save it there will this cause any issues on the windows 7 side when I boot windows?

---

### Post by jmacx81 on 2011-07-15
also along the way of trying to do this I created a shortcut to one partition that has rendered itself useless to me I have attached a picture of the screen shot. It is right above the trash can. How can I remove this icon?

---

### Post by westie457 on 2011-07-15
> **jmacx81 said:**
> Yeah man I didn't think I had ever heard of wubi. I found all my stuff on my windows partition now, next question is if I move songs around from my download folder to my music folder or download more music through Ubuntu and save it there will this cause any issues on the windows 7 side when I boot windows?

If you are happy with the Wubi installation then you need to resize the /host partition (sda2) giving the space back to your Windows partition to allow the storage of all your files inside Windows.

Here is a link to a guide.

 [http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

---

### Post by westie457 on 2011-07-15
> **jmacx81 said:**
> also along the way of trying to do this I created a shortcut to one partition that has rendered itself useless to me I have attached a picture of the screen shot. It is right above the trash can. How can I remove this icon?

Right click remove from panel

---

### Post by jmacx81 on 2011-07-15
The size is ok for windows.. I have a very small partition for Ubuntu... Can I follow these steps in the link to make my Ubuntu size larger?

---

### Post by jmacx81 on 2011-07-15
> **westie457 said:**
> Right click remove from panel

right click opens a menu and the only option available is "open"

---

### Post by Blasphemist on 2011-07-15
I haven't found a way to not display the icon. Could you describe what it was that you did to create it and why it is now not needed?

Yes, the wiki links to this thread for resizing the ubuntu wubi partition. There is more than one way to do it. [http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

---

### Post by jmacx81 on 2011-07-15
I was trying to create a shortcut to access the windows partition and that's what I came up with. Attached is a screen shot of what it opens.

---

### Post by jmacx81 on 2011-07-15
well attached now

---

### Post by Blasphemist on 2011-07-15
How did you do it? Did you add it to fstab? I don't know how to keep it from showing up unless we undo what you did.

---

### Post by jmacx81 on 2011-07-15
well I might have to live with it cause honestly I have no idea..

---

### Post by jmacx81 on 2011-07-15
It possibly may have been something on this site...

[http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html]("http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html")

---

### Post by Blasphemist on 2011-07-15
Try this for me then.

Let's see if it's in the fstab file and if we can remove it.

```
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab

```

This will open a gui for editing the fstab file after you have backed it up. See if you see the entry for that. If you're not sure, post the contents of the file in quote tags and we'll look at it. The line could be deleted, the file saved and it might take a reboot but it should be gone, if it is there to remove.

---

### Post by flemur13013 on 2011-07-15
Make the windows partition with windows or a windows boot CD/DVD.

FWIW, here's my fstab line for a partition created in Win7:
UUID=2B2etc.etcEF     /ntfs    ntfs    defaults   0   2

(Change UUID and "/ntfs" to suit yourself)

---

### Post by jmacx81 on 2011-07-15
contents

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
/dev/sda2	/host	fuseblk	defaults,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096	0	0
/dev/sda3	/media/RECOVERY	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
/dev/sda1	/media/SYSTEM	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
/host/ubuntu/disks/root.disk	/	ext4	loop,errors=remount-ro	0	1
/host/ubuntu/disks/swap.disk	none	swap	loop,sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0


```

---

### Post by Blasphemist on 2011-07-15
> **jmacx81 said:**
> contents

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
/dev/sda2	/host	fuseblk	defaults,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096	0	0
/dev/sda3	/media/RECOVERY	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
/dev/sda1	/media/SYSTEM	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
/host/ubuntu/disks/root.disk	/	ext4	loop,errors=remount-ro	0	1
/host/ubuntu/disks/swap.disk	none	swap	loop,sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0


```
Put a # in front of the /dev/sda3 and /dev/sda1 lines and you should see both of those leave nautilus and the offender leave the launcher. I don't think you'll have to remove the lines, I think you can just use the # to remark them out.

---

### Post by jmacx81 on 2011-07-15
That worked! Thanks...

---

### Post by Blasphemist on 2011-07-15
Great! You gotta love that. You should mark the thread solved now.

---

