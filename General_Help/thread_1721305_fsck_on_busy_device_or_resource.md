---
title: "fsck on busy device or resource"
date: 2011-04-04
forum: General Help
---

### Post by DanceLink on 2011-04-04
Hello Ubuntu Forums world! :)
 
This is officially my first post here, so first I'll say hello... wait, I just did. >.<
 
Ok, onto the topic I'm sure many Ubuntu-ers have encountered trouble with. I am dual-booting my Gateway laptop with Windows XP Media center Ed. and Ubuntu Notebook 10.10. Several weeks ago I was in the midst of downloading a program from the software center and my system starts running slow (this is in the Ubuntu kernel, not the Windows OS). So I decided to cold-boot the laptop in mid-download. When it boots back up, I get dropped to a grub-rescue menu that states the following:
 
```
error: hd0,msdos5 out of disk.
grub rescue> 
```
 
Now, the only way I can even remotely use my laptop at the moment is to use my Live USB with the corresponding version of Ubuntu Netbook 10.10 or the Live CD I made with Ubuntu 10.04 on it (I'll explain why I made this below).
 
I read somewhere that I need to run fsck on my device to try to fix the partition, which btw my Ubuntu partition on my device is /dev/sda5, and before someone suggests it, I even tried using GParted and it doesn't work. 
 
The reason I made a 10.04 CD is because I read somewhere that using the fsck from 10.04 might be more effective (for whatever reason) than the 10.10 fsck version.
 
I'd also like to add that I'm incapable of booting onto my Windows OS at all, yet I can access the partition from my Live CD/USB. the Ubuntu partition however, I can neither access or mount.
 
I tried running fsck on the entire device partition table, and I get the following:
 
```
ubuntu@ubuntu:~$ sudo fsck /dev/sda
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Device or resource busy wile trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ 
```
 
This is me running fsck from the 10.04 version, I get a similar msg from the 10.10 Live USB but replace fsck.ext2 with fsck.ext4 in the message.
 
I need help, I'm new at linux (still learning Introduction to Unix actually), and I need that partition back up and running! Most of, if not all of, my current school-related files are on that partition.
 
Please help!
 
Regards,
 
~*DanceLink*

---

### Post by FuturePilot on 2011-04-04
Try
```
sudo fsck /dev/sda5
```
from the live USB.

You can't fsck an entire disk at once.

---

### Post by oldfred on 2011-04-04
Since it is sda5, it is also in the extended partition. Right click on the swap and choose swapoff in gparted.

 LIveCDs usually mount the swap partition to speed things up, but that in effect mounts the extended partition which prevents any work on any partitions in the extended. 

A few have still had problems and found that downloading another distribution like Slitaz and running e2fsck from there worked. 

From liveCD so everything is unmounted,swap off if necessary, change sda5 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda5
if errors:
sudo e2fsck -f -y -v /dev/sda5

Try this, is sure swapoff completed:
root@ubuntu# fuser -vam /dev/sda5
root@ubuntu# lsof /dev/sda5
Terminate with "kill [pid]" or "kill -9 [pid]
If not:
Problem running e2fsck apparently in use by the system,  Use Slitaz
[http://ubuntuforums.org/showthread.php?t=1713946](http://ubuntuforums.org/showthread.php?t=1713946)
SATA will use sda1 and IDE devices use hda1 in Slitaz

---

### Post by DanceLink on 2011-04-04
@FuturePilot: Thanks, but I actually started out with that before researching for further help, same set of messages. :)
 
@oldfred: Thanks, I'll try that. I'm trying to disable the swap partition (/dev/sda6) but GParted is taking its dear sweet time doing so. The progress bar just bounces back and forth, I'll leave it for another 5 minutes and see where that gets me. Failing that, I may just start off with your suggestion:
 
[QUOTE=oldfred]sudo e2fsck -C0 -p -f -v /dev/sda5
if errors:
sudo e2fsck -f -y -v /dev/sda5
[/QUOTE]
 
without swapoff completing. :(
 
I'll let you all know how that goes. :)

---

### Post by DanceLink on 2011-04-04
Hey, so progress. Swapoff completed (yay), and trying to kill the process but I get the following messages:
 
```
ubuntu@ubuntu:~$ sudo lsof /dev/sda5
lsof: WARNING: can't stat() tmpfs file system /cow
       Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ubuntu/.gvfs
       Output information may be incomplete.
ubuntu@ubuntu:~$ 
```
 
What do I do next? What's the process(es) I need to kill?
 
:)

---

### Post by oldfred on 2011-04-04
I would download and run Slitaz, like the one I linked to. As a last resort.

---

### Post by DanceLink on 2011-04-06
@oldfred: I tried SliTaz 3.0 Stable's iso and ran e2fsck -f -y -v /dev/sda5, and it ran through 10 minutes' worth of scripting with error checks, and fixes. But then after that time, my screen went black. After waiting 2 minutes, I decided to try to boot up my laptop normally (no rescue CD's/USB's). grub rescue now displays the following message:
 
```
error: file not found
grub rescue> 
```
 
What do I do?

---

### Post by oldfred on 2011-04-06
I do not know if 2 minutes was enough to wait, if it was posting errors. I have not use Slitaz so I do not know if it was just the screensaver kicking in.

Lots of info here:
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)
[https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode)

Express Boot to the Most Recent Kernel
 Command Summary ls to see drive X & partition Y (hdX,Y) or sdXY:
      ls
      set root=(hdX,Y)
      linux /vmlinuz root=/dev/sdXY ro
      initrd /initrd
      boot

If your install is sda5 replace X with a and Y with 5.

---

### Post by DanceLink on 2011-04-12
Sorry for the late reply, but it doesn't recognize the linux command in grub rescue. 
 
Here's the code with output from my laptop's grub rescue screen:
 
```
error: file not found
grub rescue> ls
(hd0) (hd0,msdos6) (hd0,msdos5) (hd0,msdos2) (hd0,msdos1) (fd0) (fd1) 
grub rescue> set root=(hd0,5)
grub rescue> linux /vmlinuz root=/dev/sda5 ro
Unknown command 'linux'
grub rescue> 
```
 
The good news is now that the partition's fs is clean, I can access it remotely through a rescue USB/CD, but I need to be able to boot up my laptop.
 
What's my next step?
 
:D

---

### Post by oldfred on 2011-04-12
You may have to run full chroot into your install and reinstall grub2 and update system. But lets confirm what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by DanceLink on 2011-04-13
Here ya go!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

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

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   244,196,063   244,196,001   7 HPFS/NTFS
/dev/sda2         244,196,064   292,966,086    48,770,023   c W95 FAT32 (LBA)
/dev/sda3         292,966,398   488,396,799   195,430,402   5 Extended
/dev/sda5         292,966,400   480,358,399   187,392,000  83 Linux
/dev/sda6         480,360,448   488,396,799     8,036,352  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.0 GB, 16047407104 bytes
94 heads, 30 sectors/track, 11114 cylinders, total 31342592 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064    31,342,591    31,334,528   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A844152B1887E334                       ntfs       Sonic's Hard Drive            
/dev/sda2        641A-8B7D                              vfat       SONIC'S NUL                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        052e2b4f-3629-4a5f-906c-2084917cbd4f   ext4                                     
/dev/sda6        9f1a8c6b-5487-48d6-9a7c-376d80db2b41   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7E2D-AD06                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=052e2b4f-3629-4a5f-906c-2084917cbd4f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9f1a8c6b-5487-48d6-9a7c-376d80db2b41 none            swap    sw              0       0
/dev/sda2 /mnt/win vfat user,noauto,quiet,umask=0 0 0

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  19 15 99 00 b9 89 ca 0a  a1 ac 11 8a 36 32 fa 9f  |............62..|
00000010  1a 3d 83 ac 89 b9 2a 14  ba 99 dc a9 bf 89 99 99  |.=....*.........|
00000020  88 73 33 11 53 93 bc 98  0a 26 a9 20 b1 cf 41 13  |.s3.S....&. ..A.|
00000030  98 10 e0 bf 98 da aa 18  81 2b 35 b8 9b 63 81 72  |.........+5..c.r|
00000040  04 10 02 a8 aa 0a 22 33  41 37 b8 be aa 08 81 0a  |......"3A7......|
00000050  37 02 da 0a ff bb c9 ac  bb 18 b0 9e 42 81 33 c1  |7...........B.3.|
00000060  0b 12 73 24 11 ba b8 8e  22 21 32 54 a3 ef 08 80  |..s$...."!2T....|
00000070  08 08 88 10 22 90 e7 bd  11 42 a2 9c 90 9b a0 ef  |...."....B......|
00000080  89 08 25 91 18 91 ac 22  b8 8b 73 12 10 32 46 02  |..%...."..s..2F.|
00000090  89 a9 18 ea ae 40 82 99  f6 39 ba 1a 46 a1 ac 10  |.....@...9..F...|
000000a0  f8 ad 19 10 88 42 33 80  cb 11 c9 1a 45 90 1a 44  |.....B3.....E..D|
000000b0  23 81 18 a0 08 20 17 dc  8a 11 f3 3f 89 09 12 fb  |#.... .....?....|
000000c0  89 80 39 23 00 19 77 12  01 a9 09 a8 9c 61 13 89  |..9#..w......a..|
000000d0  99 29 34 d9 0a 92 cf 31  03 ba ab da 00 3c a8 aa  |.)4....1.....<..|
000000e0  28 fc 0c 01 a8 9b 11 89  66 12 21 11 32 91 29 91  |(.......f.!.2.).|
000000f0  3a 77 80 88 00 88 02 dc  89 88 88 c9 9a ec ec 3d  |:w.............=|
00000100  ac 3b 67 10 13 10 fb 8f  80 08 18 80 08 81 b9 09  |.;g.............|
00000110  10 12 81 6a b6 2e a2 71  82 09 12 90 1d 83 89 10  |...j...q........|
00000120  f5 40 89 99 2c 67 18 11  00 a0 ff 88 00 10 98 08  |.@..,g..........|
00000130  09 88 01 00 80 da 70 c1  2a a1 4b 27 8a 14 99 00  |......p.*.K'....|
00000140  a8 08 3f c5 00 13 98 18  90 10 22 a0 9c 00 72 45  |..?......."...rE|
00000150  01 00 00 00 00 ae bc 48  b2 1a fc ef 10 00 a8 89  |.......H........|
00000160  00 22 a0 88 fd c5 21 04  29 05 89 53 11 01 da 8b  |."....!.)..S....|
00000170  98 53 a8 8a 54 b2 0a 99  25 a9 19 c1 9b 34 bc e9  |.S..T...%....4..|
00000180  8c a8 51 d8 40 d1 f7 42  b9 59 15 08 01 ab 1a 82  |..Q.@..B.Y......|
00000190  0b 06 51 11 63 13 aa 28  12 18 22 ba a9 20 bb 77  |..Q.c..(..".. .w|
000001a0  23 00 ac b9 cd ac 18 01  01 4e 0b 22 08 21 a0 9b  |#........N.".!..|
000001b0  01 ac 00 48 85 29 33 f9  38 a3 08 80 62 b0 00 fe  |...H.)3.8...b...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 60 2b 0b 00 fe  |...........`+...|
000001d0  ff ff 05 fe ff ff 8f 64  2b 0b 73 a3 7a 00 00 00  |.......d+.s.z...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 30 00  |.X.SYSLINUX..@0.|
00000010  02 00 00 00 00 f8 00 00  3f 00 80 00 80 1f 00 00  |........?.......|
00000020  80 20 de 01 f8 0e 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 08 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 06 ad 2d 7e 4b  49 4e 47 53 54 4f 4e 20  |..)..-~KINGSTON |
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
00000100  7d 00 66 b8 e0 48 00 00  66 ba 00 00 00 00 bb 00  |}.f..H..f.......|
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

### Post by oldfred on 2011-04-13
Your sda5 seems to have fstab and nothing else, no grub, no kernels or as if the /boot folder was deleted.

You may be able to chroot into your system & reinstall grub & update to get new kernel, but I do not know if then other folders are missing. If so then a reinstall would be required any way. 

One line version of chroot (uses && to combine)
kansasnoob's change sda5 to correct partition:
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop
# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

reinstall kernel:
sudo apt-get update
sudo apt-get install linux-image
sudo update-grub

sudo dpkg-reconfigure grub-pc

---

### Post by DanceLink on 2011-04-14
Hey oldfred, I'm running the commands you posted in your latest reply, but I keep getting errors on some of them. 
 
For instance, the one-line code you posted:
 
```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

```
 
I ended up getting some sort of input/output error.
 
Then I ignored that and proceeded with the rest of the code until:
 
```
apt-get upgrade
```
 
After I ran that, I got this after it was all done:
 
```
Preconfiguring packages ...
dpkg-deb (subprocess): failed to exec tar: Input/output error
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/dpkg_1.15.8.4ubuntu3.1.i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu: /home/ubuntu# 
```
 
After that I tried:
 
```
root@ubuntu: /home/ubuntu# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 306 not upgraded.
root@ubuntu: /home/ubuntu# dpkg --configure -a
root@ubuntu: /home/ubuntu# 
```
 
That's where I stopped. I wasn't sure whether or not to continue with the preceeding errors I got as posted herein. Any advice or ideas, or should I just continue with the operation (codes posted by you)?
 
:D

---

### Post by oldfred on 2011-04-14
If you get an error on first command, I am not sure any of the rest matter. Instead of on long command joined with && run each command separately.

drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)
sudo -i
mount /dev/sda5 /mnt
mount --bind /dev  /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys  /mnt/sys
mount --bind /usr/ /mnt/usr
chroot /mnt
apt-get update
apt-get upgrade
#would upgrade you to the latest kernel in the repositories
apt-get dist-upgrade

Then we may be able to see what is the problem. But you are missing key system files, it will probably be easier just to reinstall.

---

### Post by DanceLink on 2011-04-21
I found the error:
 
```
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mount /dev/sda5 /mnt
root@ubuntu:~# mount --bind /dev /mnt/dev
root@ubuntu:~# mount --bind /proc /mnt/proc
root@ubuntu:~# mount --bind /sys /mnt/sys
root@ubuntu:~# mount --bind /usr /mnt/usr
root@ubuntu:~# chroot /mnt
/bin/bash: error while loading shared libraries: libncurses.so.5: cannot open shared object file: Input/output error
root@ubuntu:~# 

```
 
What's my next step, or am I looking at re-formatting that partition at this point?
 
P.S. Sorry again for delayed reply. ^^;

---

### Post by dino99 on 2011-04-21
its the way you learn but its faster to make a clean install over yours: you only have to reformat the / partition if you still have this kind of install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by oldfred on 2011-04-21
I have to agree with dino99, that it may be time to reinstall.

But I think I left out a command that some say is optional and there are two others that only seem to apply with certain versions. If you want to try add these just before the chroot command. 

cp /etc/resolv.conf /mnt/etc/resolv.conf

# new for lucid & karmic 
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

---

### Post by DanceLink on 2011-04-26
Well I tried the cp line you posted oldfred, but after the chroot, I got an I/O error from bin, so to make a long story short, I zipped all the files I had on that partition onto an old USB key, deleted the sda5 ubuntu and sda6 swap partitions as well as the sda4 extended logical unit, and manually re-installed ubuntu in sda5 with a 4 GB sda6 swap partition. sda5 being formatted with ext4. Basically my laptop runs fine now, and I still have the data I wanted to recover on a USB Key, which I'll reload into my computer later on tonight probably. 

Thanks for all the help btw, I gotta say, until you started posting in the thread, I wouldn't have been able to figure this one out. Thanks!

~DanceLink

---

