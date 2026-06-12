---
title: "Windows install stopped loading after Ubuntu WUBI install"
date: 2009-11-22
forum: General Help
---

### Post by Bullfrog245 on 2009-11-22
I have recently installed Ubuntu 9.10 through windows (I believe this is called a WUBI install) and Ubuntu is working great (besides a CD/DVD issue, but I have another thread about that.  The problem now is that Windows won't start anymore.

I think the issue may be that I installed a NTFS configuration tool to get my hard drives to mount at start-up so that I didn't have to mount them individually once Ubuntu starts.  One of these drives has my windows partition on it.

When I start windows, it loads until windows splash screen, then restarts.  I don't actually see the splash, it restarts just before it.  If I try to start windows in safe mode, everything loads fine, it hangs for a few seconds on the mup.sys (which I think is normal), then I get an option at the bottom that says to press escape to stop loading some file, then the computer restarts.  Its a "gentle" restart, as my CPU fans keep running, and the monitors don't loose signal.  Instead of the windows screen, I see my motherboard splash screen instead.

Any ideas?

---

### Post by lisati on 2009-11-22
First of all, don't panic, your request for help has been noticed.

I don't know if this is relevant: A year or so back I had a similar problem with XP restarting after a botched installation of Ubuntu (this one was in its own partition, not via Wubi). Turns out that my troubles with XP were unrelated to Ubuntu, there was a patch from my computer's manufacturer that I needed on my XP installation before installing XP's SP3. Long story short, I ended up backing up my data and doing a complete reinstall of both XP and Ubuntu.

---

### Post by Bullfrog245 on 2009-11-22
No panic here.  All of my data is intact, and that's the important thing.

You helped me to remember something that may be of importance, though.  I first installed Ubuntu (I think it was 8.10) through Wubi a year ago.  Everything worked fine.  I upgraded to 9.04 through the update manager, and everything was still fine.  I then got into a game that I couldn't get to work in ubuntu, so I booted windows exclusively for a couple of months.  When I came back to ubuntu, it would freeze after a couple of seconds.

I uninstalled 9.04 through windows using "add or remove programs", then downloaded and installed 9.10 using wubi.  I don't know if windows would have booted immediately after the install, because I didn't try.  So it could be something from the previous install, this install, or something I've done in the last two days...  I guess that made things more complicated :(

But like I said, no panic yet :)

---

### Post by hungryOrb on 2009-11-22
maybe try a:

```
sudo update-grub
```

---

### Post by Bullfrog245 on 2009-11-22
I tried the update-grub command.  It ran and gave two errors, both saying that a file could not be found.  The errors came from two partitions on an external hard drive, and since I only use them for storage (and have never booted from them) that's probably the reason.

I ran a boot-info script that I saw in a different thread.  I don't know if any of this is important, but here are the results.  I believe that Windows is installed on sda1.  It's a 20GB partition of a larger drive.  I think that sda2 is the rest of the windows drive.

The Grub0.97 I think was installed with Ubuntu 7.10.  I actually did a proper dual boot install for it, but accidentally turned it into Mythbuntu when trying to get a capture card to work.  I abandoned it and forgot about it until now.  If anyone knows how to get rid of that, I'm open for suggestions :)


```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 7.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2a422a41

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sda2          81,931,500   312,576,704   230,645,205   7 HPFS/NTFS
/dev/sda3          40,965,750    44,082,359     3,116,610   f W95 Ext d (LBA)
/dev/sda5          40,965,813    44,082,359     3,116,547  82 Linux swap / Solaris
/dev/sda4          44,082,360    81,931,499    37,849,140  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0b6291cd

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 61.5 GB, 61475807232 bytes
255 heads, 63 sectors/track, 7474 cylinders, total 120069936 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00630063

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   120,053,744   120,053,682   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44fdfe06

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63       819,314       819,252   7 HPFS/NTFS
/dev/sdd2             819,315   717,623,549   716,804,235   7 HPFS/NTFS
/dev/sdd3         717,623,550 1,465,144,064   747,520,515   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: UUID="d83cda09-43e4-4fbf-95a2-ab3c6592b257" TYPE="ext4" 
/dev/sda1: UUID="F2C809E4C809A7C5" LABEL="Windows" TYPE="ntfs" 
/dev/sda2: UUID="5EC4A92AC4A904FD" LABEL="File Box" TYPE="ntfs" 
/dev/sda4: UUID="7a4fcf9c-0c51-4c80-8b73-e0cfdf77d568" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="de669af1-7eee-45bc-8fc0-45eaa19c23f7" TYPE="swap" 
/dev/sdb1: UUID="96D4A8F5D4A8D8AF" LABEL="Movies" TYPE="ntfs" 
/dev/sdc1: UUID="D0304C9A304C8A04" LABEL="Bullfrog" TYPE="ntfs" 
/dev/sdd1: UUID="603896A0389674AE" LABEL="WD Software" TYPE="ntfs" 
/dev/sdd2: UUID="36D4CC3DD4CBFD5D" LABEL="Nintendo" TYPE="ntfs" 
/dev/sdd3: UUID="E468ED2F68ED0162" LABEL="Backup" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/loop0 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdc1 on /host type fuseblk (rw)
/dev/sdb1 on /media/Movies type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /media/File Box type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/Windows type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bullfrog/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bullfrog)
/dev/sdd1 on /media/WD Software type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=512)
/dev/sdd3 on /media/Backup type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdd2 on /media/Nintendo type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /noguiboot
C:\wubildr.mbr = "Ubuntu"

=========================== sda4/boot/grub/menu.lst: ===========================

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
default		6

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		0

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
# kopt=root=UUID=7a4fcf9c-0c51-4c80-8b73-e0cfdf77d568 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=7a4fcf9c-0c51-4c80-8b73-e0cfdf77d568 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=7a4fcf9c-0c51-4c80-8b73-e0cfdf77d568 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7a4fcf9c-0c51-4c80-8b73-e0cfdf77d568 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7a4fcf9c-0c51-4c80-8b73-e0cfdf77d568 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=7a4fcf9c-0c51-4c80-8b73-e0cfdf77d568 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=F2C809E4C809A7C5 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=5EC4A92AC4A904FD /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=96D4A8F5D4A8D8AF /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc1
UUID=16B861CBB861A9C7 /media/sdc1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdd1
UUID=D0304C9A304C8A04 /media/sdd1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=de669af1-7eee-45bc-8fc0-45eaa19c23f7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

=================== sda4: Location of files loaded by Grub: ===================


  22.5GB: boot/grub/menu.lst
  22.5GB: boot/grub/stage2
  22.5GB: boot/initrd.img-2.6.22-14-generic
  22.5GB: boot/initrd.img-2.6.22-14-generic.bak
  22.5GB: boot/initrd.img-2.6.22-15-generic
  22.5GB: boot/initrd.img-2.6.22-15-generic.bak
  22.5GB: boot/vmlinuz-2.6.22-14-generic
  22.5GB: boot/vmlinuz-2.6.22-15-generic
  22.5GB: initrd.img
  22.5GB: initrd.img.old
  22.5GB: vmlinuz
  22.5GB: vmlinuz.old

================================== sdc1Wubi: ==================================

Operating System: "Ubuntu 9.10"

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
/host/ubuntu/disks/root.disk / ext4 loop,errors=remount-ro 0 1
/host/ubuntu/disks/swap.disk none swap loop,sw 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdb1 /media/Movies ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda2 /media/File\040Box ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/Windows ntfs-3g defaults,locale=en_US.UTF-8 0 0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  cd 91 62 0b 00 00 00 01  |..........b.....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 42 45 1c 1d 00 00  |......?...BE....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by fluffman86 on 2009-11-23
You've definitely got a corrupt Windows system file that's keeping windows from booting.  This was either caused by mounting/unmounting your /host drive improperly, or by something going wrong in windows that's completely unrelated.  

Backup and reinstall, or do a repair from your Windows CD.  Next time when installing Ubuntu, try a full install on its own partition.  Ubuntu likes that better, and so does windows. :)

---

