---
title: "Help, my boot loader is FUBAR"
date: 2010-12-06
forum: General Help
---

### Post by JPBodner on 2010-12-06
Hi all.  I've got a dual boot Ubuntu/XP system (two separate HDs) that I've really hosed up and I'm hoping someone here can help.  Here's the sad tale:

1.  When rebooting recently, the bios prompted me to confirm a change to my system configuration... the query you get when you add a new HD, for example.  I didn't add anything to the system, but stupidly hit F1 to apply the changes in my haste.  

2. I could then boot into Ubuntu, but not Windows.  When I tried the latter, I got the "NTLDR is missing" message.  

3. Based on reading some online help tips, I booted into the recovery console and tried fixboot. 

4.  Now, I can't boot into either system!  I get something like this when I choose Ubuntu from the Grub menu:

"gave up waiting for root device
ALERT dropping to a shell
BusyBox built in shell
<initramfs>  
" 

I am paraphrasing above.  I hope you'll recognize that screen.  

So, I think both installations are ok, but I've hosed up the boot loader pretty well.  Can anyone point me in the right direction?  Since I don
't have much experience in this part of the system, please be explicit with any ideas.  Many, many thanks in advance!

---

### Post by oldfred on 2010-12-06
Run this so we can see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by JPBodner on 2010-12-06
Thanks Old Fred.  I booted via a live cd and got these results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Fat16
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x035b8b84

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   470,142,224   470,142,162  83 Linux
/dev/sda2         470,142,225   488,392,064    18,249,840   5 Extended
/dev/sda5         470,142,288   488,392,064    18,249,777  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6999f4ed

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   312,576,704   312,576,642   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4016 MB, 4016045568 bytes
255 heads, 63 sectors/track, 488 cylinders, total 7843839 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        dfbe62d6-556e-456d-ae01-4101d4ff74d1   ext3                                     
/dev/sda5        6bf77a56-dee7-4a3a-ae4c-6469648598f1   swap                                     
/dev/sdb1        55D123D9E79ABF54                       ntfs       OneTouch4 Mini                
/dev/sdc1        18A7-3197                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /media/disk              vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdb1        /media/OneTouch4 Mini    fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d5 50 88 46  |......u..1.F.P.F|
00000080  d2 be 68 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..h....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fc cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fc e9 c7 47 fd 92  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 33  ||U........R....3|
00000130  db 8a de 8b 46 0a 33 d2  83 e1 3f f7 f1 91 97 8b  |....F.3...?.....|
00000140  46 08 f7 f7 42 87 ca 3b  da 72 17 43 f7 f3 8a f2  |F...B..;.r.C....|
00000150  86 c5 d1 e8 d1 e8 0a c8  d0 cc d0 cc 0a f4 84 e4  |................|
00000160  74 02 b4 41 5b 8a d3 c3  0d 0a 4d 42 52 20 45 72  |t..A[.....MBR Er|
00000170  72 6f 72 20 00 0d 0a 00  72 65 73 73 20 61 6e 79  |ror ....ress any|
00000180  20 6b 65 79 20 74 6f 20  62 6f 6f 74 20 66 72 6f  | key to boot fro|
00000190  6d 20 66 6c 6f 70 70 79  2e 2e 2e 00 00 00 00 00  |m floppy........|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 00 00 00  ed f4 99 69 00 00 80 01  |...........i....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 82 8a a1 12 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2010-12-06
You show no windows bootable partition and the grub in the MBR of sda is pointing to sda1, but in one place it says it is FAT and another ext3.

I would first use testdisk to see if it can fix your sda1 partition. What partition was windows in? Or was this a wubi install, I do see a separate swap, so I assume you have a full Ubuntu install in sda1. But the NTFS sdb1 shows no boot files. Sometimes boot files are moved to another windows partition if you have more than one install of windows.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

You may be able to repair with fsck:
From liveCD so everything is unmounted, change sda1 to your partition(s) if needed:
sudo e2fsck -C0 -p -f -v /dev/sda1
if errors:
sudo e2fsck -f -y -v /dev/sda1

Not sure about your windows.

---

### Post by JPBodner on 2010-12-07
Hi again.

I tried both methods to no avail.  You're right that the windows disk is not showing up anywhere.  The linux disk is found by testdisk and it tells me it's "ok", but I still can't from it.  I get the grub selection menu, but when I select Ubuntu, it eventually ends up in that emergency shell prompt.  

Any other ideas????

---

### Post by oldfred on 2010-12-07
Until you get sda1 fixed, it will not boot. Did you run the fsck on sda1? 

Did you look in:
syslog - try
       dmesg | tail  or so

---

### Post by JPBodner on 2010-12-08
I tried the e2fsck commands as you suggested. No luck there. 

Sorry, I don't know what the syslog -try thing means.  I am booted into Linux via a livedisk and I see a syslog choice under admin, but I'm not sure exactly what you mean. Or is this a terminal command?

My bios isn't seeing the windows drive at all when I boot to the HP bios setup screen, so this is my theory for what has happened:
1. My windows drive failed, and is not being recognized by the machine. 
2. I booted into the windows recovery console, and used fixboot, but stupidly choose the Linux drive since that was the only thing listed.
3. That screwed up the boot on the Linux drive.  Haven't been able to recover it. 

I still believe the Linux partition is salvagable.  One other note: when I boot to the live disk, the Linux drive shows up in the file browser.  But when I click on it, three files are shown with ascii garbage as their titles. No file structure is seen. 

Thanks again for your patience and help!!

---

### Post by oldfred on 2010-12-08
We normally run this to fix where someone has installed grub to a windows boot sector. It recovers the backup boot sector. Should work as you just want the only one back.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Testdisk also has a function to rebuild a boot sector for NTFS do not know it it does anything else.

---

### Post by JPBodner on 2010-12-08
Hi again

Some progress here.  I unplugged and re-plugged the windows drive, which is now back to normal. It must have been some physical connection issue. Not sure how that happened, but I guess it did.

So, that drive is fine and I can boot to it. Now I just have to get the more important disk (Linux!) back from the dead.  No progress there yet. 

JP

---

### Post by JPBodner on 2010-12-08
Here's my updated output from that bash script.  

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Testdisk is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Fat16
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   470,142,224   470,142,162  83 Linux
/dev/sda2         470,142,225   488,392,064    18,249,840   f W95 Ext d (LBA)
/dev/sda5         470,142,288   488,392,064    18,249,777  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xde95de95

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   312,560,639   312,560,577   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4016 MB, 4016045568 bytes
255 heads, 63 sectors/track, 488 cylinders, total 7843839 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2e512e50

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        dfbe62d6-556e-456d-ae01-4101d4ff74d1   ext3                                     
/dev/sda5        6bf77a56-dee7-4a3a-ae4c-6469648598f1   swap                                     
/dev/sdb1        4A1CCA271CCA0DBF                       ntfs                                     
/dev/sdc1        18A7-3197                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /media/disk              vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=dfbe62d6-556e-456d-ae01-4101d4ff74d1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 10.10, kernel 2.6.35-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=dfbe62d6-556e-456d-ae01-4101d4ff74d1 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=dfbe62d6-556e-456d-ae01-4101d4ff74d1 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=dfbe62d6-556e-456d-ae01-4101d4ff74d1 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=dfbe62d6-556e-456d-ae01-4101d4ff74d1 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.32-25-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=dfbe62d6-556e-456d-ae01-4101d4ff74d1 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 10.10, kernel 2.6.32-25-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=dfbe62d6-556e-456d-ae01-4101d4ff74d1 ro  single
initrd		/boot/initrd.img-2.6.32-25-generic

title		Ubuntu 10.10, kernel 2.6.31-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=dfbe62d6-556e-456d-ae01-4101d4ff74d1 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 10.10, kernel 2.6.31-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=dfbe62d6-556e-456d-ae01-4101d4ff74d1 ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 10.10, kernel 2.6.28-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=dfbe62d6-556e-456d-ae01-4101d4ff74d1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic
quiet

title		Ubuntu 10.10, kernel 2.6.28-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=dfbe62d6-556e-456d-ae01-4101d4ff74d1 ro  single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 10.10, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=dfbe62d6-556e-456d-ae01-4101d4ff74d1 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 10.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=dfbe62d6-556e-456d-ae01-4101d4ff74d1 ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 10.10, memtest86+
root		(hd0,0)
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


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=dfbe62d6-556e-456d-ae01-4101d4ff74d1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6bf77a56-dee7-4a3a-ae4c-6469648598f1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 190.7GB: boot/grub/menu.lst
 190.7GB: boot/grub/stage2
 190.7GB: boot/initrd.img-2.6.24-21-generic
 190.8GB: boot/initrd.img-2.6.24-21-generic.bak
 190.8GB: boot/initrd.img-2.6.28-18-generic
 190.7GB: boot/initrd.img-2.6.31-21-generic
 190.8GB: boot/initrd.img-2.6.32-25-generic
 190.7GB: boot/initrd.img-2.6.35-22-generic
 190.8GB: boot/initrd.img-2.6.35-23-generic
 190.8GB: boot/vmlinuz-2.6.24-21-generic
 190.8GB: boot/vmlinuz-2.6.28-18-generic
 190.8GB: boot/vmlinuz-2.6.31-21-generic
 190.8GB: boot/vmlinuz-2.6.32-25-generic
 190.7GB: boot/vmlinuz-2.6.35-22-generic
 190.8GB: boot/vmlinuz-2.6.35-23-generic
 190.8GB: initrd.img
 190.7GB: initrd.img.old
 190.8GB: vmlinuz
 190.7GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

```

---

### Post by oldfred on 2010-12-08
I see you have a windows boot loader in the MBR of sdb. I have seen testdisk reported in the MBR before but know nothing about it. I think you need to replace test disk with grub.

Since you had old grub legacy it may be best just to reinstall that.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

[https://help.ubuntu.com/community/DualBoot/Grub#Ubuntu%209.10%20&%20earlier]("https://help.ubuntu.com/community/DualBoot/Grub#Ubuntu%209.10%20&%20earlier")
#reset grub boot from terminal in LiveCD:
sudo grub
find /boot/grub/stage1 #you will get a response such as  (hd0,5) if sda6
root (hdx,y) #use the numbers from the previous command x is drive, y is partition  or root (hd0,0) if sda1
setup (hd0)
quit

---

### Post by JPBodner on 2010-12-08
when I do: find /boot/grub/stage1
I get: Error 15: File not found. 

Should I just do this? Or is it bad to guess? 
root (hd0,0)
setup (hd0)

---

### Post by oldfred on 2010-12-09
Boot script shows no stage1. I do not remember if you have to have that still or not. Script shows this so try it.
 190.7GB: boot/grub/stage2

So yes I would try the rest of the commands. If it does not work then grub legacy will need reinstalling.

---

### Post by JPBodner on 2010-12-11
Nothing has worked with those commands.  How do I install grub legacy?  If this doesn't fly, I'll just reinstall Ubuntu

---

### Post by oldfred on 2010-12-11
You can just totally reinstall grub or grub2 from a chroot with a liveCD. I would suggest grub2.

chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by JPBodner on 2010-12-12
I reinstalled Maverick from scratch, which isn't such a bad thing.  It all seemed to go well, but I'm still not getting Grub to appear.  If I boot from sda (Linux) I get the following:

invalid system disk
replace the disk and then press any key

Here's my updated script output

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
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

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

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

/dev/sda1    *          2,048   469,962,751   469,960,704  83 Linux
/dev/sda2         469,964,798   488,396,799    18,432,002   5 Extended
/dev/sda5         469,964,800   488,396,799    18,432,000  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   312,560,639   312,560,577   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4016 MB, 4016045568 bytes
255 heads, 63 sectors/track, 488 cylinders, total 7843839 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        54865137-d900-44b4-83a3-29cb05f6e9e8   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        e1e0b4ac-3ee1-4efd-96c3-1ebd3263583c   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4A1CCA271CCA0DBF                       ntfs                                     
/dev/sdb                                                promise_fasttrack_raid_member                               
/dev/sdc1        18A7-3197                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 54865137-d900-44b4-83a3-29cb05f6e9e8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 54865137-d900-44b4-83a3-29cb05f6e9e8
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 54865137-d900-44b4-83a3-29cb05f6e9e8
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=54865137-d900-44b4-83a3-29cb05f6e9e8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 54865137-d900-44b4-83a3-29cb05f6e9e8
    echo    'Loading Linux 2.6.35-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=54865137-d900-44b4-83a3-29cb05f6e9e8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 54865137-d900-44b4-83a3-29cb05f6e9e8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 54865137-d900-44b4-83a3-29cb05f6e9e8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 4a1cca271cca0dbf
    drivemap -s (hd0) ${root}
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=54865137-d900-44b4-83a3-29cb05f6e9e8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e1e0b4ac-3ee1-4efd-96c3-1ebd3263583c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  83.9GB: boot/grub/core.img
 165.4GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.35-23-generic-pae
  83.9GB: boot/vmlinuz-2.6.35-23-generic-pae
    .5GB: initrd.img
  83.9GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 20 00  |.X.SYSLINUX..@ .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 26 00 00 00  |........?...&...|
00000020  c2 9f 77 00 bd 03 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 97 31 a7 18 4e  4f 20 4e 41 4d 45 20 20  |..).1..NO NAME  |
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
00000100  7d 00 66 b8 5a bc 02 00  66 ba 00 00 00 00 bb 00  |}.f.Z...f.......|
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


=============================== StdErr Messages: ===============================

ERROR: pdc: zero sectors on /dev/sdb
ERROR: pdc: setting up RAID device /dev/sdb
ERROR: pdc: zero sectors on /dev/sdb
ERROR: pdc: setting up RAID device /dev/sdb
```

Any ideas?

---

### Post by oldfred on 2010-12-12
That sounds more like a BIOS error where it does not see a valid bootable device. What order are you booting and is sda the first boot device in BIOS?

Is this an older BIOS. Older one's had a 137GB boot limit. You installed your system to the full 250GB drive. (Note that your grub.cfg is located at 165GB on drive in boot script near end). As a quicker test than reinstalling you could just shrink your system partiton to 120GB with gparted from the liveCD so the partition is not mounted. It will have to move some data, but the install does not have that much ~3-4GB, so it should not take too long to shrink.

I normally suggest a 20GB system partition and then make the rest of the drive /home (or /data). If sharing with windows part of the data portion should a NTFS shared partition for any data you want to shared between windows & Ubuntu. 

Boot script now as some new comments at the end about RAID?. Was this drive ever part of RAID or did you turn RAID on in the BIOS? RAID settings often get saved on a drive as meta data that interferes with installing. Can happen even with one drive.

---

### Post by JPBodner on 2010-12-13
Victory!!!

I updated my system BIOS, and it was able to find grub and boot to the new Linux installation. 

Sir, I want to sincerely thank you for all your help and patience. I owe you some beers. :)

JP

---

### Post by oldfred on 2010-12-13
Glad it worked.

I may take you up on the offer, but we vacationed this year to Europe and went to Oktoberfest for the first time (and probably only time). I have not over imbibed so much since college. Litre beers are a little large.:)

---

### Post by JPBodner on 2010-12-14
Ok, I spoke too soon. The Grub menu comes up, and I can boot to Linux.  But, when I try to go to XP, I just get a blank screen. I know the windows installation is ok since I can boot to it if I tell the bios to go there first.  Any last thoughts.

---

### Post by oldfred on 2010-12-15
The issue is windows knows it is drive 0 partition 1. When you use BIOS to boot that is what it is and it works.  But when you boot Ubuntu, Ubuntu is drive 0 and windows is drive 1 partition 1. The drivemap command in the grub boot stanza is supposed to make windows think it is still drive 0.

I have seen it work and I have seen it not solved. It almost always is easier to have windows as drive 0, usually first SATA port and Ubuntu as drive 1 or hd1. Ubuntu does not care as much, while the set root = hd0  wiil be wrong on first boot the search line overrides the set root and it will still boot. Run an update to correct the entries for grub & windows then both should work.
sudo update-grub

---

### Post by JPBodner on 2010-12-15
upgrade-grub worked. Thanks again!!:D

---

