---
title: "Gave up waiting for root device"
date: 2011-02-27
forum: General Help
---

### Post by almanik on 2011-02-27
Hi, this is my first post and I have recently installed Ubuntu 10.10 on my computer. After updating using update manager and restarting it the computer now goes to a Grub screen to choose which kernel to use. After choosing one it goes to another screen for around 10-15 seconds then says:

"Gave up waiting for root device" and some other things which I can't remember.  I've read some other posts and I've run the boot info script which is here:
Edit: I can mount the drive sdb1 through the liveusb, could it be not waiting for the right device?

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 8011 MB, 8011120640 bytes
41 heads, 41 sectors/track, 9307 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          8,064    15,646,719    15,638,656   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       cfffc50f-2fca-3d41-94cc-2ce1e7b7a654   ext2       casper-rw                     
/dev/sda1        170E-133A                              vfat       PENDRIVE                      
/dev/sda: PTTYPE="dos" 
error: block: No such file or directory
error: devices: No such file or directory
error: /dev/mapper/no: No such file or directory
error: found: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 80 1f 00 00  |........?.......|
00000020  80 a0 ee 00 da 76 00 00  00 00 00 00 02 00 00 00  |.....v..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 3a 13 0e 17 4e  4f 20 4e 41 4d 45 20 20  |..):...NO NAME  |
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
00000100  7d 00 66 b8 d8 ed 00 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
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

no block devices found 
```

---

### Post by almanik on 2011-02-28
Bump

---

### Post by sikander3786 on 2011-02-28
Welcome to the forums and apologies for the delayed response :-)

Your internal HDD is not being read by the boot script. Can you please check in your Bios if it is being detected there?

The only thing boot script is reporting is your USB drive.

> =========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: [COLOR="Red"]8011[/COLOR] MB, 8011120640 bytes
41 heads, 41 sectors/track, 9307 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


We need to find your HDD first.

---

### Post by almanik on 2011-02-28
The Hard Drive does work, it shows up on the BIOS and is the first boot option. It goes to a screen where I choose a kernel version then another screen where it says gave up waiting for boot device. I even did a fresh reinstall and it still happens, and when I tried to boot into live USB it hangs.

---

### Post by sikander3786 on 2011-02-28
Please boot an Ubuntu Live CD/USB and go to System > Administration > GParted and post a screenshot.

Also, from Applications > Accessories > Terminal, post the output of these commands.

```
sudo fdisk -l
sudo parted -l
```

Boot script is not picking up your Hard Disk at all. I wonder if there are any related problems with the hardware.

In the mean time, I would recommend to download the diagnostic tools from your HDD manufacturer's website and see if any errors are reported.

Missing HDD in boot script output is very rare and un-common.

---

### Post by almanik on 2011-03-01
> **sikander3786 said:**
> Please boot an Ubuntu Live CD/USB and go to System > Administration > GParted and post a screenshot.

Also, from Applications > Accessories > Terminal, post the output of these commands.

```
sudo fdisk -l
sudo parted -l
```Boot script is not picking up your Hard Disk at all. I wonder if there are any related problems with the hardware.

In the mean time, I would recommend to download the diagnostic tools from your HDD manufacturer's website and see if any errors are reported.

Missing HDD in boot script output is very rare and un-common.

Sorry about the late reply, had school.

FDISK:
```
Disk /dev/sdb: 8011 MB, 8011120640 bytes
41 heads, 41 sectors/track, 9307 cylinders
Units = cylinders of 1681 * 512 = 860672 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           5        9308     7819328    c  W95 FAT32 (LBA)

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000231ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       29637   238053376   83  Linux
/dev/sdc2           29637       30402     6142977    5  Extended
/dev/sdc5           29637       30402     6142976   82  Linux swap / Solaris

Disk /dev/sda: 2000.4 GB, 2000398933504 bytes
255 heads, 62 sectors/track, 247123 cylinders
Units = cylinders of 15810 * 512 = 8094720 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      247124  1953512000+   7  HPFS/NTFS

```PARTED:
```
Model: Seagate FA GoFlex Desk (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2000GB  2000GB  primary  ntfs


Model: Kingston DT 101 G2 (scsi)
Disk /dev/sdb: 8011MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  8011MB  8007MB  primary  fat32        boot, lba


Model: ATA ST9250827AS (scsi)
Disk /dev/sdc: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  244GB  244GB   primary   ext4            boot
 2      244GB   250GB  6290MB  extended
 5      244GB   250GB  6290MB  logical   linux-swap(v1)

```Screenshot:

---

### Post by Rubi1200 on 2011-03-01
Very interesting. I wonder if the fact that there is no boot flag on sda might have something to do with the initial results both from the script and the error message?

Linux does not need the boot flag, but Windows does (indicated by the asterisk * next to the drive/partition).

I would wait until sikander3786 comments on this, but you may need to use GParted from the LiveCD to add the boot flag to sda.

---

### Post by sikander3786 on 2011-03-01
Yes a boot flag is definitely needed on sda1 as Rubi1200 suggested above. Right click sda1 in GParted > Manage Flags > Enable Boot and Apply.

Reboot and re-run boot script. Are the HDDs mentioned in the Results.txt this time?

For the initial issue, mount the sdc1 drive in Live CD and post the contents of undermentioned files as an alternative to boot script output.

The files will be there only if the install was successful. Lets see.

```
/boot/grub/grub.cfg
/etc/fstab
```

And the output of this command.

```
sudo blkid
```

You mentioned in your fist post that you are able to mount sdb1 under Live USB. Does that mean that sdb1 was your root partition then? I wonder if your drives are switching themselves due to some Bios configuration or master/slave settings.

Rubi1200 or some other senior member might have better suggestions on this.

---

### Post by almanik on 2011-03-01
> **sikander3786 said:**
> Yes a boot flag is definitely needed on sda1 as Rubi1200 suggested above. Right click sda1 in GParted > Manage Flags > Enable Boot and Apply.

Reboot and re-run boot script. Are the HDDs mentioned in the Results.txt this time?

For the initial issue, mount the sdc1 drive in Live CD and post the contents of undermentioned files as an alternative to boot script output.

The files will be there only if the install was successful. Lets see.

```
/boot/grub/grub.cfg
/etc/fstab
```And the output of this command.

```
sudo blkid
```You mentioned in your fist post that you are able to mount sdb1 under Live USB. Does that mean that sdb1 was your root partition then? I wonder if your drives are switching themselves due to some Bios configuration or master/slave settings.

Rubi1200 or some other senior member might have better suggestions on this.
Currently my root drive should be sdc1  the 250GB one. The current sda1 is a portable hard drive used for storage.

---

### Post by sikander3786 on 2011-03-01
Yes the current one is sdc1 as mentioned above in the outputs. I was talking about your first post.

> Edit: I can mount the drive sdb1 through the liveusb, could it be not waiting for the right device?

And boot flag will go to sda1, the partition with Windows install.

---

### Post by almanik on 2011-03-01
> **sikander3786 said:**
> Yes a boot flag is definitely needed on sda1 as Rubi1200 suggested above. Right click sda1 in GParted > Manage Flags > Enable Boot and Apply.

Reboot and re-run boot script. Are the HDDs mentioned in the Results.txt this time?

For the initial issue, mount the sdc1 drive in Live CD and post the contents of undermentioned files as an alternative to boot script output.

The files will be there only if the install was successful. Lets see.

```
/boot/grub/grub.cfg
/etc/fstab
```And the output of this command.

```
sudo blkid
```You mentioned in your fist post that you are able to mount sdb1 under Live USB. Does that mean that sdb1 was your root partition then? I wonder if your drives are switching themselves due to some Bios configuration or master/slave settings.

Rubi1200 or some other senior member might have better suggestions on this.

Boot Info:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398933504 bytes
255 heads, 62 sectors/track, 247123 cylinders, total 3907029167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63 3,907,024,063 3,907,024,001   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8011 MB, 8011120640 bytes
41 heads, 41 sectors/track, 9307 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064    15,646,719    15,638,656   c W95 FAT32 (LBA)


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048   476,108,799   476,106,752  83 Linux
/dev/sdc2         476,110,846   488,396,799    12,285,954   5 Extended
/dev/sdc5         476,110,848   488,396,799    12,285,952  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A2ECED3FECED0DFB                       ntfs       FreeAgent GoFlex Drive        
/dev/sda: PTTYPE="dos" 
/dev/sdb1        170E-133A                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        b8e0582a-f89c-47f6-a2df-a820f1be26d1   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        d4395323-4351-40a4-b85d-a53be893e4ae   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/b8e0582a-f89c-47f6-a2df-a820f1be26d1 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set b8e0582a-f89c-47f6-a2df-a820f1be26d1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set b8e0582a-f89c-47f6-a2df-a820f1be26d1
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
    search --no-floppy --fs-uuid --set b8e0582a-f89c-47f6-a2df-a820f1be26d1
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b8e0582a-f89c-47f6-a2df-a820f1be26d1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b8e0582a-f89c-47f6-a2df-a820f1be26d1
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b8e0582a-f89c-47f6-a2df-a820f1be26d1 ro single 
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
    search --no-floppy --fs-uuid --set b8e0582a-f89c-47f6-a2df-a820f1be26d1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b8e0582a-f89c-47f6-a2df-a820f1be26d1
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=b8e0582a-f89c-47f6-a2df-a820f1be26d1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=d4395323-4351-40a4-b85d-a53be893e4ae none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


 219.1GB: boot/grub/core.img
   4.4GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-22-generic
 219.1GB: boot/vmlinuz-2.6.35-22-generic
    .8GB: initrd.img
 219.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 80 1f 00 00  |........?.......|
00000020  80 a0 ee 00 da 76 00 00  00 00 00 00 02 00 00 00  |.....v..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 3a 13 0e 17 4e  4f 20 4e 41 4d 45 20 20  |..):...NO NAME  |
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
00000100  7d 00 66 b8 d8 ed 00 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
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

Unknown BootLoader  on sdc2

00000000  ed ae 07 80 c2 13 08 03  0a 2f ab de 86 ae bd 10  |........./......|
00000010  e5 2b c2 d3 ad eb 18 10  a1 1c 4e 69 fd 83 eb 4a  |.+........Ni...J|
00000020  0a 11 c4 13 04 60 27 b3  ba a3 dc 5e 6c d7 3c 01  |.....`'....^l.<.|
00000030  e3 81 01 b1 84 c8 78 59  d3 40 51 9b ae f6 b2 23  |......xY.@Q....#|
00000040  e9 dc bf df 0f 20 84 6c  32 f7 0f 24 1a 04 eb d9  |..... .l2..$....|
00000050  1d ee 28 c7 78 5e cb 75  3e 97 96 13 54 b4 c4 8c  |..(.x^.u>...T...|
00000060  76 8f 77 5d 99 5f 22 b4  b6 96 a5 c1 3e 8c c7 1d  |v.w]._".....>...|
00000070  e9 a7 03 96 02 77 7e e7  7b ee e5 63 a3 a9 d4 2e  |.....w~.{..c....|
00000080  7f 0f c5 fd 7d df bf 3e  08 d1 f1 59 3a de ea f6  |....}..>...Y:...|
00000090  15 89 f3 98 d3 89 e9 b2  bb bf bc 9a b8 57 66 e5  |.............Wf.|
000000a0  db 42 1e ed dc 11 63 0f  6f 2d 2a 99 d5 2e dc 7e  |.B....c.o-*....~|
000000b0  d7 fe d9 be 36 49 ac 23  87 c1 80 bd 34 ff fd c4  |....6I.#....4...|
000000c0  ce fb 25 a4 ae fe bd fe  4a bf 40 9f df a0 5e ca  |..%.....J.@...^.|
000000d0  86 7b a7 d8 b7 08 a8 0e  da 96 ff fe 71 86 d5 f3  |.{..........q...|
000000e0  8d 6a e7 85 7d 7b 5e a2  43 df 8a f5 a5 a5 57 fd  |.j..}{^.C.....W.|
000000f0  6f 33 54 15 f7 2e 72 c3  39 3b 17 7e f2 f4 47 f9  |o3T...r.9;.~..G.|
00000100  e9 51 84 66 48 b7 15 d7  b2 fd a9 91 7c 25 82 03  |.Q.fH.......|%..|
00000110  db d7 5a 43 71 b5 aa d7  eb a5 37 32 aa 3e 29 f4  |..ZCq.....72.>).|
00000120  7a 9f fe f5 6e ea f6 97  74 9a 5d f9 49 f1 c4 e0  |z...n...t.].I...|
00000130  c9 97 dd 24 24 0c 2c 00  0f 3f f2 6c a7 48 e2 a2  |...$$.,..?.l.H..|
00000140  81 02 83 05 ff 6f ca 32  29 68 b9 95 07 92 b2 a8  |.....o.2)h......|
00000150  1f 80 64 5c 23 59 bb 4a  1f 02 96 4a cd ec 14 6f  |..d\#Y.J...J...o|
00000160  77 6a c0 24 03 54 03 b2  f6 48 0c f7 0c fd e3 cd  |wj.$.T...H......|
00000170  58 bc a4 89 c0 75 26 30  41 1a 18 b6 3d e1 75 37  |X....u&0A...=.u7|
00000180  47 ad 2d 65 e4 10 14 13  6d c4 8e 0c 49 ac 52 3e  |G.-e....m...I.R>|
00000190  f6 a3 b4 d2 c3 b3 19 0c  ba 3e 66 5a 28 8e f7 a2  |.........>fZ(...|
000001a0  25 34 25 fa db 72 21 a4  89 c3 7c a4 b3 52 33 c8  |%4%..r!...|..R3.|
000001b0  50 48 86 23 9a 86 9b a2  1e a8 c6 97 a4 21 00 fe  |PH.#.........!..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 bb 00 00 00  |...........x....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```GRUB.CFG
```
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
search --no-floppy --fs-uuid --set b8e0582a-f89c-47f6-a2df-a820f1be26d1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set b8e0582a-f89c-47f6-a2df-a820f1be26d1
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
    search --no-floppy --fs-uuid --set b8e0582a-f89c-47f6-a2df-a820f1be26d1
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b8e0582a-f89c-47f6-a2df-a820f1be26d1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b8e0582a-f89c-47f6-a2df-a820f1be26d1
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b8e0582a-f89c-47f6-a2df-a820f1be26d1 ro single 
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
    search --no-floppy --fs-uuid --set b8e0582a-f89c-47f6-a2df-a820f1be26d1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b8e0582a-f89c-47f6-a2df-a820f1be26d1
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
```FSTAB:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=b8e0582a-f89c-47f6-a2df-a820f1be26d1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=d4395323-4351-40a4-b85d-a53be893e4ae none            swap    sw              0       0
```BLKID:
```
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="FreeAgent GoFlex Drive" UUID="A2ECED3FECED0DFB" TYPE="ntfs" 
/dev/sdb1: LABEL="PENDRIVE" UUID="170E-133A" TYPE="vfat" 
/dev/sdc1: UUID="b8e0582a-f89c-47f6-a2df-a820f1be26d1" TYPE="ext4" 
/dev/sdc5: UUID="d4395323-4351-40a4-b85d-a53be893e4ae" TYPE="swap" 
```The HD with Ubuntu 10.10 on it had to be mounted with Disk Utility i.e. it didn't auto-mount. Don't know if that means anything.

---

### Post by sikander3786 on 2011-03-01
The drives don't need to be mounted manually for the boot script to read them. Strange. I have reported it lets see what the developers come up with.

[http://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4390488](http://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4390488)

Grub seems pretty ok to me. Everything is in its place. No problem with UUIDs either. In these type of cases, the best practice is to purge and re-install Grub2 from a Live CD. See here.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
courtesy of forum member *drs305*

I hope you'll be up and running again soon.

Good Luck!

---

### Post by almanik on 2011-03-01
> **sikander3786 said:**
> The drives don't need to be mounted manually for the boot script to read them. Strange. I have reported it lets see what the developers come up with.

[http://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4390488](http://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4390488)

Grub seems pretty ok to me. Everything is in its place. No problem with UUIDs either. In these type of cases, the best practice is to purge and re-install Grub2 from a Live CD. See here.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
courtesy of forum member *drs305*



Good Luck!

Thank you! Purging and reinstalling grub worked! 
EDIT: Spoke too soon, rebooted and it happened again >.<

---

### Post by sikander3786 on 2011-03-01
So, the problem reappeared after a reboot. Sad.

Can you please try once more. Run the bootinfoscirpt once when the drives are un-mounted and once when they are manually mounted and please post the results.

This is taking longer than expected and you need to be patient throughout :-)

---

### Post by alphaamanitin on 2011-03-01
> **almanik said:**
> Thank you! Purging and reinstalling grub worked! 
EDIT: Spoke too soon, rebooted and it happened again >.<


I would redo that and update grub before rebooting.  ```
sudo update-grub
```

AlphaA

PS-not super skilled in Ubuntu.

---

### Post by almanik on 2011-03-02
> **sikander3786 said:**
> So, the problem reappeared after a reboot. Sad.

Can you please try once more. Run the bootinfoscirpt once when the drives are un-mounted and once when they are manually mounted and please post the results.

This is taking longer than expected and you need to be patient throughout :-)

I may have found the problem, I am unable to boot normally but if I click the (recovery mode) kernel instead of the normal it always boots. I choose failsafeX option and I am able to boot normally. What's all this then?:confused:

---

### Post by Rubi1200 on 2011-03-02
As sikander3786 already suggested, run the boot info script again.

Perhaps this time we can find something that will point out what is going on with your setup.

---

### Post by foontas on 2011-03-05
I just thought I'd add my two cents here.

I had this problem for a while, but silly me, it looks like it was just the hard drive set to "slave" rather than master. I figured that out when I installed a new hard drive, once i changed the pins, and made sure i had the right connections, the problem seemed to go away.

---

