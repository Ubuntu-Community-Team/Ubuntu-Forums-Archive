---
title: "Noob completely lost.  Grub Rescue screen"
date: 2010-12-13
forum: General Help
---

### Post by melek-taus on 2010-12-13
Hello.  I have a eeePC 1015PEB with Windows 7.  My friend helped me with a dual install and it worked fine until I accidentally clicked on the Windows Vista option on the GRUB menu.  I was redirected to a recovery screen with the options "Recovery" and "Cancel".  I clicked on "recovery" and that initialized, but then spit me back to the GRUB menu, this time with no Windows 7 option.  I then accessed Ubuntu.  I upgraded to 10.4 and then all kinds of problems started.  Firefox was crashing, the computer was shutting down without warning, etc.  I tried some things I found on this forum and ended up with a "grub rescue>" prompt. I tried booting Ubuntu from here by trying this: [http://ubuntuforums.org/showthread.php?t=1599293]("http://ubuntuforums.org/showthread.php?t=1599293") but I couldn't find the ISO file.  What are my options here?

---

### Post by quinntar on 2010-12-13
Hi, well those kinds of things can happen... anyway do you still have an access to ubuntu or windows ? 
#1 Still have access to windows : ok then you did not mess up the all thing go to  #2 or 3


#2 If You can boot on Ubuntu you can take a usb stick, take a live iso file from ubuntu.com and make a bootable usb stick from ubuntu preferences, administration, make a bootable thing... once it's done just reboot, with the stick plugged in. then boot on ubuntu from the stick with a live session, save the data from your installed ubuntu partition (and from you windows partition if you cannot access windows normally anymore) on a usb hard drive if needed and finally install ubuntu by clicking "install ubuntu" on the desktop... Follow the instructions to install Ubuntu and Windows side by side(or ask your friend to do it if you're not sure how to do it).

#3 If you cannot boot on ubuntu, you can either try and download Super Grub Disk which will give you the opportunity to recover your initial grub parameters (but you'll need an external usb CD/DVD driver since you have a netbook without a cd driver I presume) (if you have one burn the super grub disk and boot on it then follow the instructions to recover your initial grub parameters

Or you an still download an Ubuntu 10.10 iso file using windows and have a look to  the documentation on how to make a bootable usb stick of ubuntu from windows on ubuntu forums then follow the same progression as read before, save, install etc...

If you cannot boot on windows anymore save you data from a live session of ubuntu on a usb hard drive and then recover Windows before installing ubuntu again.

I hope it could help

Quinnt

ps :On a netbook, ubuntu 10.10 should be fine. Once it's installed, plug your netbook with an RJ45 cable to your internet provider box or with a usb cable to get the latest proprietary drivers that should be available for your devices(such as wifi things, video card and so on). Then everything should be ok.

---

### Post by arpanaut on 2010-12-13
Take a look at this:

[http://ubuntuforums.org/showthread.php?t=1594052&highlight=grub+rescue+megathread](http://ubuntuforums.org/showthread.php?t=1594052&highlight=grub+rescue+megathread)

edit: fixed now

---

### Post by wilee-nilee on 2010-12-13
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

---

### Post by melek-taus on 2010-12-20
Ok I have been travelling for a while and have lugged my sick netbook with me.  I have finally got it to boot from a USB drive with Ubuntu Netbook 10.10.  I am running off of the USB.  If I do not I still boot up to the 'grub rescue>' prompt.  Here is the Boot Info Script:

```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /media/sda5/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   308,688,974   308,686,927   7 HPFS/NTFS
/dev/sda2         308,688,975   456,888,599   148,199,625   5 Extended
/dev/sda5         308,689,038   450,944,549   142,255,512  83 Linux
/dev/sda6         450,944,613   456,888,599     5,943,987  82 Linux swap / Solaris
/dev/sda3         456,892,416   488,349,695    31,457,280  1b Hidden W95 FAT32
/dev/sda4         488,349,696   488,392,064        42,369  ef EFI (FAT-12/16/32)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2063 MB, 2063597568 bytes
64 heads, 62 sectors/track, 1015 cylinders, total 4030464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     4,027,519     4,027,458   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0A66A13B66A12881                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        86F4-D40A                              vfat                                     
/dev/sda5        0f7e6557-9464-40f5-b16d-fdf4d47afc2a   ext4                                     
/dev/sda6        d0325aa6-1e07-4230-a8ae-8939f621f006   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7A5E-29B0                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 0f7e6557-9464-40f5-b16d-fdf4d47afc2a
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 0f7e6557-9464-40f5-b16d-fdf4d47afc2a
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0f7e6557-9464-40f5-b16d-fdf4d47afc2a
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=0f7e6557-9464-40f5-b16d-fdf4d47afc2a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0f7e6557-9464-40f5-b16d-fdf4d47afc2a
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=0f7e6557-9464-40f5-b16d-fdf4d47afc2a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0f7e6557-9464-40f5-b16d-fdf4d47afc2a
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=0f7e6557-9464-40f5-b16d-fdf4d47afc2a ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0f7e6557-9464-40f5-b16d-fdf4d47afc2a
    echo    'Loading Linux 2.6.31-22-generic ...'
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=0f7e6557-9464-40f5-b16d-fdf4d47afc2a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0f7e6557-9464-40f5-b16d-fdf4d47afc2a
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0f7e6557-9464-40f5-b16d-fdf4d47afc2a ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0f7e6557-9464-40f5-b16d-fdf4d47afc2a
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0f7e6557-9464-40f5-b16d-fdf4d47afc2a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0f7e6557-9464-40f5-b16d-fdf4d47afc2a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0f7e6557-9464-40f5-b16d-fdf4d47afc2a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod fat
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 86f4-d40a
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=0f7e6557-9464-40f5-b16d-fdf4d47afc2a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d0325aa6-1e07-4230-a8ae-8939f621f006 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 158.1GB: boot/grub/core.img
 158.4GB: boot/grub/grub.cfg
 158.4GB: boot/initrd.img-2.6.31-14-generic
 158.9GB: boot/initrd.img-2.6.31-22-generic
 158.9GB: boot/initrd.img-2.6.32-26-generic
 158.3GB: boot/vmlinuz-2.6.31-14-generic
 158.5GB: boot/vmlinuz-2.6.31-22-generic
 158.7GB: boot/vmlinuz-2.6.32-26-generic
 158.9GB: initrd.img
 158.9GB: initrd.img.old
 158.7GB: vmlinuz
 158.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 54 01  |.X.SYSLINUX...T.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3e 00 00 00  |........?...>...|
00000020  42 74 3d 00 56 0f 00 00  00 00 00 00 02 00 00 00  |Bt=.V...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 b0 29 5e 7a 4e  4f 20 4e 41 4d 45 20 20  |..).)^zNO NAME  |
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
00000100  7d 00 66 b8 d0 dd 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
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

sdc 
```

I am starting to understand this stuff a little better, but I still am unsure what to do with all of these partitions.  What I am pretty sure of is that most of my files (from my Windows 7 partition) are in sda1.  I cannot access these from Ubuntu, as I am assuming that my previous mistake of accidentally starting a Vista recovery has made them inaccessible.  I would like to revert back to a dual boot (Ubuntu 10.10/Windows 7) set-up if possible.  How can I go about this? What is the best way to go about loading 10.10?  How should I manage the partitions?  Thanks for the help.

---

### Post by drs305 on 2010-12-20
From the LiveCD, mount the Ubuntu partition and reinstall Grub2. These instructions assume sda is your main drive:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```

Power off/reboot with the USB disconnected and see if it now boots. If so, run the following command after the boot:
```
sudo update-grub
```

If it doesn't boot, reboot and enter your BIOS setup and make sure it registers the drive as the correct size (i.e. more than 137GB). Some BIOS cannot see the entire drive unless the 'large drive' setting is enabled.

---

### Post by melek-taus on 2010-12-20
Ok. Now the grub menu loads up and I am able to again access my Ubuntu 10.4 OS, but there is still no option to select Windows 7 on the Grub menu.  When I try to access my files on the Windows 7 partition (158 GB filesystem) Ubuntu says that there are no files on it (147GB freespace) which cannot be the case.  I was never prompted to format this drive.  I was only put through a Vista recovery process accidentally.  Any ideas on how to recover my data on a netbook?  Do I need to create a windows 7 recovery USB?  If so, how do I do this and how do I boot it?  Thanks so much for the help thus far.

---

### Post by drs305 on 2010-12-20
> **melek-taus said:**
> Ok. Now the grub menu loads up and I am able to again access my Ubuntu 10.4 OS, but there is still no option to select Windows 7 on the Grub menu.  When I try to access my files on the Windows 7 partition (158 GB filesystem) Ubuntu says that there are no files on it (147GB freespace) which cannot be the case.  I was never prompted to format this drive.  I was only put through a Vista recovery process accidentally.  Any ideas on how to recover my data on a netbook?  Do I need to create a windows 7 recovery USB?  If so, how do I do this and how do I boot it?  Thanks so much for the help thus far.

I'm not intimately familiar with Windows any longer. In the meantime, if you run the boot info script from the following site and post the RESULTS.txt it will provide a lot of information about your partitions, installed systems, etc. 

[_http://bootinfoscript.sourceforge.net_]("http://bootinfoscript.sourceforge.net")

I'm about to log off but hopefully a Windows guru will wander by.

---

### Post by wilee-nilee on 2010-12-20
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs: ** /bootmgr /Boot/BCD /Windows/System32/winload.exe   **

That is your sda1 the highlighted part is what missing probably. sda3 has the /bootmgr /boot/bcd that is what grub is seeing probably.

Do you have a windows 7 install DVD or repair/recovery  cd?

---

### Post by melek-taus on 2010-12-21
I don't have a windows recovery disk.  I found an .ISO for one online.  I guess I will have to break down and buy an external disc drive.  I'm having new problems now.  I tried to update to 10.10 because some of the components of Ubuntu were missing/malfunctioning.  I downloaded the updates and they started to install.  The timer told me it would take an hour and a half and I left it.  The screen went blank after a bit and nothing was happening.  The hard disc light was not flickering and nothing was happening.  I restarted the computer and now it won't load, telling me it did not install properly.  I don't understand why the install timer would disappear.  What is happening when the install timer disappears and there seems to be nothing happening?  Am i being to impatient? Do I have to leave it sit overnight or something? Really frustrated at this point!!  Its not even loading off of the USB now.  So sick of this sh##.  Not missing Windows, but dunno how much more of this I can take.  Any input greatly appreciated. Thanks people.

---

### Post by drs305 on 2010-12-21
Do you still get the Grub menu and can you boot into the recovery mode? If so, you can try running the commands I detail later.

If not, you may be able to fix the failed upgrade by booting your USB drive once more and chrooting into your real installation. The instructions on how to do this are [_located here_]("http://ubuntuforums.org/showthread.php?t=1581099").

Don't follow the purge commands, just use the guide to mount your Ubuntu partition and chroot into it. Once at the root prompt, run "apt-get update && apt-get upgrade" and see what error messages you get. They may tell you what commands to run next, such as
```
dpkg --configure -a
or 
apt-get install -f 
```
Note in a chroot environment you don't include "sudo" in the commands since you are already at the root prompt.

You exit the chroot by typing "exit".

---

### Post by melek-taus on 2010-12-22
At this point wouldn't it be easier to load 10.10 from the USB?  If so, how do I rid myself of the old install? Which partitions should I keep?  I really only want to keep the Windows 7 and any backup partitions I might need later. ```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   308,688,974   308,686,927   7 HPFS/NTFS
/dev/sda2         308,688,975   456,888,599   148,199,625   5 Extended
/dev/sda5         308,689,038   450,944,549   142,255,512  83 Linux
/dev/sda6         450,944,613   456,888,599     5,943,987  82 Linux swap / Solaris
/dev/sda3         456,892,416   488,349,695    31,457,280  1b Hidden W95 FAT32
/dev/sda4         488,349,696   488,392,064        42,369  ef EFI (FAT-12/16/32)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2063 MB, 2063597568 bytes
64 heads, 62 sectors/track, 1015 cylinders, total 4030464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     4,027,519     4,027,458   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0A66A13B66A12881                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        86F4-D40A                              vfat                                     
/dev/sda5        0f7e6557-9464-40f5-b16d-fdf4d47afc2a   ext4                                     
/dev/sda6        d0325aa6-1e07-4230-a8ae-8939f621f006   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7A5E-29B0                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 0f7e6557-9464-40f5-b16d-fdf4d47afc2a
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 0f7e6557-9464-40f5-b16d-fdf4d47afc2a
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0f7e6557-9464-40f5-b16d-fdf4d47afc2a
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=0f7e6557-9464-40f5-b16d-fdf4d47afc2a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0f7e6557-9464-40f5-b16d-fdf4d47afc2a
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=0f7e6557-9464-40f5-b16d-fdf4d47afc2a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0f7e6557-9464-40f5-b16d-fdf4d47afc2a
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=0f7e6557-9464-40f5-b16d-fdf4d47afc2a ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0f7e6557-9464-40f5-b16d-fdf4d47afc2a
    echo    'Loading Linux 2.6.31-22-generic ...'
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=0f7e6557-9464-40f5-b16d-fdf4d47afc2a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0f7e6557-9464-40f5-b16d-fdf4d47afc2a
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0f7e6557-9464-40f5-b16d-fdf4d47afc2a ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0f7e6557-9464-40f5-b16d-fdf4d47afc2a
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0f7e6557-9464-40f5-b16d-fdf4d47afc2a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0f7e6557-9464-40f5-b16d-fdf4d47afc2a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 0f7e6557-9464-40f5-b16d-fdf4d47afc2a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod fat
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 86f4-d40a
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=0f7e6557-9464-40f5-b16d-fdf4d47afc2a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d0325aa6-1e07-4230-a8ae-8939f621f006 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 158.1GB: boot/grub/core.img
 161.3GB: boot/grub/grub.cfg
 158.4GB: boot/initrd.img-2.6.31-14-generic
 158.9GB: boot/initrd.img-2.6.31-22-generic
 158.9GB: boot/initrd.img-2.6.32-26-generic
 158.3GB: boot/vmlinuz-2.6.31-14-generic
 158.5GB: boot/vmlinuz-2.6.31-22-generic
 158.7GB: boot/vmlinuz-2.6.32-26-generic
 158.9GB: initrd.img
 158.9GB: initrd.img.old
 158.7GB: vmlinuz
 158.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 54 01  |.X.SYSLINUX...T.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3e 00 00 00  |........?...>...|
00000020  42 74 3d 00 56 0f 00 00  00 00 00 00 02 00 00 00  |Bt=.V...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 b0 29 5e 7a 4e  4f 20 4e 41 4d 45 20 20  |..).)^zNO NAME  |
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
00000100  7d 00 66 b8 d0 dd 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
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

sdc 
```

---

### Post by drs305 on 2010-12-22
> **melek-taus said:**
> At this point wouldn't it be easier to load 10.10 from the USB?  If so, how do I rid myself of the old install? Which partitions should I keep?  I really only want to keep the Windows 7 and any backup partitions I might need later.

I don't know what the EFI partition is, but you can delete/remove any of the partitions with GPparted from the LiveCD. Just find the swap partition, highlight it and then Partition > Swapoff to allow you to work with all the partitions. You can leave sda5 (Ubuntu) as is and use manual partitioning as described below. Or you can delete all the partitions except sda1 and sda3, which are your Windows partitions, and possibly sda4, your EFI partition, if you wanted to keep that for some reason. You have primary partitions which should probably be moved to the start of the disk but if you don't understand what I'm talking about just ask - a screen shot of Gparted would be helpful if you need assistance.

The easiest thing to do would probably be to boot to the LiveCD Desktop via the external drive. Select install, and when you get to the partitioning page select the last option (manual partitioning). Select sda5, select / as the mount point, ext3 or ext4 formatting, and tick the "format" box. This will wipe your old Ubuntu installation and install a completely fresh version. 

Just be sure that sda5 is the partition by comparing the size of the one you select to the size of your old Ubuntu partition. You don't want to pick the wrong partition because whatever is on it will be overwritten during the installation. The sda6 swap partition can be left as is and Ubuntu should use that one on the new installation as well.

---

### Post by melek-taus on 2010-12-22
Ok I have successfully installed 10.10netbook!! woo-hoo!!   That is at least one problem solved. I still need to find a way to access my Windows 7 partition.  It does not show up on the Grub menu. Only Windows Vista.  I am a bit concerned now as my Disk Utility is showing that I have two 79GB file systems, with one being empty.  I think this stems from a previous botched 10,10 install.  I have attached a screen-shot of the Disk Utility info.  I couldn't find the Gparted program.  I am hoping that my data is still all there, as I was never prompted to format or remove any of it.   Is it safe to assume that my data is ok?  What could have happened to it?  Did Ubuntu eat it? What are my data recovery options? I am assuming I need to start from a Windows 7 recovery disk. I am sincerely grateful for all of your help.  It is really reassuring that there are other Super Users out there who are truly super!  :DAny further help with this windows issue would be greatly appreciated.
```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   154,782,745   154,780,698   7 HPFS/NTFS
/dev/sda2         308,689,036   456,888,599   148,199,564   5 Extended
/dev/sda5         308,689,038   450,944,549   142,255,512  83 Linux
/dev/sda6         450,944,613   456,888,599     5,943,987  82 Linux swap / Solaris
/dev/sda3         456,892,416   488,349,695    31,457,280  1b Hidden W95 FAT32
/dev/sda4         488,349,696   488,392,064        42,369  ef EFI (FAT-12/16/32)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0A66A13B66A12881                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        86F4-D40A                              vfat                                     
/dev/sda5        cd24f510-1000-4216-949f-cbce031dda04   ext3                                     
/dev/sda6        d0325aa6-1e07-4230-a8ae-8939f621f006   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,errors=remount-ro,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set cd24f510-1000-4216-949f-cbce031dda04
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set cd24f510-1000-4216-949f-cbce031dda04
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set cd24f510-1000-4216-949f-cbce031dda04
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=cd24f510-1000-4216-949f-cbce031dda04 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set cd24f510-1000-4216-949f-cbce031dda04
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=cd24f510-1000-4216-949f-cbce031dda04 ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set cd24f510-1000-4216-949f-cbce031dda04
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set cd24f510-1000-4216-949f-cbce031dda04
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 86f4-d40a
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d0325aa6-1e07-4230-a8ae-8939f621f006 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 162.8GB: boot/grub/core.img
 162.8GB: boot/grub/grub.cfg
 162.8GB: boot/initrd.img-2.6.35-22-generic
 162.8GB: boot/vmlinuz-2.6.35-22-generic
 162.8GB: initrd.img
 162.8GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by melek-taus on 2010-12-23
Got an external disc drive and used Windows 7 disk.  Windows didn't recognize any previous installs.  To make matters worse, Ubuntu 10.10 decided to start crashing.  After using the OS and browsing the internet for a while, Mozilla started crashing and soon the whole thing froze up.  After a reboot, Ubuntu would allow me to click to my hearts content on the contents of the sidebar, but would not open any programs.  I'm pretty sure that my data is a complete loss at this point, as is any hope for me ever wanting to use Ubuntu again.  Its too bad this OS is not more user friendly.

---

### Post by theasprint on 2010-12-23
Hi,

Wait, did you get rid of your EFI partition?

Argh, one thing special about Asus Laptops is about their EFI partition. From what I know, their EFI partition is related to BIOS (I can say EFI is the BIOS in some way) (EFI=Extensible Firmware Interface, which is what all laptops will have in 2011, I read somewhere)

I am not sure about the state of your EeePC now, but if you can't access your Windows 7 partition you might want to fix your MBR. 

Execute: Bootrec.exe /fixmbr in the Command Prompt in the Windows Recovery Disc to fix your MBR.

---

