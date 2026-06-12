---
title: "Hardy boot failed after update drop to initramfs"
date: 2011-04-05
forum: General Help
---

### Post by zaski on 2011-04-05
Hi, I'm new to ubuntu, just installed hardy after I removed Maverick since it doesn't support my ati graphics.
I installed it inside my windows xp pro and run smoothly after installation, added couple of widgets and so on...
after I restarted it the next time, a balloon showed on top saying 113 or so updates are available, so I updated it.
After update I reboot my lappy and it won't get to my ubuntu anymore but works fine with my xp.
I tried several searches on the net to find the solution but can't really figure it out.
I just tried running Boot info script as it might help experts figure out what's wrong with my box and here's what it shows:
```

ubuntu@ubuntu:~/Downloads$ cat /home/ubuntu/Downloads/RESULTS.txt 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /wubildr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /etc/fstab

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda4 starts at sector 80823078.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     6,152,894     6,152,832  12 Compaq diagnostics
/dev/sda2           6,152,895    45,592,469    39,439,575   f W95 Ext d (LBA)
/dev/sda5           6,152,958    45,592,469    39,439,512   7 HPFS/NTFS
/dev/sda3    *     45,596,313    80,822,699    35,226,387   7 HPFS/NTFS
/dev/sda4          80,823,078   156,296,384    75,473,307   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1010 MB, 1010826752 bytes
255 heads, 63 sectors/track, 122 cylinders, total 1974271 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     1,974,270     1,974,208   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       1a864d17-da6f-4523-a1e7-7b15b2a2141b   ext3                                     
/dev/ramzswap0                                          swap                                     
/dev/sda1        3007-17F2                              vfat       PQSERVICE                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        00B4C2A8B4C29F90                       ntfs                                     
/dev/sda4        7E187C08187BBDA9                       ntfs                                     
/dev/sda5        DA448EF9448ED7A1                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        100B-240C                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/DA448EF9448ED7A1  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


==================== sda3/ubuntu/disks/boot/grub/menu.lst: ====================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=00B4C2A8B4C29F90 loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-29-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.24-29-generic root=UUID=00B4C2A8B4C29F90 loop=/ubuntu/disks/root.disk ro quiet splash
initrd        /boot/initrd.img-2.6.24-29-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-29-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.24-29-generic root=UUID=00B4C2A8B4C29F90 loop=/ubuntu/disks/root.disk ro single
initrd        /boot/initrd.img-2.6.24-29-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=00B4C2A8B4C29F90 loop=/ubuntu/disks/root.disk ro quiet splash
initrd        /boot/initrd.img-2.6.24-26-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=00B4C2A8B4C29F90 loop=/ubuntu/disks/root.disk ro single
initrd        /boot/initrd.img-2.6.24-26-generic

title        Ubuntu 8.04.4 LTS, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Microsoft Windows XP Professional
root        (hd0,2)
savedefault
chainloader    +1


======================== sda3/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt

================================ sda3/boot.ini: ================================

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
c:\wubildr.mbr="Ubuntu"

=================== sda3: Location of files loaded by Grub: ===================


    ??GB: ubuntu/disks/boot/grub/menu.lst
    ??GB: ubuntu/disks/boot/initrd.img-2.6.24-26-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.24-26-generic.bak
    ??GB: ubuntu/disks/boot/initrd.img-2.6.24-29-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.24-29-generic.bak
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.24-26-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.24-29-generic

============================= sda3/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  c0 1f 1e 00 01 0f 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 0c 24 0b 10 4e  4f 20 4e 41 4d 45 20 20  |..).$..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 26  1e 00 00 66 ba 00 00 00  |..E}.f.&...f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```Can anyone help me with my problem?
I'm really stuck because my machine's cdrom just stop recognising bootable discs except windows xp and acronis live cd's, so i have to run it using my flash drive and installed boot manager to detect my flash
drive since it's not listed on the bios boot menu...

My machine:
Acer Aspire 5500
512MB Ram
80 GB ATA HD
ATI Mobility Radeon X700

Thanks...:)

---

### Post by bcbc on 2011-04-06
Try chkdsk  (from Windows go to My computer, right click on drive, Properties, Tools, Check disk for errors, fix automatically). You need to reboot to complete. Then you can try defragmenting as well.

---

### Post by HappyTimeHarry on 2011-04-11
Dang... I have a similar problem. When I updated hardy a while back, first my initrd.img-2.6.24-28 broke, so i replaced it with a backup. Well that worked fine until a few days ago when I had another update (2.6.24-29) and I had to revert to using the 2.6.24-28 kernel and image and whatnot. Well that's working fine so far, except I'm afraid I'll be dropped back into grub4dos (I used wubi to install hardy) every time I boot up and will have to choose the old kernel manually. BTW I tried using chkdsk /r the first time before I did anything else, needless to say it didn't find or fix any problems.  

   So I'm assuming this is some sort of bug in the update or update process... Any suggestions? 

BTW I'm also using hardy because of my ATI card.

---

### Post by bcbc on 2011-04-11
> **HappyTimeHarry said:**
> Dang... I have a similar problem. When I updated hardy a while back, first my initrd.img-2.6.24-28 broke, so i replaced it with a backup. Well that worked fine until a few days ago when I had another update (2.6.24-29) and I had to revert to using the 2.6.24-28 kernel and image and whatnot. Well that's working fine so far, except I'm afraid I'll be dropped back into grub4dos (I used wubi to install hardy) every time I boot up and will have to choose the old kernel manually. BTW I tried using chkdsk /r the first time before I did anything else, needless to say it didn't find or fix any problems.  

   So I'm assuming this is some sort of bug in the update or update process... Any suggestions? 

BTW I'm also using hardy because of my ATI card.
Sometimes the initrd.img isn't created properly.
You could try removing the latest kernel, and reinstalling, or try regenerating the initrd.img manually:
sudo update-initramfs -k 2.6.24-29 -c

Do not supply the *-k all* option.

Personally I think the safest is to just remove the latest kernel and then reinstall it.

---

### Post by HappyTimeHarry on 2011-04-11
Well, I'll try but after two updates caused this problem twice I'm not optimistic...
   Question, because I manually removed all 2.6.24-29 files from boot to a different folder in order to boot into 2.6.24-28, will that cause any problems with the reinstall? I'm using the 2.6.24-28 kernel now, should I put the files back before the reinstall? :confused:

---

### Post by mörgæs on 2011-04-11
Are you aware that Hardy will be out of support in a few weeks?

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

---

### Post by HappyTimeHarry on 2011-04-11
> **mörgæs said:**
> Are you aware that Hardy will be out of support in a few weeks?

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

Yes I am, but I'm the king of procrastination and besides that I'm having trouble deciding which distro I want to try next. In the meantime I'm just trying to keep this ship afloat. But your right I should probably just abandon hardy and make the switch already, still I wonder why it is that they bother releasing buggy updates when they are just going to discontinue support soon...

Don't take that as a sign that I don't want help with my current problem. :p

---

### Post by bcbc on 2011-04-11
> **HappyTimeHarry said:**
> Well, I'll try but after two updates caused this problem twice I'm not optimistic...
   Question, because I manually removed all 2.6.24-29 files from boot to a different folder in order to boot into 2.6.24-28, will that cause any problems with the reinstall? I'm using the 2.6.24-28 kernel now, should I put the files back before the reinstall? :confused:

I'm not really sure what to advise. If it was me, I would restore the files to where they were and uninstall using synaptic, but I don't suppose it makes too much difference. If you are concerned with having the latest updates then - as [mörgæs]("http://ubuntuforums.org/member.php?u=939075") points out - you won't have support for much longer. If you are not concerned, just keep using the older kernel.

What ATI card do you have? I have two computers running on ATI cards: X1300 and an older 9000

---

