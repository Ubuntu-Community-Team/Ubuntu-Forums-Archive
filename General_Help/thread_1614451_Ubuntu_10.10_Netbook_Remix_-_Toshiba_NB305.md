---
title: "Ubuntu 10.10 Netbook Remix - Toshiba NB305"
date: 2010-11-05
forum: General Help
---

### Post by Lothair on 2010-11-05
I've installed Ubuntu roughly three times now via USB using the Ubuntu instructions and recommended software.

But when I go to start the computer back up after the installer tells me to restart, I get;

Gave up waiting for root device. Common problems:

Etc etc etc

Alert! /dev/disk/by-uuid/dba355c0-54f9-4b67-83fc-8e36beb8b97b does not exist.
Dropping to a shell!

BusyBox v1.15.3 etc etc etc (I'm on an iPod touch right now, forgive my laziness)

---

### Post by Lothair on 2010-11-05
I wonder, would installing an earlier edition work or would I run into the same problem?

---

### Post by drs305 on 2010-11-05
Some netbook users have had success by placing "rootdelay=90" at the end of the "linux" line when they boot.

At the Grub menu, highlight the entry you want, press "e" to edit the menuentry. 
Find the "linux" line. It probably ends with "quiet splash".
Add **rootdelay=90** to the end of that line.
Press CTRL-x to boot.

If it works, edit /etc/default/grub  (gksu gedit /etc/default/grub) and add **rootdelay=90** to this line:
 > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash rootdelay=90"
Then update grub:
```
sudo update-grub
```

You may be able to reduce the value of rootdelay.

---

### Post by Lothair on 2010-11-06
What's the Grub menu? Where is it at? 

I don't know very much about Linux or it's variants. I'm very new to this area of software.

---

### Post by drs305 on 2010-11-06
The Grub menu is the first menu you see when Ubuntu boots. It normally displays several choices to boot, including the normal mode ("Ubuntu..."), a recovery mode ("Ubuntu.....recovery"), possibly other OS's such as Windows.

If you have two or more operating systems, you should see the menu when you boot. If you have only Ubuntu, try turning on your computer and holding down the SHIFT key until the menu displays. Then you can accomplish the steps I discussed in the previous post.

---

### Post by Lothair on 2010-11-06
I did as you asked and it didn't seem to work. Any other suggestions?

---

### Post by drs305 on 2010-11-06
Please run the boot info script from the following link and post the contents of the RESULTS.txt file it generates:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Lothair on 2010-11-06
Where on earth is the desktop in ubuntu??? That's where the file was saved but I can't for the life of me find it. 

You'd think the desktop would be, you know, where the desktop is supposed to be? That's just purposely confusing.

---

### Post by Lothair on 2010-11-06
```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc

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

sdc1: _________________________________________________________________________

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

/dev/sda1    *          2,048   306,440,191   306,438,144  83 Linux
/dev/sda2         306,442,238   312,580,095     6,137,858   5 Extended
/dev/sda5         306,442,240   312,580,095     6,137,856  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1028 MB, 1028653056 bytes
2 heads, 63 sectors/track, 15945 cylinders, total 2009088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32     2,009,087     2,009,056   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        dba355c0-54f9-4b67-83fc-8e36beb8b97b   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        03e6eabf-1189-4c00-81d4-65ee888b854c   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        1012-B0D8                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set dba355c0-54f9-4b67-83fc-8e36beb8b97b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set dba355c0-54f9-4b67-83fc-8e36beb8b97b
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set dba355c0-54f9-4b67-83fc-8e36beb8b97b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=dba355c0-54f9-4b67-83fc-8e36beb8b97b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set dba355c0-54f9-4b67-83fc-8e36beb8b97b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=dba355c0-54f9-4b67-83fc-8e36beb8b97b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set dba355c0-54f9-4b67-83fc-8e36beb8b97b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set dba355c0-54f9-4b67-83fc-8e36beb8b97b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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
# / was on /dev/sdb1 during installation
UUID=dba355c0-54f9-4b67-83fc-8e36beb8b97b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=03e6eabf-1189-4c00-81d4-65ee888b854c none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  13.0GB: boot/grub/core.img
  51.7GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-22-generic
  13.0GB: boot/vmlinuz-2.6.35-22-generic
    .8GB: initrd.img
  13.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 20 01 00  |.X.SYSLINUX.. ..|
00000010  02 00 02 00 00 f8 f6 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  e0 a7 1e 00 00 00 29 d8  b0 12 10 4e 4f 20 4e 41  |......)....NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 33 c9  |ME    FAT16   3.|
00000040  8e d1 bc f0 7b 8e d9 b8  00 20 8e c0 fc bd 00 7c  |....{.... .....||
00000050  38 4e 24 7d 24 8b c1 99  e8 3c fa fc 31 c9 8e d1  |8N$}$....<..1...|
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
00000100  7d 00 66 b8 ed d3 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
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


=======Devices which don't seem to have a corresponding hard drive==============

sdb

```

---

### Post by drs305 on 2010-11-06
Your grub.cfg file shows a lot of "set root='(hd1,msdos1)'" lines. This translates to sdb1, which you don't have.

Boot the LiveCD and make sure you don't have any external drives/flashdrives attached. We can reinstall Grub2 to make sure it points to the correct partition.

Once booted from the LiveCD, open a terminal (Applications, Accessories, Terminal).

Mount your Ubuntu partition (sda1):
```

sudo mkdir /mnt/temp
sudo mount /dev/sda1 /mnt/temp
```

Since there was a problem with Grub2 choosing the correct device, verify the correct partition is mounted by opening a file browser and checking the normal Ubuntu folders are on the mount point. You can close the browser once you see the normal folders such as /boot and /etc.
```
nautilus /mnt/temp
```

Now you can *chroot* into your real installation so the commands will work on your Ubuntu files (and not the CD's):
```

for i in /dev /dev/pts /proc /sys ; do sudo mount -B $i /mnt/temp$i; done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
sudo chroot /mnt/temp
```
You are now "root" in sda1. You don't use sudo with the commands. The first one reinstalls Grub2; the second creates /boot/grub/grub.cfg in sda**1**.

```

grub-install /dev/sda
update-grub

```

When you are done, exit:
```
exit
```
Unmount:
```
for i in /dev/pts /dev /proc /sys / ; do sudo umount /mnt/temp$i ; done
```
Reboot.

---

### Post by Lothair on 2010-11-06
I'm not sure what I did wrong or if I did anything wrong, but that didn't seem to work. The same problems came up after reboot. 

Also, I don't have a LiveCD or the ability to use one, as I'm using a Netbook which doesn't have a CD-ROM drive. So I have to use a Flash Drive with Ubuntu on it.

---

### Post by drs305 on 2010-11-06
Sorry about the LiveCD. When I returned to the thread after work I'd forgotten you were on a netbook (even though it's in the title !).

A couple of questions about my previous post. 

Were you able to confirm that your real Ubuntu installation was "sda1"? If not, did you change the device designation to the real location?

Did the commands produce errors?

Did you try to boot without the flash drive inserted, and is BIOS set to boot the hard drive if the flash drive is not present?

If everything seemed to run but it's still not booting, please rerun and repost the RESULTS.txt.

---

### Post by Lothair on 2010-11-06
1.) I'm not entirely sure how to confirm this. 

2.) There were not any errors.

3.) Yes.

---

### Post by drs305 on 2010-11-06
> **Lothair said:**
> 1.) I'm not entirely sure how to confirm this. 

When you were running the commands I suggested:
"Since there was a problem with Grub2 choosing the correct device, verify the correct partition is mounted by opening a file browser and checking the normal Ubuntu folders are on the mount point. You can close the browser once you see the normal folders such as /boot and /etc."

The mount point would have been /mnt/temp.

It was just to make sure that sda1 was in fact your Ubuntu installation. Since the grub.cfg file seemed to think it was sdb1 (hd1,1), I thought it best to check before running the commands.


Can you boot this way? Hold down the SHIFT key as the computer boots to show the Grub2 menu.

Press "c" to get to the grub terminal.

Type:
> ls (hd0,1)/boot/grub
Do you see a lot of *.mod files? If not, type just "ls" and see what partitions G2 sees.

Try to boot if you found the *.mod files above. If it wasn't (hd0,1), change all the commands to the correct device:
```
set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot
```

---

### Post by Lothair on 2010-11-06
None of that changed anything.

There were a bunch of mod files though.

---

### Post by drs305 on 2010-11-06
> **Lothair said:**
> None of that changed anything.

There were a bunch of mod files though.

Well, that's good. Continue exploring from the grub prompt. See if you can find the kernel and initrd image:

```
ls (hd0,1)/boot
```
Do you see the kernel (for instance vmlinuz-2.6.35-22-generic)?
Do you see the initrd image (initrd.img-2.6.35-22-generic)?

If so, try booting with the following:
```
set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1 ro
initrd /initrd.img-2.6.35-22-generic
boot

```

If it won't take a command, let us know what error message it generates.

---

### Post by Lothair on 2010-11-06
ls (hd0,1)/boot

That code didn't work. It says:

/bin/sh: syntax error: unexpected word (expecting ")")
(initramfs) ls (hd0,1) /boot

---

### Post by drs305 on 2010-11-06
Those commands need to be run from the grub prompt, *before* you get to the initramfs message. The grub prompt would have to be called up by pressing "c" from the Grub menu or if it appeared by itself during a failed boot. The prompt would be "grub>" or "grub rescue>". It won't work from: (initramfs)

If you don't see the Grub menu during boot, try holding down the SHIFT key.

---

### Post by Lothair on 2010-11-06
linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1 ro

Error: file not found.

---

### Post by drs305 on 2010-11-06
I've sent you a PM. Please check your inbox.

---

### Post by Lothair on 2010-11-07
I downgraded to 10.04 and it's running just fine now. It takes awhile to boot up but otherwise I like it better so far, actually. I wonder why they changed it? This seems more user-friendly.

---

### Post by jvanvolk on 2010-11-09
I am having the same problem as Lothair and with a Toshiba NB305 Netbook as well.

[QUOTE=Lothair;10077428]I've installed Ubuntu roughly three times now via USB using the Ubuntu instructions and recommended software.

But when I go to start the computer back up after the installer tells me to restart, I get;

Gave up waiting for root device. Common problems:

Etc etc etc

Alert! /dev/disk/by-uuid/dba355c0-54f9-4b67-83fc-8e36beb8b97b does not exist.
Dropping to a shell!

BusyBox v1.15.3 etc etc etc

---

### Post by jvanvolk on 2010-11-09
Was anyone able to reslove this with ubuntu netbook 10.10?

---

### Post by drs305 on 2010-11-09
> **jvanvolk said:**
> Was anyone able to reslove this with ubuntu netbook 10.10?

Take a look at this thread. I don't think it's netbook specific but it may provide some answers. If it doesn't help, post your RESULTS.txt from the boot info script. The instructions are in the referenced link.

[http://ubuntuforums.org/showthread.php?t=1399810]("http://ubuntuforums.org/showthread.php?t=1399810")

---

