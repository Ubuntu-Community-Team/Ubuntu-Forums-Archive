---
title: "After update GBU Grub prompt shows up can't start ubuntu"
date: 2010-12-01
forum: General Help
---

### Post by sxs317 on 2010-12-01
Hi, 

I just ran the most recent updates on ubuntu, restarted my computer and now all that shows up is the Gnu Grub prompt.  What happened!!? What can I do to fix this!?

Thanks

---

### Post by thelaw on 2010-12-01
Just happened to me as well.  I'm googling around and just learned what Grub is :).  If I learn anything, I'll post to this thread.

Some info:
- Kubuntu 10.10
- I am not dual-booting
- I had run a system update, it prompted me to reboot, I rebooted and I am now presented a grub prompt.
- Grub version 1.98
- I am am able boot to a USB Install Stick at the moment to try and figure this out.

here is /boot/grub/grub.cfg (I googled around and this might be relevant to people wishing to help)

```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR- lsb_release -i -s 2> /dev/null ||echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```


In the meantime...help...in Grub, no-one can hear you scream...

---

### Post by sikander3786 on 2010-12-01
> **sxs317 said:**
> Hi, 

I just ran the most recent updates on ubuntu, restarted my computer and now all that shows up is the Gnu Grub prompt.  What happened!!? What can I do to fix this!?

Thanks
Hi.

We need some more info and the output of bootinfoscript will provide us with those.

Please boot an Ubuntu Live CD, choose to try it and not install.

Then download the bootinfoscript, run it as per instructions here and post the output.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Please wrap your output with proper code # tags from the post menu. [/code] at the end and [code] at the beginning.

Thanks.

---

### Post by thelaw on 2010-12-01
Here we go (and thanks for jumping on this):

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
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

/dev/sda1    *          2,048   300,298,239   300,296,192  83 Linux
/dev/sda2         300,300,286   312,580,095    12,279,810   5 Extended
/dev/sda5         300,300,288   312,580,095    12,279,808  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8086 MB, 8086617600 bytes
255 heads, 63 sectors/track, 983 cylinders, total 15794175 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    15,794,174    15,794,112   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       2b2eb7a3-a794-8740-9569-9ae3beddf4ef   ext2       casper-rw                     
/dev/sda1        3ca1c9e1-af7b-4206-be77-517637a6ace7   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        c4c5f220-0a00-4fa5-9335-41cab72b0173   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        603A-43F1                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/disk              ext4       (rw,nosuid,nodev,uhelper=hal)


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
search --no-floppy --fs-uuid --set 3ca1c9e1-af7b-4206-be77-517637a6ace7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 3ca1c9e1-af7b-4206-be77-517637a6ace7
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=3ca1c9e1-af7b-4206-be77-517637a6ace7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 3ca1c9e1-af7b-4206-be77-517637a6ace7
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=3ca1c9e1-af7b-4206-be77-517637a6ace7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 3ca1c9e1-af7b-4206-be77-517637a6ace7
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3ca1c9e1-af7b-4206-be77-517637a6ace7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 3ca1c9e1-af7b-4206-be77-517637a6ace7
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3ca1c9e1-af7b-4206-be77-517637a6ace7 ro single 
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
	search --no-floppy --fs-uuid --set 3ca1c9e1-af7b-4206-be77-517637a6ace7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 3ca1c9e1-af7b-4206-be77-517637a6ace7
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
# / was on /dev/sda1 during installation
UUID=3ca1c9e1-af7b-4206-be77-517637a6ace7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c4c5f220-0a00-4fa5-9335-41cab72b0173 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  90.3GB: boot/grub/core.img
 146.9GB: boot/grub/grub.cfg
  64.6GB: boot/initrd.img-2.6.35-22-generic
 135.0GB: boot/initrd.img-2.6.35-23-generic
  90.3GB: boot/vmlinuz-2.6.35-22-generic
  90.3GB: boot/vmlinuz-2.6.35-23-generic
 135.0GB: initrd.img
  64.6GB: initrd.img.old
  90.3GB: vmlinuz
  90.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 24 00  |.X.SYSLINUX...$.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  c0 ff f0 00 22 3c 00 00  00 00 00 00 02 00 00 00  |...."<..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 f1 43 3a 60 4e  4f 20 4e 41 4d 45 20 20  |..).C:`NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 00 35 16 00  66 ba 00 00 00 00 bb 00  |}.f..5..f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by sikander3786 on 2010-12-01
Well Grub seems pretty intact. I couldn't find any problem with that at all.

What do you mean by Gnu Grub Prompt? Is it the famous Grub Rescue > or just a blinking cursor in the top of your screen?

---

### Post by thelaw on 2010-12-01
"GBU Grub prompt" was the OPs title and I don't know what that means. For me, it is a simple prompt that says: Grub>

The top of the screen contains information such as Grub version, but I see nothing that indicates "rescue" or anything of the sorts.

I can do a help and see all sorts of grub commands but I am unsure as to where to go from there.

---

### Post by sikander3786 on 2010-12-01
Regardless of anything else, I would first recommend to re-instal Grub by following these 2 commands.

```
sudo mount /dev/sda1 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Note, for the 2nd one, it is just sda and not sda1.

Reboot and see if it works now, if doesn't, you need to chroot, purge and re-install Grub as explained here by **drs305**.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by thelaw on 2010-12-01
ok, that did not work. So I will check out the other thread and report back here.  In the meantime, would you please describe what those two commands you had me do actually did?

Did the first command just mount my hard drive to a known mount point for you to do the second command?

Did the second command just say where grub should look for the boot partition?

Thanks.

---

### Post by sikander3786 on 2010-12-01
> **thelaw said:**
> ok, that did not work. So I will check out the other thread and report back here.  In the meantime, would you please describe what those two commands you had me do actually did?

Did the first command just mount my hard drive to a known mount point for you to do the second command?

Did the second command just say where grub should look for the boot partition?

Thanks.
Yes you are nearly correct about everything you said :-)

More info here.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by thelaw on 2010-12-01
I performed that procedure but am receiving the following:

```

grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).

```

Should I post that issue to that thread or can we work that here?

Thanks.

---

### Post by sikander3786 on 2010-12-01
> **thelaw said:**
> I performed that procedure but am receiving the following:

```

grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).

```

Should I post that issue to that thread or can we work that here?

Thanks.
Might be some wiser heads than mine jump in here and advise you better :-)

In the mean time, it would be better to make a post in this thread instead.

[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by thelaw on 2010-12-01
Ok, got it working.  The previous error "cannot find device..." was due to my missing one of the commands in the thread you pointed me to:

```

for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done

```

Rerunning the steps from beginning (and not missing any, this time), proved fruitful.

Thanks for your assistance! (and for the other links for my knowledge).

---

