---
title: "IDE &amp; SATA - Which one's which?"
date: 2009-11-07
forum: General Help
---

### Post by distortedecho on 2009-11-07
Hi, can someone help me please determine which HDD Ubuntu is installed on??

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xabb7ffe0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   163,855,439   163,855,377   7 HPFS/NTFS
/dev/sda2         163,855,440   488,391,119   324,535,680   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x844b844b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   315,066,779   315,066,717   7 HPFS/NTFS
/dev/sdb2         315,066,780   488,392,064   173,325,285   5 Extended
/dev/sdb5         315,066,843   485,420,039   170,353,197  83 Linux
/dev/sdb6         485,420,103   488,392,064     2,971,962  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/sdc: 1015 MB, 1015021568 bytes
32 heads, 61 sectors/track, 253 cylinders, total 495616 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1     ?   778,135,908 1,919,645,538 1,141,509,631  72 Unknown
/dev/sdc2     ?   168,689,522 2,104,717,761 1,936,028,240  65 Novell Netware 386
/dev/sdc3     ? 1,869,881,465 3,805,909,656 1,936,028,192  79 Unknown
/dev/sdc4     ? 2,885,681,152 2,885,736,650        55,499   d Unknown

/dev/sdc1 ends after the last sector of /dev/sdc
/dev/sdc1 overlaps with /dev/sdc2
/dev/sdc1 overlaps with /dev/sdc3
/dev/sdc2 ends after the last sector of /dev/sdc
/dev/sdc2 overlaps with /dev/sdc3
/dev/sdc3 ends after the last sector of /dev/sdc
/dev/sdc3 overlaps with /dev/sdc4
/dev/sdc4 ends after the last sector of /dev/sdc

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="9884BAFB84BADB48" TYPE="ntfs" 
/dev/sda2: UUID="5E407F3E407F1C49" LABEL="Storage" TYPE="ntfs" 
/dev/sdb1: UUID="E83CDFFB3CDFC2AC" TYPE="ntfs" 
/dev/sdb5: UUID="ed298760-5672-4486-87ba-3fc395b40e6a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: TYPE="swap" UUID="febf56c9-488d-4738-91f5-ef054f686c36" 
/dev/ramzswap0: TYPE="swap" 
/dev/sdc: LABEL="RICHARD_S I" UUID="04BF-CD93" TYPE="vfat" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc on /media/RICHARD_S I type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=ed298760-5672-4486-87ba-3fc395b40e6a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ed298760-5672-4486-87ba-3fc395b40e6a

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		ed298760-5672-4486-87ba-3fc395b40e6a
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ed298760-5672-4486-87ba-3fc395b40e6a ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		ed298760-5672-4486-87ba-3fc395b40e6a
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ed298760-5672-4486-87ba-3fc395b40e6a ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		ed298760-5672-4486-87ba-3fc395b40e6a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=ed298760-5672-4486-87ba-3fc395b40e6a /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=febf56c9-488d-4738-91f5-ef054f686c36 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 202.7GB: boot/grub/menu.lst
 202.7GB: boot/grub/stage2
 202.7GB: boot/initrd.img-2.6.28-11-generic
 202.6GB: boot/vmlinuz-2.6.28-11-generic
 202.7GB: initrd.img
 202.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 08 04 20 00  |.X.MSDOS5.0... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 90 07 00 f2 00 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 93 cd bf 04 52  49 43 48 41 52 44 5f 53  |..)....RICHARD_S|
00000050  20 49 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  | IFAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 08  |{......|.N..V@..|
00000070  cd 13 73 05 b9 ff ff 8a  f1 66 0f b6 c6 40 66 0f  |..s......f...@f.|
00000080  b6 d1 80 e2 3f f7 e2 86  cd c0 ed 06 41 66 0f b7  |....?.......Af..|
00000090  c9 66 f7 e1 66 89 46 f8  83 7e 16 00 75 38 83 7e  |.f..f.F..~..u8.~|
000000a0  2a 00 77 32 66 8b 46 1c  66 83 c0 0c bb 00 80 b9  |*.w2f.F.f.......|
000000b0  01 00 e8 2b 00 e9 48 03  a0 fa 7d b4 7d 8b f0 ac  |...+..H...}.}...|
000000c0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000d0  ee a0 fb 7d eb e5 a0 f9  7d eb e0 98 cd 16 cd 19  |...}....}.......|
000000e0  66 60 66 3b 46 f8 0f 82  4a 00 66 6a 00 66 50 06  |f`f;F...J.fj.fP.|
000000f0  53 66 68 10 00 01 00 80  7e 02 00 0f 85 20 00 b4  |Sfh.....~.... ..|
00000100  41 bb aa 55 8a 56 40 cd  13 0f 82 1c 00 81 fb 55  |A..U.V@........U|
00000110  aa 0f 85 14 00 f6 c1 01  0f 84 0d 00 fe 46 02 b4  |.............F..|
00000120  42 8a 56 40 8b f4 cd 13  b0 f9 66 58 66 58 66 58  |B.V@......fXfXfX|
00000130  66 58 eb 2a 66 33 d2 66  0f b7 4e 18 66 f7 f1 fe  |fX.*f3.f..N.f...|
00000140  c2 8a ca 66 8b d0 66 c1  ea 10 f7 76 1a 86 d6 8a  |...f..f....v....|
00000150  56 40 8a e8 c0 e4 06 0a  cc b8 01 02 cd 13 66 61  |V@............fa|
00000160  0f 82 54 ff 81 c3 00 02  66 40 49 0f 85 71 ff c3  |..T.....f@I..q..|
00000170  4e 54 4c 44 52 20 20 20  20 20 20 00 00 00 00 00  |NTLDR      .....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200

Unknown BootLoader  on sdc1


Unknown BootLoader  on sdc2


Unknown BootLoader  on sdc3


Unknown BootLoader  on sdc4



=============================== StdErr Messages: ===============================

hexdump: /dev/sdc1: No such file or directory
hexdump: /dev/sdc1: No such file or directory
hexdump: /dev/sdc2: No such file or directory
hexdump: /dev/sdc2: No such file or directory
hexdump: /dev/sdc3: No such file or directory
hexdump: /dev/sdc3: No such file or directory
hexdump: /dev/sdc4: No such file or directory
hexdump: /dev/sdc4: No such file or directory
```

Basically...

I have 2 hard-drives in my PC.
BOTH have a Windows partition.

My IDE drive was a Windows pc which I moved to my new Dell.
The Dell is SATA, so I basically lost a CD-ROM to house my IDE drive. This Dell was originally installed with Windows also - but I dual booted Ubuntu 9.4 (now 9.10)

In my mind, the IDE drive can now be wiped and used purely for storage. 
The SATA drive "SHOULD" be the hdd with Ubuntu on it - but how can I confirm this???

There is a STORAGE partition, which I think may be on the IDE drive - how can I tell?

The intention is to have the SATA drive as purely Ubuntu (250gb)
And the IDE drive as Storage (so I will delete the Windows partition and extend the Storage partition.

When I look in File manager, Ubuntu has mounted 2 NTFS partitions which when I browse I can see as Windows directories. However, these show as 84GB and 161GB. When I look in Gparted, these partition sizes don't exist/correspond.

I just want to make sure I'm deleting and extending the right partitions.

I'll also need some advice on the best tool for this job.

---

### Post by coffeecat on 2009-11-07
The best tool for the job is Gparted. The reason the partition sizes don't correspond may be that Gparted is reporting in Gibibytes, and the file manager (possibly) in Gigabytes. 

1 gibibyte = 1073741824bytes

1 gigabyte = 1000000000bytes

But I'm concerned that Gparted is not showing one of the partitions - or so I understand from your post.

The best thing would be to open Gparted again and post screenshots of the Gparted window for both sda and sdb.

---

### Post by distortedecho on 2009-11-07
> **coffeecat said:**
> The best tool for the job is Gparted. The reason the partition sizes don't correspond may be that Gparted is reporting in Gibibytes, and the file manager (possibly) in Gigabytes. 

1 gibibyte = 1073741824bytes

1 gigabyte = 1000000000bytes

But I'm concerned that Gparted is not showing one of the partitions - or so I understand from your post.

The best thing would be to open Gparted again and post screenshots of the Gparted window for both sda and sdb.


Hopefully, the screenshots are attached.

---

### Post by coffeecat on 2009-11-07
Several comments, not necessarily in any order.

If you look at the Gparted screenshots, you'll see that both the Windows partitions (sda1 and sdb1) have exclamation icons next to them, and they're showing nothing under 'used' and 'unused'. This suggests that Gparted has picked up a filesystem problem in both of them. Can you mount and view the Windows partitions from Ubuntu? Can you boot into either or both of the Windows partitions?

Next thing, re-reading your first post again, it sounds as though you want Ubuntu to take up the whole of your SATA drive and you want to use the whole of your IDE drive for storage. Which means that you want to get rid of Windows entirely. Am I correct?

If I am, and you were hoping to enlarge your Ubuntu root partition to take over the space formerly occupied by the Windows NTFS partition, I have bad news for you. Your Ubuntu root partition is in a logical partition (sdb5) which is contained in the extended partition sdb2. Which would mean you would have to remove sdb1, enlarge sdb2 backwards and then enlarge sdb5 backwards. I may be wrong, but I'm fairly sure this is impossible. Which would mean that you would need to do a fresh install, or image your root partition, reformat the drive and restore the image back to the new partition. After which you would have to do some serious reconfiguration of grub and editing of /etc/fstab. A fresh install might be easier.

Third thing: from the information you've given it would certainly seem that sdb is the SATA drive. It's certainly the one with Ubuntu on it. (Both your drives are 232.88 GiB = 250GB in size.) If you have set the BIOS to boot from the SATA, the simple way to answer your original question is to disconnect the ide and boot up. That way, sdb will probably become sda, but you can check everything with Gparted again and that will prove which disc is which.

---

### Post by michy99 on 2009-11-07
> **coffeecat said:**
> Which would mean you would have to remove sdb1, enlarge sdb2 backwards and then enlarge sdb5 backwards. I may be wrong, but I'm fairly sure this is impossible.

Not at all impossible, although it might take a while, as the whole partition will have to be copied to the new location.

---

### Post by coffeecat on 2009-11-07
> **michy99 said:**
> Not at all impossible, although it might take a while, as the whole partition will have to be copied to the new location.

Thanks for the clarification. But just out of curiosity - I doubt I'll ever need to do this :wink: - what would happen to the partition numbering. If the OP removed partition #1, and enlarged extended #2 to fill the space, would they end up with just one massive 250GB extended partition (containing logicals, obviously), but numbered #2?

---

### Post by michy99 on 2009-11-07
Yep. I removed sda2 on my system, and sda3 and above retained the same numbers they had. Of course, it's better to use the UUID in fstab anyways.

---

### Post by distortedecho on 2009-11-08
Wait.... you've lost me... Can I or can't I achieve what I'm trying to achieve?

What steps do I need to follow?

Thanks for your help so far...

---

### Post by coffeecat on 2009-11-08
> **coffeecat said:**
> Next thing, re-reading your first post again, it sounds as though you want Ubuntu to take up the whole of your SATA drive and you want to use the whole of your IDE drive for storage. Which means that you want to get rid of Windows entirely. Am I correct?

> **distortedecho said:**
> Can I or can't I achieve what I'm trying to achieve?

Yes you can achieve what you are trying to achieve. The trouble is, you haven't clarified exactly what it is you want to achieve.

---

### Post by distortedecho on 2009-11-08
Haha, on the contrary - I want my IDE drive (which I'm hoping is my Storage partion) to be extended to be solely Storage.

I want my Sata drive (which I'm hoping is my Ubuntu partition) to be extended to be solely Ubuntu.

---

### Post by distortedecho on 2009-11-10
uppin for coffeecat

---

### Post by distortedecho on 2009-12-05
Latest progress:

Used Partition Magic on the IDE drive to Remove XP Partition.
Again on SATA Drive.

This obviously screwed up Grub, so I've used Partition Editor from the Live CD to get the attached.

How can I get rid of sdb5?????????

How do I now make sure Linux boots?

---

### Post by Sin@Sin-Sacrifice on 2009-12-05
To get rid of sdb5 you just need to delete it by right clicking and hitting delete. Then you can resize another partition to "consume" it. You're gonna need to install grub on the partition with /boot with [this tutorial]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by distortedecho on 2009-12-07
Hi, I've got GRUB installed, and the machine is booting fine. I think I did everything OK.

But, when I try to delete sdb5, it tells me I have to unmount all drives of a higher number??

When I re-installed grub, I also had to do the (hd1, 4) bit, but when it boots it tells me (hd0, 5). It still boots but I think I may have made an error somewhere?

Any ideas?

---

### Post by distortedecho on 2009-12-11
Guys, did I do this right?

---

