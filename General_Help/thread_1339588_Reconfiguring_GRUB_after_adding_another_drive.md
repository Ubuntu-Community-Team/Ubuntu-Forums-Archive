---
title: "Reconfiguring GRUB after adding another drive"
date: 2009-11-27
forum: General Help
---

### Post by dans1337 on 2009-11-27
I screwed up nicely this time. It's a good way to learn linux, I suppose. I've been reading forum posts and documentation on GRUB for a few days now with no luck.

What I'm stuck with here, is /dev/sda has Ubuntu 9.04 on it. sda1 is swap, sda2 is root, and sda3 is /home.

sdb has Windows 7 and Kubuntu 9.10

Now, GRUB currently boots Kubuntu 9.10 by default, which is what I want, and I edited fstab to mount /home to sda3 so I could keep all my old apps and my VirtualBox VMs.

The problem is that booting Windows 7 produces and error:invalid signature. It was working until I changed the mount point for /home. Once I did that, GRUB found my old 9.04 kernels on sda and added them to the boot menu.

It appears that GRUB is actually now using sda2 for /boot... because that's where the menu.lst file is.

I no longer have a menu.lst in dev/sdb5/boot/grub which is where it used to be. (see below)

How should I reconfigure GRUB so that it no longer sees dev/sda2 as a bootable option, and how do I fix the Windows 7 boot?

Output of fdisk -l:

```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08f93ad8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         996     8000338+  82  Linux swap / Solaris
/dev/sda2   *         997        7318    50781465   83  Linux
/dev/sda3            7319       37712   244139805   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13be13be

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13       10534    84506624    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sdb3           10534       19457    71676360    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sdb5           10534       18728    65817328+  83  Linux
/dev/sdb6           18728       19457     5858968+  82  Linux swap / Solaris
```

Output of df /boot:
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb5             64782900   3571096  57920940   6% /

```

Output of ls /boot/grub:
```
915resolution.mod  cpio.mod      grub.cfg       lvm.mod         play.mod      ufs1.mod
acpi.mod           cpuid.mod     grubenv        mdraid.mod      png.mod       ufs2.mod
affs.mod           crc.mod       gzio.mod       memdisk.mod     probe.mod     uhci.mod
afs_be.mod         datehook.mod  halt.mod       memrw.mod       pxeboot.img   unicode.pf2
afs.mod            date.mod      handler.lst    minicmd.mod     pxecmd.mod    usb_keyboard.mod
aout.mod           datetime.mod  handler.mod    minix.mod       pxe.mod       usb.mod
ata.mod            device.map    hdparm.mod     mmap.mod        raid5rec.mod  usbms.mod
ata_pthru.mod      diskboot.img  hello.mod      moddep.lst      raid6rec.mod  usbtest.mod
at_keyboard.mod    dm_nv.mod     help.mod       msdospart.mod   raid.mod      vbeinfo.mod
befs_be.mod        drivemap.mod  hexdump.mod    multiboot.mod   read.mod      vbe.mod
befs.mod           echo.mod      hfs.mod        normal.mod      reboot.mod    vbetest.mod
biosdisk.mod       efiemu32.o    hfsplus.mod    ntfscomp.mod    reiserfs.mod  vga.mod
bitmap.mod         efiemu64.o    iso9660.mod    ntfs.mod        scsi.mod      vga_text.mod
blocklist.mod      efiemu.mod    jfs.mod        ohci.mod        search.mod    video_fb.mod
boot.img           elf.mod       jpeg.mod       part_acorn.mod  serial.mod    video.mod
boot.mod           ext2.mod      kernel.img     part_amiga.mod  setjmp.mod    videotest.mod
bsd.mod            extcmd.mod    keystatus.mod  part_apple.mod  sfs.mod       xfs.mod
bufio.mod          fat.mod       linux16.mod    part_gpt.mod    sh.mod        xnu.mod
cat.mod            font.mod      linux.mod      partmap.lst     sleep.mod     xnu_uuid.mod
cdboot.img         fs_file.mod   lnxboot.img    part_msdos.mod  tar.mod       zfsinfo.mod
chain.mod          fshelp.mod    loadenv.mod    part_sun.mod    terminfo.mod  zfs.mod
cmp.mod            fs.lst        loopback.mod   parttool.lst    test.mod
command.lst        fs_uuid.mod   lsmmap.mod     parttool.mod    tga.mod
configfile.mod     gfxterm.mod   ls.mod         password.mod    true.mod
core.img           gptsync.mod   lspci.mod      pci.mod         udf.mod

```

Output of ls /media/disk/boot/grub :
```
default     e2fs_stage1_5  installed-version  menu.lst   minix_stage1_5     stage1  xfs_stage1_5
device.map  fat_stage1_5   jfs_stage1_5       menu.lst~  reiserfs_stage1_5  stage2

```

Contents of /media/disk/boot/grub/menu.lst :
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a763d978-56d8-480d-b671-f5be934401db ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=a763d978-56d8-480d-b671-f5be934401db

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		a763d978-56d8-480d-b671-f5be934401db
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=a763d978-56d8-480d-b671-f5be934401db ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		a763d978-56d8-480d-b671-f5be934401db
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=a763d978-56d8-480d-b671-f5be934401db ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		a763d978-56d8-480d-b671-f5be934401db
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a763d978-56d8-480d-b671-f5be934401db ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		a763d978-56d8-480d-b671-f5be934401db
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a763d978-56d8-480d-b671-f5be934401db ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		a763d978-56d8-480d-b671-f5be934401db
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


```

---

### Post by dans1337 on 2009-11-27
I just realized GRUB2 is default on 9.10... and the config files are different.

/facepalm

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

Problem solved.

---

