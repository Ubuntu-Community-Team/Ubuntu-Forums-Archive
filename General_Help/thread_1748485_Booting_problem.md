---
title: "Booting problem"
date: 2011-05-03
forum: General Help
---

### Post by xuyuangogogo on 2011-05-03
Hi all,

I had a win7 and a wubi-installed 10.10 Ubuntu OS.
Yesterday, I tried to update my ubuntu to 11.04.
After I updated it, I continue to install burg, which is a brand-new boot loader based on GRUB. 

[http://code.google.com/p/burg/](http://code.google.com/p/burg/)

After I reboot, I can't boot both ubuntu and win7.
I got a line like: boot error: no such device and a long number string like e76.....

And then there is line like:
grub rescue>

cmds like ls and set works.

Is there anybody can help me with it?
It's getting close to the finals of a semester. It's really bad to reach that situation!

Thank you all for your attention and help!!

---

### Post by bcbc on 2011-05-03
Insert windows disk, boot to a repair prompt:
For XP run: fixmbr
For vista/7 run: bootrec /fixmbr

Don't install burg on Wubi.

PS if you don't have a windows disk you can also install lilo. For reference see Problem #1 here [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) (it explains how to install lilo to get windows booting).

---

### Post by xuyuangogogo on 2011-05-08
I would say "you saved me!!!"

I can't thank you more!

Right now, I can boot into windows.

However, I still cannot boot into ubuntu.

This time, it stays in grub>. not grub rescue>

I don't know what should I do.

Change grub configuration file?

> **bcbc said:**
> Insert windows disk, boot to a repair prompt:
For XP run: fixmbr
For vista/7 run: bootrec /fixmbr

Don't install burg on Wubi.

PS if you don't have a windows disk you can also install lilo. For reference see Problem #1 here [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) (it explains how to install lilo to get windows booting).

---

### Post by garvinrick4 on 2011-05-08
[[wubi] Wubi megathread - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1639198")

---

### Post by bcbc on 2011-05-09
Why don't you post the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") so we can see what's going on.

I'm not sure whether burg replaces grub.cfg with burg.cfg (not that I've noticed with other people who had the same problem). So it could be a grub issue (as described in Problem #2 of the wubi megathread linked to above). You said you upgraded to Natty - when you're in that grub prompt, what version does it say on top? It should be 1.99~rc1-13ubuntu# (not sure of the last number, but that's the Natty version that's been fixed). 
If it still says 1.98+20100804-5ubuntu2... then likely it's the Problem #2 from the megathread.

---

### Post by xuyuangogogo on 2011-05-09
Hi, I run the boot info shell, and I got the following result:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda6/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 52.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     2,459,647     2,457,600   7 HPFS/NTFS
/dev/sda2           2,459,648   344,162,295   341,702,648   7 HPFS/NTFS
/dev/sda3         344,162,304   604,659,711   260,497,408   f W95 Ext d (LBA)
/dev/sda5         344,164,352   471,140,351   126,976,000   7 HPFS/NTFS
/dev/sda6         471,142,400   533,606,399    62,464,000   7 HPFS/NTFS
/dev/sda4         604,659,712   625,139,711    20,480,000   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.0 GB, 16028794368 bytes
254 heads, 63 sectors/track, 1956 cylinders, total 31306239 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             52    31,283,909    31,283,858   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       bc219155-5e9a-401c-9779-5af70298926a   ext3                                     
/dev/loop2       e7bea48d-922f-4d5f-b0a3-885b52454d45   ext4                                     
/dev/sda1        BC84CF5B84CF1734                       ntfs       SYSTEM_DRV                    
/dev/sda2        D858D38258D35E36                       ntfs       System                        
/dev/sda3: PTTYPE="dos" 
/dev/sda4        1446DA3A46DA1BF4                       ntfs       Lenovo_Recovery               
/dev/sda5        9ABA5525BA54FEE7                       ntfs       Material                      
/dev/sda6        CEEC82FCEC82DE59                       ntfs       Ubuntu                        
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9E74-CBFA                              vfat       &#26032;&#21367;                        
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)


======================== sda6/Wubi/boot/grub/grub.cfg: ========================

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root CEEC82FCEC82DE59
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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root CEEC82FCEC82DE59
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-8-generic-pae" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root CEEC82FCEC82DE59
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=CEEC82FCEC82DE59 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Ubuntu, Linux 2.6.38-8-generic-pae (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root CEEC82FCEC82DE59
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=CEEC82FCEC82DE59 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root CEEC82FCEC82DE59
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=CEEC82FCEC82DE59 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root CEEC82FCEC82DE59
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=CEEC82FCEC82DE59 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.35-28-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root CEEC82FCEC82DE59
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=CEEC82FCEC82DE59 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, Linux 2.6.35-28-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root CEEC82FCEC82DE59
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=CEEC82FCEC82DE59 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-28-generic
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
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root BC84CF5B84CF1734
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root D858D38258D35E36
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

============================= sda6/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda6/Wubi: Location of files loaded by Grub: =================


  23.8GB: boot/grub/grub.cfg
   1.0GB: boot/initrd.img-2.6.35-28-generic
   3.0GB: boot/initrd.img-2.6.38-8-generic
   7.7GB: boot/initrd.img-2.6.38-8-generic-pae
  13.6GB: boot/vmlinuz-2.6.35-28-generic
   5.2GB: boot/vmlinuz-2.6.38-8-generic
   5.3GB: boot/vmlinuz-2.6.38-8-generic-pae
   7.7GB: initrd.img
   3.0GB: initrd.img.old
   5.3GB: vmlinuz
   5.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 10 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  20 00 40 00 00 00 00 00  |........ .@.....|
00000020  92 5a dd 01 a0 3b 00 00  00 00 00 00 02 00 00 00  |.Z...;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 fa cb 74 9e e6  96 b0 e5 8d b7 20 20 20  |..)..t.......   |
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
00000100  7d 00 66 b8 a0 f0 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e cd c2 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
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
> **bcbc said:**
> Why don't you post the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") so we can see what's going on.

I'm not sure whether burg replaces grub.cfg with burg.cfg (not that I've noticed with other people who had the same problem). So it could be a grub issue (as described in Problem #2 of the wubi megathread linked to above). You said you upgraded to Natty - when you're in that grub prompt, what version does it say on top? It should be 1.99~rc1-13ubuntu# (not sure of the last number, but that's the Natty version that's been fixed). 
If it still says 1.98+20100804-5ubuntu2... then likely it's the Problem #2 from the megathread.

---

### Post by xuyuangogogo on 2011-05-09
Thanks, I've followed the problem 1 solution 2.

Right now, my situation is neither problem 1 nor problem 2.

Thank you for your help!

> **garvinrick4 said:**
> [[wubi] Wubi megathread - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1639198")

---

### Post by bcbc on 2011-05-09
You didn't mention the grub version. Everything looks good so **I am going to assume** that the wubildr grub version does _not_ match 1.99~rc1-13ubuntu# and therefore it is likely you are suffering from problem #2 (it's a memory corruption issue when the loopback device is created more than once)

From the grub prompt enter:
```
linux /vmlinuz root=/dev/sda6 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot

```

Once booted make sure that burg did not uninstall package grub-pc (grub2). If it did, you need to reinstall it.

If grub-pc is still there, run the following from a terminal (CTRL+ALT+t):
```
sudo grub-install /dev/loop0
```
What this does is tell grub to update the wubildr file (grub will look for it on your windows partition and replace it with a current version of wubildr that doesn't suffer from the loopback corruption issue. (That's loop+ZERO)

---

### Post by xuyuangogogo on 2011-05-09
Thank you for you instant reply!

Could you tell me how to check the version of grub?

I'll check that and post it here ASAP.

> **bcbc said:**
> You didn't mention the grub version. Everything looks good so **I am going to assume** that the wubildr grub version does _not_ match 1.99~rc1-13ubuntu# and therefore it is likely you are suffering from problem #2 (it's a memory corruption issue when the loopback device is created more than once)

From the grub prompt enter:
```
linux /vmlinuz root=/dev/sda6 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot

```Once booted make sure that burg did not uninstall package grub-pc (grub2). If it did, you need to reinstall it.

If grub-pc is still there, run the following from a terminal (CTRL+ALT+t):
```
sudo grub-install /dev/loop0
```What this does is tell grub to update the wubildr file (grub will look for it on your windows partition and replace it with a current version of wubildr that doesn't suffer from the loopback corruption issue. (That's loop+ZERO)

---

### Post by bcbc on 2011-05-09
When you boot, choose Ubuntu. The next screen you'll see is the grub menu (or in your case a grub prompt). Look at the top of the screen and it will say the version of grub up there. If it says 1.98.... then follow my instructions. If it says 1.99~rc1... then likely you have some other problem.


PS when you actually boot Ubuntu you can see the version of grub installed from a terminal:
```
sudo grub-install -v
```
The version should match what is shown on the grub menu.

---

### Post by xuyuangogogo on 2011-05-09
The version is 1.98.

I'll follow your instructions.

> **bcbc said:**
> When you boot, choose Ubuntu. The next screen you'll see is the grub menu (or in your case a grub prompt). Look at the top of the screen and it will say the version of grub up there. If it says 1.98.... then follow my instructions. If it says 1.99~rc1... then likely you have some other problem.


PS when you actually boot Ubuntu you can see the version of grub installed from a terminal:
```
sudo grub-install -v
```The version should match what is shown on the grub menu.

---

### Post by xuyuangogogo on 2011-05-09
Hi,

When I type in

```
linux /vmlinuz root=/dev/sda6 loop=/ubuntu/disks/root.disk ro quiet splash
```

It displayed the following:

```
error: file not found

```

Could you tell me what should I do?

Thanks.

> **bcbc said:**
> You didn't mention the grub version. Everything looks good so **I am going to assume** that the wubildr grub version does _not_ match 1.99~rc1-13ubuntu# and therefore it is likely you are suffering from problem #2 (it's a memory corruption issue when the loopback device is created more than once)

From the grub prompt enter:
```
linux /vmlinuz root=/dev/sda6 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot

```Once booted make sure that burg did not uninstall package grub-pc (grub2). If it did, you need to reinstall it.

If grub-pc is still there, run the following from a terminal (CTRL+ALT+t):
```
sudo grub-install /dev/loop0
```What this does is tell grub to update the wubildr file (grub will look for it on your windows partition and replace it with a current version of wubildr that doesn't suffer from the loopback corruption issue. (That's loop+ZERO)

---

### Post by bcbc on 2011-05-09
/vmlinuz is supposed to link to your latest kernel. Are you sure you entered it correctly? You could try entering the full path. If that doesn't work likely there is some problem accessing the root.disk (but that seems unlikely as the bootinfoscript can read it). 

Just check whether the root.disk is loop mounted (the following should say "(loop0)":
```
echo $root
```

For the full path use:
```
linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sda6 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /boot/initrd.img-2.6.38-8-generic
boot
```

(or use the -pae kernel if you want)

You can also do:
```
ls /boot/
```
To see if the boot files are available.

---

### Post by xuyuangogogo on 2011-05-09
I think I enter the grub correctly.

Still error: file not found.

When I type in

```
echo $root
```

I got 
```
hd0,2
```

When I type in 
```
ls
```

I got 
```
(hd0) (hd0,msdos6) (hd0,msdos5) (hd0,msdos4) (hd0,msdos2) (hd0,msdos1)
```

When I type in 
```
ls /boot/
```

I got 
```
BCD BCD.LOG BCD.LOG1 BCD.LOG2 BOOTSTAT.DAT cs-CZ/ da-DK/ de-DE/ el-GR/ en-US/ es-ES/ fi-FI/ Fonts/ fr-Fr/ hu-HU/ it-IT ja-JP/ ko-KR/ memtest.exe nb-NO/ nl-NL/ pl-PL/ pt-BR/ pt-PT/ ru-RU/ sv-SE/ tr-TR/ zh-CH/ zh-HK/ zh-TW/
```


> **bcbc said:**
> /vmlinuz is supposed to link to your latest kernel. Are you sure you entered it correctly? You could try entering the full path. If that doesn't work likely there is some problem accessing the root.disk (but that seems unlikely as the bootinfoscript can read it). 

Just check whether the root.disk is loop mounted (the following should say "(loop0)":
```
echo $root
```

For the full path use:
```
linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sda6 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /boot/initrd.img-2.6.38-8-generic
boot
```

(or use the -pae kernel if you want)

You can also do:
```
ls /boot/
```
To see if the boot files are available.

---

### Post by xuyuangogogo on 2011-05-09
When I type in 
```
set
```

I got 
```

?=0
color-hightlight=
color-normal=
pager=
prefix=(hd0,2)//ubuntu/burg
root=hd0,2

```


> **bcbc said:**
> /vmlinuz is supposed to link to your latest kernel. Are you sure you entered it correctly? You could try entering the full path. If that doesn't work likely there is some problem accessing the root.disk (but that seems unlikely as the bootinfoscript can read it). 

Just check whether the root.disk is loop mounted (the following should say "(loop0)":
```
echo $root
```

For the full path use:
```
linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sda6 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /boot/initrd.img-2.6.38-8-generic
boot
```

(or use the -pae kernel if you want)

You can also do:
```
ls /boot/
```
To see if the boot files are available.

---

### Post by xuyuangogogo on 2011-05-09
At the begining, I use these cmds to install burg:

```

sudo add-apt-repository ppa:n-muench/burg
sudo apt-get update
sudo apt-get install burg burg-common burg-emu burg-pc burg-themes burg-themes-common

```

> **bcbc said:**
> /vmlinuz is supposed to link to your latest kernel. Are you sure you entered it correctly? You could try entering the full path. If that doesn't work likely there is some problem accessing the root.disk (but that seems unlikely as the bootinfoscript can read it). 

Just check whether the root.disk is loop mounted (the following should say "(loop0)":
```
echo $root
```

For the full path use:
```
linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sda6 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /boot/initrd.img-2.6.38-8-generic
boot
```

(or use the -pae kernel if you want)

You can also do:
```
ls /boot/
```
To see if the boot files are available.

---

### Post by bcbc on 2011-05-09
That's strange... you boot the computer, you select Ubuntu from the Windows boot manager, and you get a grub prompt with that? Did burg update wubildr?? (What does that version info on top say?)

Let's try this:
```
set root=(hd0,6)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sda6 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /boot/initrd.img-2.6.38-8-generic
boot
```

---

### Post by xuyuangogogo on 2011-05-09
It works.

Thank you so much!!

All problems solved!

You're really expert of linux~ :D

Due to my curiosity, could you tell me if I want to learn some stuff like that, which is definitely hard to learn from a course, what should I do?

Also, I don't want to use wubi anymore. 
Can I backup all the stuff in the ubuntu and uninstall the wubi-ubuntu from windows, and create a logic disk in windows in order to install ubuntu in it from a flash-disk?

> **bcbc said:**
> That's strange... you boot the computer, you select Ubuntu from the Windows boot manager, and you get a grub prompt with that? Did burg update wubildr?? (What does that version info on top say?)

Let's try this:
```
set root=(hd0,6)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sda6 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /boot/initrd.img-2.6.38-8-generic
boot
```

---

### Post by bcbc on 2011-05-09
> **xuyuangogogo said:**
> It works.

Thank you so much!!

All problems solved!

You're really expert of linux~ :D

Due to my curiosity, could you tell me if I want to learn some stuff like that, which is definitely hard to learn from a course, what should I do?

Also, I don't want to use wubi anymore. 
Can I backup all the stuff in the ubuntu and uninstall the wubi-ubuntu from windows, and create a logic disk in windows in order to install ubuntu in it from a flash-disk?

Great! Don't forget to update wubildr (that "sudo grub-install /dev/loop0" command).

The best place to learn is helping out on ubuntuforums.org (there are many knowledgeable people).

If you can prepare the partitions you can migrate your wubi install using the script here: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

