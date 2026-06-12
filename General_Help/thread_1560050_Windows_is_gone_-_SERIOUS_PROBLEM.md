---
title: "Windows is gone - SERIOUS PROBLEM"
date: 2010-08-24
forum: General Help
---

### Post by DManX04 on 2010-08-24
My second partition, on which Windows Vista was sitting, is now listed as completely free. Windows Vista no longer shows up on the Grub menu, and I can't mount the partition that it was on. I haven't booted to Windows in a while, but I'm not sure how long ago this happened. My best guess would be that it was sometime in the last 3-4 weeks. I don't know whether I've mounted the partition in Ubuntu since the last time I actually booted to it. Other than accessing it to play music off of, and occasionally saving documents to it, I never used the partition for much.

Does anyone have any suggestions on what I should do? I think I'm mostly backed up, but I do need Windows from time to time, and I don't want to have to risk losing anything that I haven't backed up recently.

---

### Post by stlsaint on 2010-08-24
Considering that harddrives DO NOT erase themselves on their own i must ask what changes to your drive have you made in these last 3-4 weeks that may have done this? Also what is causing you to not be able to mount the drive either in ubuntu or via livecd?
(meaning please provide errors you are getting)

---

### Post by DManX04 on 2010-08-24
I don't get any error messages because there is nothing to mount. The partition that Windows was on is just not there. When I go to Disk Utility, it says that the 125Gb partition is empty. There is no option to boot to Windows in the Grub menu.

As far as what I've done, I really can't think of anything. From a strictly hardware perspective, I took the computer apart to clean the fans, but that's it. When I did that, I didn't disconnect the hard drives or even touch them really. As far as software goes, other than installing some programs in Ubuntu, I've done nothing. The computer has failed to come out/go into of sleep mode a few times, and I've had to hard reboot. But no version of Ubuntu has ever worked well with my sleep mode, so that's nothing new. I've restarted after failure to wake up from sleep mode countless times in the last 2+ years. I've also run the Disk Utility a few times. I've run the self tests, and I've also tried to check and repair the file systems, but it never worked for that partition. I'm also almost positive that I've used the Windows partition since I did that.

---

### Post by Rubi1200 on 2010-08-24
Do you have an Ubuntu CD?

If yes, boot the computer making sure BIOS is set to boot from the CD drive.

Choose to try Ubuntu not install.

Then, post the results of the bootscript linked to at the bottom of my post.

The results should tell us what is going on.

Thanks.

---

### Post by DManX04 on 2010-08-24
I think I have the live CD at home. Does it matter if it's a 10.04 CD?

In the meantime, would installing testdisk on my Ubunutu partition be a problem for recovering the Windows partition? As in, would it possibly harm any of the data I'm hoping to get back? For that matter, how much of a problem is it that I've installed several programs in the last few weeks before I saw this problem? I guess I'd just always assumed that the partitions were completely separate, but now I realize that I have no idea.

---

### Post by stlsaint on 2010-08-24
I would suggest running that script and posting the results before installing more programs. Also no it does not matter what livecd you use.

---

### Post by Rubi1200 on 2010-08-24
I agree with stlsaint; please don't mess around with anything until we see the results of the bootscript.

---

### Post by DManX04 on 2010-08-24
Cool. Thanks a lot guys. I'll post that information as soon as I can get home and get the LiveCD.

---

### Post by DManX04 on 2010-11-02
I know this was "urgent" like two months ago, but I couldn't get Brasero to properly burn me a new LiveCD until a few days ago.

Here's the output of that boot script.

```
        Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.
 => No boot loader? is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *    306,279,288   312,576,704     6,297,417   c W95 FAT32 (LBA)
/dev/sda2         306,279,286   312,576,704     6,297,419   f W95 Ext d (LBA)
/dev/sda5         306,279,288   312,576,704     6,297,417  dd Dell Media Direct
/dev/sda3                  63     4,321,484     4,321,422  82 Linux swap / Solaris
/dev/sda4           4,323,328    62,908,415    58,585,088  83 Linux

/dev/sda1 overlaps with /dev/sda2

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2004 MB, 2004877312 bytes
16 heads, 32 sectors/track, 7648 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,064     3,915,775     3,907,712   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D9-0916                              vfat       MEDIADIRECT                   
/dev/sda2: PTTYPE="dos" 
/dev/sda3        686fc6a5-4234-4a18-a9cb-ee28b3dbaefd   swap                                     
/dev/sda4        6e71543f-fe9e-44d5-a91c-a6bfde778573   ext4                                     
/dev/sda5        07D9-0916                              vfat       MEDIADIRECT                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        95C5-AD2E                              vfat       USB DISK                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/Ubuntu 10.10 i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdb1        /media/USB DISK          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 6e71543f-fe9e-44d5-a91c-a6bfde778573
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 6e71543f-fe9e-44d5-a91c-a6bfde778573
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 6e71543f-fe9e-44d5-a91c-a6bfde778573
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=6e71543f-fe9e-44d5-a91c-a6bfde778573 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 6e71543f-fe9e-44d5-a91c-a6bfde778573
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=6e71543f-fe9e-44d5-a91c-a6bfde778573 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 6e71543f-fe9e-44d5-a91c-a6bfde778573
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=6e71543f-fe9e-44d5-a91c-a6bfde778573 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 6e71543f-fe9e-44d5-a91c-a6bfde778573
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=6e71543f-fe9e-44d5-a91c-a6bfde778573 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 6e71543f-fe9e-44d5-a91c-a6bfde778573
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 6e71543f-fe9e-44d5-a91c-a6bfde778573
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda4       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=686fc6a5-4234-4a18-a9cb-ee28b3dbaefd none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


  17.4GB: boot/grub/core.img
  18.2GB: boot/grub/grub.cfg
  24.3GB: boot/initrd.img-2.6.32-25-generic
  24.6GB: boot/initrd.img-2.6.35-22-generic
  20.5GB: boot/vmlinuz-2.6.32-25-generic
  20.4GB: boot/vmlinuz-2.6.35-22-generic
  24.6GB: initrd.img
  24.3GB: initrd.img.old
  20.4GB: vmlinuz
  20.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  93 71 b9 9b 00 94 9a 03  0b 12 5d 9a 16 b5 10 4a  |.q........]....J|
00000010  32 6b c4 76 a5 50 72 32  b5 c1 90 86 d9 ca e0 ca  |2k.v.Pr2........|
00000020  81 ec 05 c1 d0 01 88 ae  fa e5 47 28 55 20 c2 24  |..........G(U .$|
00000030  42 33 25 98 94 0f 49 c6  f2 a1 28 d9 e4 a8 04 d1  |B3%...I...(.....|
00000040  f4 44 5c 60 4c 2a b4 41  2b ac a8 fc d3 b1 03 53  |.D\`L*.A+......S|
00000050  84 82 08 7a cd 16 a3 4e  99 91 44 83 52 da 15 4f  |...z...N..D.R..O|
00000060  03 c5 88 0b 8b c7 cc 92  40 ab 67 d4 ec 3b 27 15  |........@.g..;'.|
00000070  84 f5 cc 9c 98 16 9a 8c  c8 74 1e 89 26 e7 47 eb  |.........t..&.G.|
00000080  c8 71 97 4a 62 09 70 ed  b3 83 66 0a c4 aa c6 55  |.q.Jb.p...f....U|
00000090  43 83 60 65 a2 e4 66 01  f9 0d 50 d4 7a f1 59 02  |C.`e..f...P.z.Y.|
000000a0  08 c8 24 c8 8f 7a ad 15  ce cb 25 65 84 b5 d1 a5  |..$..z....%e....|
000000b0  1f ce db 4a 9c 82 4c 22  94 f4 c7 31 83 c8 02 27  |...J..L"...1...'|
000000c0  74 ca 28 29 8b 0e 8b 4b  31 5a f6 99 98 ce 83 08  |t.()...K1Z......|
000000d0  d7 19 8d ad 6e b7 9e c2  f8 fd 3d 46 bb 62 8c f8  |....n.....=F.b..|
000000e0  33 48 79 2f 73 51 9d ae  91 ed a8 93 89 5e f3 64  |3Hy/sQ.......^.d|
000000f0  f5 97 59 13 c0 2c a1 ac  af 4e 63 aa 1c 88 c7 16  |..Y..,...Nc.....|
00000100  26 08 a5 ec 70 b8 e9 8e  0d 3c 46 34 27 78 70 2f  |&...p....<F4'xp/|
00000110  a2 54 9c 21 68 c3 99 5d  17 26 f2 be 3b 32 54 ee  |.T.!h..].&..;2T.|
00000120  ae 2e 0f 43 cd 58 f1 f0  5c b5 a2 28 12 c1 3e 86  |...C.X..\..(..>.|
00000130  4a a2 a9 18 eb f6 b1 9e  a5 2a 29 52 15 26 5c 5b  |J........*)R.&\[|
00000140  76 23 23 12 0d 88 0f ba  fa f2 f4 2d 58 f9 2e 8b  |v##........-X...|
00000150  87 70 5c 5b 85 4b 14 98  2a 26 f4 ad 17 56 bc 7a  |.p\[.K..*&...V.z|
00000160  84 6e a9 d7 8a c2 18 d2  8c ce 85 d5 c8 a9 09 34  |.n.............4|
00000170  f1 b4 48 91 2c 66 1c 3f  34 43 3e 8f 48 6e 17 e5  |..H.,f.?4C>.Hn..|
00000180  2b 66 05 82 a9 ff fa e2  04 da eb c5 80 06 a2 68  |+f.............h|
00000190  d6 7b 0f 63 98 cd 4d 1b  2d 3d ec 6f 27 39 f9 34  |.{.c..M.-=.o'9.4|
000001a0  0e 65 ed c3 be 34 6b b4  f6 3f 84 d9 8d 1b 34 25  |.e...4k..?....4%|
000001b0  16 60 85 39 c6 2c 3d c6  90 9c 93 56 8c d2 00 fe  |.`.9.,=....V....|
000001c0  ff ff dd fe ff ff 02 00  00 00 49 17 60 00 00 00  |..........I.`...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by DManX04 on 2010-11-02
Bump. Any help would be great.

---

### Post by DManX04 on 2010-11-03
Bump.

---

### Post by lindsay7 on 2010-11-03
I would think that your windows boot loader is bad or changed,  Follow the instructions on fixing your windows bootloader in this link, after you do that and you can boot into windows successfully, you will need to follow the instructions in the link to re install grub,

[http://ubuntuforums.org/showpost.php?p=6391959&postcount=1](http://ubuntuforums.org/showpost.php?p=6391959&postcount=1)

---

### Post by Rubi1200 on 2010-11-03
To be honest, I am not sure attempting to restore the Windows bootloader will achieve anything other than to make the situation worse.

I base this statement on the following information from the script:[FONT=monospace]

[/FONT]sda1: 
> File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    [COLOR=Red]Operating System:  
    Boot files/dirs:[/COLOR]sda5:
> File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    [COLOR=Red]Operating System:  
    Boot files/dirs:[/COLOR]It looks as if the operating system is gone and whatever was there has been formatted with the FAT32 file-system.

You could try recovering the partitions, but I do not know how successful that will be:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

