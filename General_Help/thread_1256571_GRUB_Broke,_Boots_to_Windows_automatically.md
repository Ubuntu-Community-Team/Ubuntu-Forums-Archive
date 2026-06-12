---
title: "GRUB Broke, Boots to Windows automatically"
date: 2009-09-02
forum: General Help
---

### Post by domokunrox on 2009-09-02
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x21432143

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   976768064   488384001    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b9b3b9b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63       16064        8001    7  HPFS/NTFS
/dev/sdb2           16065   390652604   195318270   83  Linux
/dev/sdb3       390652605   488392064    48869730    5  Extended
/dev/sdb5       390652668   391150619      248976   82  Linux swap / Solaris

```

Here is the boot info script
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x21432143

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b9b3b9b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63        16,064        16,002   7 HPFS/NTFS
/dev/sdb2              16,065   390,652,604   390,636,540  83 Linux
/dev/sdb3         390,652,605   488,392,064    97,739,460   5 Extended
/dev/sdb5         390,652,668   391,150,619       497,952  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="ACC81CE9C81CB394" TYPE="ntfs" 
/dev/sdb1: UUID="568C126A8C124541" TYPE="ntfs" 
/dev/sdb2: UUID="31e43d63-289c-473e-b451-29de4aa0a3e2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="431c180c-a1ea-42b6-afb7-4e094fa290b7" TYPE="swap" 

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


================================ sda1/boot.ini: ================================



C:\ubnldr.mbr="Auto Super Grub Disk"


================================ sdb1/boot.ini: ================================

[boot loader]

;timeout=1

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS



[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

;

[spybotsd]

timeout.old=1




=========================== sdb2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=31e43d63-289c-473e-b451-29de4aa0a3e2

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, memtest86+
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
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
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 176.5GB: boot/grub/menu.lst
 176.5GB: boot/grub/stage2
 176.5GB: boot/initrd.img-2.6.27-11-generic
 176.6GB: boot/initrd.img-2.6.28-11-generic
 176.5GB: boot/initrd.img-2.6.28-13-generic
 176.5GB: boot/initrd.img-2.6.28-14-generic
 176.6GB: boot/initrd.img-2.6.28-15-generic
 176.5GB: boot/vmlinuz-2.6.27-11-generic
 176.5GB: boot/vmlinuz-2.6.28-11-generic
 176.5GB: boot/vmlinuz-2.6.28-13-generic
 176.5GB: boot/vmlinuz-2.6.28-14-generic
 176.6GB: boot/vmlinuz-2.6.28-15-generic
 176.6GB: initrd.img
 176.5GB: initrd.img.old
 176.6GB: vmlinuz
 176.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d7 50 88 46  |......u..1.F.P.F|
00000080  d4 be 6a 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..j....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fa cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fa e9 c7 47 fb 94  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 72  ||U........R....r|
00000130  33 33 db 8a de 8b 46 0a  33 d2 83 e1 3f f7 f1 91  |33....F.3...?...|
00000140  97 8b 46 08 f7 f7 42 87  ca 3b da 72 17 43 f7 f3  |..F...B..;.r.C..|
00000150  8a f2 86 c5 d1 e8 d1 e8  0a c8 d0 cc d0 cc 0a f4  |................|
00000160  84 e4 74 02 b4 41 5b 8a  d3 c3 0d 0a 4d 42 52 20  |..t..A[.....MBR |
00000170  45 72 72 6f 72 20 00 0d  0a 00 72 65 73 73 20 61  |Error ....ress a|
00000180  6e 79 20 6b 65 79 20 74  6f 20 62 6f 6f 74 20 66  |ny key to boot f|
00000190  72 6f 6d 20 66 6c 6f 70  70 79 2e 2e 2e 00 00 00  |rom floppy......|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 f2 0e 00  9b 3b 9b 3b 08 7b 80 01  |.........;.;.{..|
000001c0  01 00 07 fe 3f 00 3f 00  00 00 82 3e 00 00 00 00  |....?.?....>....|
000001d0  01 01 83 fe ff ff c1 3e  00 00 fc a3 48 17 00 fe  |.......>....H...|
000001e0  ff ff 05 fe ff ff bd e2  48 17 c4 62 d3 05 00 00  |........H..b....|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Please help. Windows is the only thing that boots up, and the Seagate drive is getting more and more frequent STOP errors because its going to go soon. Thanks.

---

### Post by blueridgedog on 2009-09-02
Your info states:

>  => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.


However, I don't see a partition #6 on sdb2.

On sdb2, partition 2 looks like a potential candidate for your Linux install.  Can you boot on the LiveCD determine if your Linux install is on sdb2?  

You can mount it with:

```
sudo mkdir /mnt/sdb2
sudo mount /dev/sdb2 /mnt/sdb2
```

Once mounted you can access the files.  If it is your linux install then perhaps Grub is pointing to the wrong partition or your Ubuntu partition has disappeared.

If you think sdb2 is your install, you can try and correct grub.  The standard way to re-install grub is:

Bootup a live cd, open a terminal and do the following.
```

sudo grub
```

This will result in a "grub>" prompt. At grub>. enter these commands
```

find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to use as the source for the new mbr.  If your boot files are in /dev/sdb2, then it will call it hd1,1 (second hard drive, second primary partition).

Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd1,1) then you would enter root (hd1,1)

Next enter the command to install grub to the mbr

```
setup (hd0)
```

Note, if you wanted to put the new mbr in another hard drive, you could adjust it accordingly.

Finally exit the grub shell
```

quit
```

---

### Post by domokunrox on 2009-09-02
I tried to clean that up before I made a boot info script.

I resized my Ubuntu partition to 200GB and left 50GB to install a swap space and a ~50GB NEW Ubuntu partition to see if it would install GRUB cleanly and give me a menu.

However, it still is stuck in booting straight to windows, so I poped my live CD in and tried to delete those partitions in the partition editor but they got the little key chain on the side there, so I couldn't remove them and resize my partition to cover it again. 

Here I am in a LIVE CD session with a firefox and terminal open.

The partition I have in question and the one I want working again the the ~200GB one. Its an up to date Ubuntu with the latest kernel. 

I have this feeling that Windows fudged the MBR. Am I correct in this assumption?

---

### Post by blueridgedog on 2009-09-02
You can't resize them because they are probably mounted and the LiveCD will use the swap partition.  If you think it is your Ubuntu install, then the re-installation of grub should work.

You can turn off the use of the swap partition with:

sudo swapoff -a

---

### Post by domokunrox on 2009-09-02
Well, I did do this

```
Sudo Grub
find /boot/grub/stage1
hd(1,1)
root (1,1)
setup (hd0)
```

It did what it was supposed to do, but I restarted the computer and it still boots to windows XP.

Perhaps a closer look into the boot info script reveals more?

EDIT: Btw, when it restarted straight to windows XP, it was trying to do a CHKDSK. I stoped it however, I didn't want to fudge more stuff.

Can I entertain a thought here? sdb1 is a 8meg ntfs partition. Now, would it be so far fetched that Windows has a mind of its own and Grub exisited there, but decided to format the partition and screwing me over?

---

### Post by domokunrox on 2009-09-02
UPDATE: I resized those partitions with the editor. It now looks like this

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x21432143

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   976768064   488384001    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b9b3b9b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63       16064        8001    7  HPFS/NTFS
/dev/sdb2           16065   488392064   244188000   83  Linux

```

Here is what happened when I installed grub in case you wanted to see it. Sent it to myself in e-mail
```
grub> find /boot/grub/stage1
 (hd1,1)

grub> root (hd1,1)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+16 p (hd1,1)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

```

EDIT: 

New information here. I check my menu.lst like so....
```
gedit /boot/grub/menu.lst
```

and I get a blank menu.lst

---

### Post by blueridgedog on 2009-09-02
> **domokunrox said:**
> 
Can I entertain a thought here? sdb1 is a 8meg ntfs partition. Now, would it be so far fetched that Windows has a mind of its own and Grub exisited there, but decided to format the partition and screwing me over?

What drive is your bios set to boot off of?  It may be that your PC is booting off of the other drive, and putting grub into hd0 has no effect.

---

### Post by domokunrox on 2009-09-02
Its set to boot priority with the 250GB drive just behind CD ROM booting. I just restarted and checked it in the BIOS.

---

### Post by domokunrox on 2009-09-02
> **blueridgedog said:**
> What drive is your bios set to boot off of?  It may be that your PC is booting off of the other drive, and putting grub into hd0 has no effect.

Should I put Grub into hd1?

EDIT:
I gave it a shot, it did do something
```
grub> find /boot/grub/stage1
 (hd1,1)

grub> root (hd1,1)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

```

---

### Post by domokunrox on 2009-09-02
Well, I decided to install grub to setup (hd1) and guess what? It worked.

Note to self and everyone else: using an Older LIVE CD doesn't work.

One last question

I have a bunch of kernels on my grub boot list. Anyone who can give me tips to clean it up?

Here is my menu.lst
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
# kopt=root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=31e43d63-289c-473e-b451-29de4aa0a3e2

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, memtest86+
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
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
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by blueridgedog on 2009-09-03
> **domokunrox said:**
> Well, I decided to install grub to setup (hd1) and guess what? It worked.

...

I have a bunch of kernels on my grub boot list. Anyone who can give me tips to clean it up?


For some reason, you bios must be booting off of hd1.  Either way, I am glad you solved the issue.  As to the kernels, you could comment out the entries, or remove the kernels with apt-get, but I recommend you keep them as they are a failsafe against kernel problems.  The OS will keep a certain number so you back out of a bad update.

---

