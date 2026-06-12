---
title: "Boot is FUBAR: Blinking cursor"
date: 2010-12-08
forum: General Help
---

### Post by ghiblian on 2010-12-08
Hello,

10.10's worked on my computer for a few months. I was just using my USB webcam, and the computer froze. So I hard-rebooted it. Now it doesn't start.

I have: GNU GRUB version 1.98+20100804-5ubuntu3
I select: Ubuntu, with Linux 2.6.35-23-generic from the menu.
The boot command is:

```
recordfail
insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set a09etcc
linux /boot/vmlinuz-2.6.35-23-generic root=UUID=a09etcc ro quiet splash
initrd /boot/initrd.img-2.6.35-23-generic
```When I boot I get a blinking cursor. Now, the system only has Ubuntu installed. It is located in /dev/sda2 with filesystem ext4. I can boot with Rescatux live cd, but not with Ubuntu livecd (get the blinking cursor again).

Clearly, there are discrepancies between what's installed and the boot command (different filesystems, some random gpt stuff?)

Anyone know what I should do? Thank you in advance for your help.

---

### Post by oldfred on 2010-12-09
Lets see what is installed where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

The script uses fdisk and blkid, but does not show everything about gpt.
run this if you have gpt:
sudo parted /dev/sda unit s print

and if you have not downloaded gdisk you should. Better to use the newest version, not the one in the repository.
GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by ghiblian on 2010-12-09
Thank you for your response. 

> **oldfred said:**
> 
and if you have not downloaded gdisk you should. Better to use the newest version, not the one in the repository.
I have downloaded and installed gdisk-0.6.13 -- I ran the commands that print detailed GPT info:

```

Command (? for help): p
Disk /dev/sda: 312581808 sectors, 149.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): A77C0E69-E747-4858-A840-EC4244FB36E9
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 312581774
Partitions will be aligned on 2048-sector boundaries
Total free space is 3693 sectors (1.8 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048            4095   1024.0 KiB  EF02  
   2            4096       300294143   143.2 GiB   0700  
   3       300294144       312580095   5.9 GiB     8200  

Command (? for help): i
Partition number (1-3): 1
Partition GUID code: 21686148-6449-6E6F-744E-656564454649 (BIOS boot partition)
Partition unique GUID: D5BB8CD4-006D-473F-A13B-D668828E19EC
First sector: 2048 (at 1024.0 KiB)
Last sector: 4095 (at 2.0 MiB)
Partition size: 2048 sectors (1024.0 KiB)
Attribute flags: 0000000000000000
Partition name: 

Command (? for help): i 2
Partition number (1-3): 2
Partition GUID code: EBD0A0A2-B9E5-4433-87C0-68B6B72699C7 (Linux/Windows data)
Partition unique GUID: B00458E9-4CA3-40D5-A362-A2471F1F7A14
First sector: 4096 (at 2.0 MiB)
Last sector: 300294143 (at 143.2 GiB)
Partition size: 300290048 sectors (143.2 GiB)
Attribute flags: 0000000000000000
Partition name: 

Command (? for help): i
Partition number (1-3): 3
Partition GUID code: 0657FD6D-A4AB-43C4-84E5-0933C84B4F4F (Linux swap)
Partition unique GUID: FDCFEECD-31F4-450F-BBDD-AC02364C1E74
First sector: 300294144 (at 143.2 GiB)
Last sector: 312580095 (at 149.0 GiB)
Partition size: 12285952 sectors (5.9 GiB)
Attribute flags: 0000000000000000
Partition name: 

```> **oldfred said:**
> 
 run this if you have gpt:
sudo parted /dev/sda unit s print

```

root@debian:/home/user/Downloads# sudo parted /dev/sda unit s print
Model: ATA FUJITSU MHZ2160B (scsi)
Disk /dev/sda: 312581808s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start       End         Size        File system     Name  Flags
 1      2048s       4095s       2048s                             bios_grub
 2      4096s       300294143s  300290048s  ext4
 3      300294144s  312580095s  12285952s   linux-swap(v1)


```

Below is my boot info script results.txt:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 2048 of the 
    same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1         4,095         4,095  ee GPT
/dev/sda2    *          4,096   300,294,143   300,290,048  83 Linux
/dev/sda3         300,294,144   312,580,095    12,285,952  82 Linux swap / Solaris


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1           2,048         4,095         2,048 Bios Boot Partition
/dev/sda2           4,096   300,294,143   300,290,048 Linux or Data
/dev/sda3     300,294,144   312,580,095    12,285,952 Linux Swap

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        a0946e6a-569b-4e19-8567-772fe1495a53   ext4                                     
/dev/sda3        3b4f7b28-deb4-4eee-9f81-cdf7626a0a83   swap                                     
/dev/sda: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /live/image              iso9660    (ro,noatime)


=========================== sda2/boot/grub/grub.cfg: ===========================

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

insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set a0946e6a-569b-4e19-8567-772fe1495a53
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set a0946e6a-569b-4e19-8567-772fe1495a53
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set a0946e6a-569b-4e19-8567-772fe1495a53
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=a0946e6a-569b-4e19-8567-772fe1495a53 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set a0946e6a-569b-4e19-8567-772fe1495a53
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=a0946e6a-569b-4e19-8567-772fe1495a53 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set a0946e6a-569b-4e19-8567-772fe1495a53
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a0946e6a-569b-4e19-8567-772fe1495a53 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set a0946e6a-569b-4e19-8567-772fe1495a53
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a0946e6a-569b-4e19-8567-772fe1495a53 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set a0946e6a-569b-4e19-8567-772fe1495a53
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set a0946e6a-569b-4e19-8567-772fe1495a53
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=3b4f7b28-deb4-4eee-9f81-cdf7626a0a83 none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


 116.1GB: boot/grub/core.img
 116.1GB: boot/grub/grub.cfg
 143.9GB: boot/initrd.img-2.6.35-22-generic
 143.9GB: boot/initrd.img-2.6.35-23-generic
 116.1GB: boot/vmlinuz-2.6.35-22-generic
 116.2GB: boot/vmlinuz-2.6.35-23-generic
 143.9GB: initrd.img
 143.9GB: initrd.img.old
 116.2GB: vmlinuz
 116.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  52 e8 28 01 74 08 56 be  33 81 e8 4c 01 5e bf f4  |R.(.t.V.3..L.^..|
00000010  81 66 8b 2d 83 7d 08 00  0f 84 e9 00 80 7c ff 00  |.f.-.}.......|..|
00000020  74 46 66 8b 1d 66 8b 4d  04 66 31 c0 b0 7f 39 45  |tFf..f.M.f1...9E|
00000030  08 7f 03 8b 45 08 29 45  08 66 01 05 66 83 55 04  |....E.)E.f..f.U.|
00000040  00 c7 04 10 00 89 44 02  66 89 5c 08 66 89 4c 0c  |......D.f.\.f.L.|
00000050  c7 44 06 00 70 50 c7 44  04 00 00 b4 42 cd 13 0f  |.D..pP.D....B...|
00000060  82 bb 00 bb 00 70 eb 68  66 8b 45 04 66 09 c0 0f  |.....p.hf.E.f...|
00000070  85 a3 00 66 8b 05 66 31  d2 66 f7 34 88 54 0a 66  |...f..f1.f.4.T.f|
00000080  31 d2 66 f7 74 04 88 54  0b 89 44 0c 3b 44 08 0f  |1.f.t..T..D.;D..|
00000090  8d 83 00 8b 04 2a 44 0a  39 45 08 7f 03 8b 45 08  |.....*D.9E....E.|
000000a0  29 45 08 66 01 05 66 83  55 04 00 8a 54 0d c0 e2  |)E.f..f.U...T...|
000000b0  06 8a 4c 0a fe c1 08 d1  8a 6c 0c 5a 52 8a 74 0b  |..L......l.ZR.t.|
000000c0  50 bb 00 70 8e c3 31 db  b4 02 cd 13 72 50 8c c3  |P..p..1.....rP..|
000000d0  8e 45 0a 58 c1 e0 05 01  45 0a 60 1e c1 e0 03 89  |.E.X....E.`.....|
000000e0  c1 31 ff 31 f6 8e db fc  f3 a5 1f e8 3e 00 74 06  |.1.1........>.t.|
000000f0  be 3b 81 e8 63 00 61 83  7d 08 00 0f 85 1d ff 83  |.;..c.a.}.......|
00000100  ef 0c e9 0f ff e8 24 00  74 06 be 3d 81 e8 49 00  |......$.t..=..I.|
00000110  5a ea 00 82 00 00 be 40  81 e8 3d 00 eb 06 be 45  |Z......@..=....E|
00000120  81 e8 35 00 be 4a 81 e8  2f 00 eb fe bb 17 04 80  |..5..J../.......|
00000130  27 03 c3 6c 6f 61 64 69  6e 67 00 2e 00 0d 0a 00  |'..loading......|
00000140  47 65 6f 6d 00 52 65 61  64 00 20 45 72 72 6f 72  |Geom.Read. Error|
00000150  00 bb 01 00 b4 0e cd 10  46 8a 04 3c 00 75 f2 c3  |........F..<.u..|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 01 08 00 00  00 00 00 00 2e 00 20 08  |.............. .|
00000200


```

---

### Post by oldfred on 2010-12-09
I cannot see anything wrong. I also installed gpt to a 160GB drive just to learn about gpt and have maverick installed to it, but my daily boot is still Lucid. My boot script looks a lot like yours except I partitioned before they changed to default of 2048 so I start at 34 and I have another data partition. The script does not parse the bios_grub partition to find core.img but it is ok.

I would first just try reinstalling grub2 to the MBR.

#Install MBR from LiveCD, Ubuntu install on sda2 and want grub2 in drive sda's MBR:
#Find linux partition, change sda2 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
#confirm that linux is sda2
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

---

### Post by srs5694 on 2010-12-09
> **ghiblian said:**
> ```
 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 2048 of the 
    same hard drive for core.img, but core.img can not be found at this 
    location.

```

This is the problem: Something seems to have wiped the boot code from /dev/sda1 (your BIOS Boot Partition). It's unclear to me what did this, since from your description there's nothing that should have done this, unless perhaps you did something else *before* the crash that might have damaged your GRUB installation. (Maybe a GRUB re-installation or some mucking about with dd or partitioning tools.)

On my system, the Boot Info Script *does* parse the BIOS Boot Partition; here's the relevant output on one of my systems:

```

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 976768065 
    of the same hard drive for core.img, core.img is at this location on 
    /dev/sda and looks on partition #2 for /grub.

```

That said, there could be version-to-version differences in the script, or perhaps in the version of the boot code, which could affect the script's ability to correctly identify the code. Thus, I can't really be 100% certain that the code is missing from your system, but it seems likely.

I concur with oldfred that you should attempt to re-install GRUB to the MBR of the disk. Doing so will cause it to locate the BIOS Boot Partition and re-install the relevant parts of itself there, too.

---

### Post by srs5694 on 2010-12-09
> **oldfred said:**
> I would first just try reinstalling grub2 to the MBR.

#Install MBR from LiveCD, Ubuntu install on sda2 and want grub2 in drive sda's MBR:
#Find linux partition, change sda2 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l

Note that since this is a GPT disk, fdisk won't return good data. The output posted earlier does clearly identify /dev/sda2 as the Linux root and boot partition.

Another way to re-install GRUB is to use the [Super GRUB 2 Disk](http://www.supergrubdisk.org/) to boot into the normal system and then type "sudo grub-install /dev/sda".

---

### Post by ghiblian on 2010-12-09
> **srs5694 said:**
> Another way to re-install GRUB is to use the [Super GRUB 2 Disk]("http://www.supergrubdisk.org/") to boot into the normal system and then type "sudo grub-install /dev/sda".

Yes!! Your solution has actually made my computer better than it was before: with the reinstall of GRUB, I no longer see the the menu of outdated OS versions, and it boots straight into Ubuntu. Thanks!

---

