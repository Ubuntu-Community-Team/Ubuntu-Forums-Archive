---
title: "deleted partition results in boot problem"
date: 2010-12-24
forum: General Help
---

### Post by SightByVision on 2010-12-24
Hello.

Using gparted, I deleted both the partition with archlinux and the swap in order expand the windows xp partition.
I am now unable to boot, just as gparted warned me.
When I turn my computer on, it just goes to a black screen with a flashing underscore. I cannot type anything, but cntrl-alt-dlt does restart.

I have been attempting to restore grub and/or windows's boot method for the last 24hrs. The main things I've tried were the instructions [here]("http://ubuntuforums.org/showthread.php?t=224351") and using super grub disk. However, I have not been successful.

I am running an Ubuntu live disk.

At the moment, I just want to be able to run windows, but do not have an xp disk because this laptop was issued from my old college.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9d9818d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1        9730    78149632    7  HPFS/NTFS
/dev/sda4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

```

Thanks in advance,
Tom

---

### Post by Quackers on 2010-12-24
You could try Lilo.
Boot into the live cd/usb and in a terminal
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

```
If both run ok try rebooting.

---

### Post by SightByVision on 2010-12-24
Thanks for the prompt reply, Quakers.

I just did as you suggested and still get the flashing underscore.
I'm now trying [this]("http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/") and going to learn more about lilo.

Thanks again.
-T

---

### Post by Quackers on 2010-12-24
You're welcome.
Good luck with that.
A flashing underscore can mean that it can't find an OS. Did you say you had XP installed? I wonder why it's on sda2 then. What was on sda1?
I think you can download XP repair discs but I don't have a link for you.

---

### Post by oldfred on 2010-12-25
I have this in my notes:

per meierfra. mbr.bin may cause problems in some cases better to use lilo

If lilo is installed and windows does not boot, you have windows issues as well.

meierfra. was a regular poster here and solved many boot problems. With a few others he developed a boot script that we all use to analyze systems. In the process of developing script he saw what worked and what did not and how to solve many issues.

This is also part of the bootinfo pages on sourceforge with solutions to many issues.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page) 

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by nm_geo on 2010-12-25
I would wonder about that sda2 like Quackers asked and  +1 on the info OldFred gave you. I think you will find that ```
 sudo apt-get install ms-sys 
``` is no longer supported.

I also have link for a torrent window recovery disk that I also downloaded and semi-tested.

[HTML]http://www.torrentreactor.net/torrents/3053520/Windows-XP-SP3-Recovery-Console-CD-Image-%28ISO%29 [/HTML]It has a built in CD Burner for the windoz ISO, which worked as well.

---

### Post by SightByVision on 2010-12-25
Merry Christmas!
Thanks for the info--will look into it soon and post results. *EDIT: results below*

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2               2,048   156,301,311   156,299,264   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  33 c0 8e d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |3.....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 07 8b  |...It.8,t.......|
00000040  f0 ac 3c 00 74 fc bb 07  00 b4 0e cd 10 eb f2 88  |..<.t...........|
00000050  4e 10 e8 46 00 73 2a fe  46 10 80 7e 04 0b 74 0b  |N..F.s*.F..~..t.|
00000060  80 7e 04 0c 74 05 a0 b6  07 75 d2 80 46 02 06 83  |.~..t....u..F...|
00000070  46 08 06 83 56 0a 00 e8  21 00 73 05 a0 b6 07 eb  |F...V...!.s.....|
00000080  bc 81 3e fe 7d 55 aa 74  0b 80 7e 10 00 74 c8 a0  |..>.}U.t..~..t..|
00000090  b7 07 eb a9 8b fc 1e 57  8b f5 cb bf 05 00 8a 56  |.......W.......V|
000000a0  00 b4 08 cd 13 72 23 8a  c1 24 3f 98 8a de 8a fc  |.....r#..$?.....|
000000b0  43 f7 e3 8b d1 86 d6 b1  06 d2 ee 42 f7 e2 39 56  |C..........B..9V|
000000c0  0a 77 23 72 05 39 46 08  73 1c b8 01 02 bb 00 7c  |.w#r.9F.s......||
000000d0  8b 4e 02 8b 56 00 cd 13  73 51 4f 74 4e 32 e4 8a  |.N..V...sQOtN2..|
000000e0  56 00 cd 13 eb e4 8a 56  00 60 bb aa 55 b4 41 cd  |V......V.`..U.A.|
000000f0  13 72 36 81 fb 55 aa 75  30 f6 c1 01 74 2b 61 60  |.r6..U.u0...t+a`|
00000100  6a 00 6a 00 ff 76 0a ff  76 08 6a 00 68 00 7c 6a  |j.j..v..v.j.h.|j|
00000110  01 6a 10 b4 42 8b f4 cd  13 61 61 73 0e 4f 74 0b  |.j..B....aas.Ot.|
00000120  32 e4 8a 56 00 cd 13 eb  d6 61 f9 c3 49 6e 76 61  |2..V.....a..Inva|
00000130  6c 69 64 20 70 61 72 74  69 74 69 6f 6e 20 74 61  |lid partition ta|
00000140  62 6c 65 00 45 72 72 6f  72 20 6c 6f 61 64 69 6e  |ble.Error loadin|
00000150  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
00000160  65 6d 00 4d 69 73 73 69  6e 67 20 6f 70 65 72 61  |em.Missing opera|
00000170  74 69 6e 67 20 73 79 73  74 65 6d 00 00 00 00 00  |ting system.....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 2c 44 63  44 52 20 69 73 20 63 6f  |.....,DcDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200

```

XP is on sda2 because that's where I had it before I deleted sda1 (or is it just sda?), which held archlinux.

I installed the ms-sys, restored the windows boot folder, try to boot from super grub disk, and got a new error:

invalid disk partition

Very simplistically, I think I need to get XP on sda1 or tell it to boot from sda2... hopefully the new error message in combination with meierfra's analysis tools (thanks oldfred) will result in swift success.

-T

---

### Post by oldfred on 2010-12-25
Even though the type is 07 for NTFS the boot sector has to have a NTFS signature.

I would try to rebuild to boot sector.

As described, it has an option to "Recover NTFS boot sector from its backup"
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

sudo testdisk

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"
"Write"

then press "q" a few times to quit testdisk

You also need to install lilo to see it that will then let you boot sda2. And with gparted add a boot flag to sda2 as that is the only way windows or lilo know what partition to boot.

---

### Post by SightByVision on 2010-12-26
Hi oldfred,

Do you mean to follow the step-by-step instructions first, and then your instructions?
Or were you just giving me background info about testdisk, and meant for me to follow your instructions exclusively?

Also, I'm not sure how to use lilo to "see it that will then let you boot sda2"...
Do you have instructions or a link?

I did follow the TestDisk step-by-step until I ran the deeper search, listed the files of the partition 2, and got a message that the files seemed damaged, instead of the list. I did not follow the steps further, since I didn't get the same results it said I should.

Then I began to follow your steps, and realized it was unclear what you meant.

EDIT: I am trying to install lilo:

```
ubuntu@ubuntu:~$ sudo /sbin/lilo
Fatal: Cannot open: /etc/lilo.conf

```



-T

---

### Post by Quackers on 2010-12-26
Try
```
sudo apt-get install lilo

sudo lilo -M /dev/sda mbr
```

---

### Post by SightByVision on 2010-12-26
@Quakers: this will put lilo on the mbr?
where can I access lilo.conf to edit it so that it loads the windows partition?

EDIT: Okay so Lilo is on the MBR. However, since I'm running a live disk and do not intend to have a linux partition, how do I edit lilo.conf so that Lilo boots windows? I tried mounting sda so that I could look for lilo.conf, but I got the following messages:

```

ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sda /mnt/sda
NTFS signature is missing.
Failed to mount '/dev/sda': Invalid argument
The device '/dev/sda' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

ubuntu@ubuntu:~$ sudo mount -t auto /dev/sda /mnt/sda
mount: you must specify the filesystem type

ubuntu@ubuntu:~$ sudo mount -t ext3  /dev/sda /mnt/sda
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```


EDIT: New boot info

```
                                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   156,301,311   156,299,264   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        88F2EB10CD0EB400                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/88F2EB10CD0EB400  fuseblk    (rw,nosuid,nodev,allow_other,blksize=512,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=3

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

C:\ = "Unidentified operating system on drive C."

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  33 c0 8e 4e 54 46 53 20  20 20 20 00 02 01 00 00  |3..NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 09 75 13 83  ff ef 50 09 00 00 00 00  |.....u....P.....|
00000030  00 00 60 00 00 00 00 00  15 f7 70 02 00 00 00 00  |..`.......p.....|
00000040  02 00 00 00 08 00 00 00  00 b4 0e cd 10 eb f2 88  |................|
00000050  00 00 00 00 00 73 2a fe  46 10 80 7e 04 0b 74 0b  |.....s*.F..~..t.|
00000060  80 7e 04 0c 74 05 a0 b6  07 75 d2 80 46 02 06 83  |.~..t....u..F...|
00000070  46 08 06 83 56 0a 00 e8  21 00 73 05 a0 b6 07 eb  |F...V...!.s.....|
00000080  bc 81 3e fe 7d 55 aa 74  0b 80 7e 10 00 74 c8 a0  |..>.}U.t..~..t..|
00000090  b7 07 eb a9 8b fc 1e 57  8b f5 cb bf 05 00 8a 56  |.......W.......V|
000000a0  00 b4 08 cd 13 72 23 8a  c1 24 3f 98 8a de 8a fc  |.....r#..$?.....|
000000b0  43 f7 e3 8b d1 86 d6 b1  06 d2 ee 42 f7 e2 39 56  |C..........B..9V|
000000c0  0a 77 23 72 05 39 46 08  73 1c b8 01 02 bb 00 7c  |.w#r.9F.s......||
000000d0  8b 4e 02 8b 56 00 cd 13  73 51 4f 74 4e 32 e4 8a  |.N..V...sQOtN2..|
000000e0  56 00 cd 13 eb e4 8a 56  00 60 bb aa 55 b4 41 cd  |V......V.`..U.A.|
000000f0  13 72 36 81 fb 55 aa 75  30 f6 c1 01 74 2b 61 60  |.r6..U.u0...t+a`|
00000100  6a 00 6a 00 ff 76 0a ff  76 08 6a 00 68 00 7c 6a  |j.j..v..v.j.h.|j|
00000110  01 6a 10 b4 42 8b f4 cd  13 61 61 73 0e 4f 74 0b  |.j..B....aas.Ot.|
00000120  32 e4 8a 56 00 cd 13 eb  d6 61 f9 c3 49 6e 76 61  |2..V.....a..Inva|
00000130  6c 69 64 20 70 61 72 74  69 74 69 6f 6e 20 74 61  |lid partition ta|
00000140  62 6c 65 00 45 72 72 6f  72 20 6c 6f 61 64 69 6e  |ble.Error loadin|
00000150  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
00000160  65 6d 00 4d 69 73 73 69  6e 67 20 6f 70 65 72 61  |em.Missing opera|
00000170  74 69 6e 67 20 73 79 73  74 65 6d 00 00 00 00 00  |ting system.....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 2c 44 63  44 52 20 69 73 20 63 6f  |.....,DcDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200
```

---

### Post by oldfred on 2010-12-26
You do not want lilo.conf or any of the rest of lilo. Lilo is like the windows boot loader in that the part of the code in the MBR looks for the active partition (boot flag) and jumps to that partition to find more boot code in the partition boot sector. Since we want to boot windows we just leave the windows code in the windows partition and lilo will boot it.

Lilo will boot linux but then has to have its code in the partition boot sector, but that is not what we want. Grub does not normally use the partition boot sector. The grub code in the MBR uses the rest of grub to boot and it can then directly jump to the windows partition boot sector to 'chainload' windows.

I had posted instructions for another and it solved his issue. I have not used testdisk enough to know all the details. Links were to give more info on testdisk and see what it may show. I think the specific instructions I gave should rebuild a windows boot sector, but if the rest of windows is corrupted it will not solve that.

---

### Post by SightByVision on 2010-12-27
I decided to dual boot, so I now have Ubuntu LTS on the hard drive.
At the grub window, when I choose "Windows XP," it just shows the flashing hash. Fortunately Ubuntu works.

I have used TestDisk to restore the Windows boot sector from the backup, however I still get the hash. I will try to use the Super Grub Disk to restore the Windows boot.

Here is the new boot script info. For sda1 (Windows), the script says "Boot sector info:  No errors found in the Boot Parameter Block." This combined with the continuing dysfunction would seem to indicate there is something else wrong/corrupted...

EDIT: just noticed the text to the left of first BootLoader code--there is something about an invalid partition table and the DcDR being compressed...

Thank you Quackers and oldfred for your continued input.
Tom

ps I have limited Internet access now that I'm home. I used to tether my nokia 5230, but now that I am unable to access the Ovi Suite, I cannot tether.


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   140,728,015   140,725,968   7 HPFS/NTFS
/dev/sda2         140,728,318   156,301,311    15,572,994   5 Extended
/dev/sda5         140,728,320   155,529,215    14,800,896  83 Linux
/dev/sda6         155,531,264   156,301,311       770,048  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        88F2EB10CD0EB400                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        e637b618-6551-4df3-a1f3-97035e612eba   ext4                                     
/dev/sda6        665d1a86-fae7-4bca-8cf6-af10006945b9   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=3

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

C:\ = "Unidentified operating system on drive C."


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
search --no-floppy --fs-uuid --set e637b618-6551-4df3-a1f3-97035e612eba
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
search --no-floppy --fs-uuid --set e637b618-6551-4df3-a1f3-97035e612eba
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set e637b618-6551-4df3-a1f3-97035e612eba
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=e637b618-6551-4df3-a1f3-97035e612eba ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set e637b618-6551-4df3-a1f3-97035e612eba
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=e637b618-6551-4df3-a1f3-97035e612eba ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set e637b618-6551-4df3-a1f3-97035e612eba
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set e637b618-6551-4df3-a1f3-97035e612eba
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 88f2eb10cd0eb400
	drivemap -s (hd0) ${root}
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=e637b618-6551-4df3-a1f3-97035e612eba /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=665d1a86-fae7-4bca-8cf6-af10006945b9 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  77.3GB: boot/grub/core.img
  74.8GB: boot/grub/grub.cfg
  76.9GB: boot/initrd.img-2.6.32-24-generic
  77.4GB: boot/vmlinuz-2.6.32-24-generic
  77.3GB: boot/vmlinuz-2.6.32-24-generic.dpkg-tmp
  76.9GB: initrd.img
  77.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  33 c0 8e 4e 54 46 53 20  20 20 20 00 02 01 00 00  |3..NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 09 75 13 83  cf 4e 63 08 00 00 00 00  |.....u...Nc.....|
00000030  00 00 60 00 00 00 00 00  15 f7 70 02 00 00 00 00  |..`.......p.....|
00000040  02 00 00 00 08 00 00 00  00 b4 0e cd 10 eb f2 88  |................|
00000050  00 00 00 00 00 73 2a fe  46 10 80 7e 04 0b 74 0b  |.....s*.F..~..t.|
00000060  80 7e 04 0c 74 05 a0 b6  07 75 d2 80 46 02 06 83  |.~..t....u..F...|
00000070  46 08 06 83 56 0a 00 e8  21 00 73 05 a0 b6 07 eb  |F...V...!.s.....|
00000080  bc 81 3e fe 7d 55 aa 74  0b 80 7e 10 00 74 c8 a0  |..>.}U.t..~..t..|
00000090  b7 07 eb a9 8b fc 1e 57  8b f5 cb bf 05 00 8a 56  |.......W.......V|
000000a0  00 b4 08 cd 13 72 23 8a  c1 24 3f 98 8a de 8a fc  |.....r#..$?.....|
000000b0  43 f7 e3 8b d1 86 d6 b1  06 d2 ee 42 f7 e2 39 56  |C..........B..9V|
000000c0  0a 77 23 72 05 39 46 08  73 1c b8 01 02 bb 00 7c  |.w#r.9F.s......||
000000d0  8b 4e 02 8b 56 00 cd 13  73 51 4f 74 4e 32 e4 8a  |.N..V...sQOtN2..|
000000e0  56 00 cd 13 eb e4 8a 56  00 60 bb aa 55 b4 41 cd  |V......V.`..U.A.|
000000f0  13 72 36 81 fb 55 aa 75  30 f6 c1 01 74 2b 61 60  |.r6..U.u0...t+a`|
00000100  6a 00 6a 00 ff 76 0a ff  76 08 6a 00 68 00 7c 6a  |j.j..v..v.j.h.|j|
00000110  01 6a 10 b4 42 8b f4 cd  13 61 61 73 0e 4f 74 0b  |.j..B....aas.Ot.|
00000120  32 e4 8a 56 00 cd 13 eb  d6 61 f9 c3 49 6e 76 61  |2..V.....a..Inva|
00000130  6c 69 64 20 70 61 72 74  69 74 69 6f 6e 20 74 61  |lid partition ta|
00000140  62 6c 65 00 45 72 72 6f  72 20 6c 6f 61 64 69 6e  |ble.Error loadin|
00000150  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
00000160  65 6d 00 4d 69 73 73 69  6e 67 20 6f 70 65 72 61  |em.Missing opera|
00000170  74 69 6e 67 20 73 79 73  74 65 6d 00 00 00 00 00  |ting system.....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 2c 44 63  44 52 20 69 73 20 63 6f  |.....,DcDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda2

00000000  a0 d2 68 30 df 69 ef a6  59 b3 58 ce b4 69 4d 09  |..h0.i..Y.X..iM.|
00000010  35 a4 58 e8 18 21 07 28  63 eb 77 70 ba 32 60 f9  |5.X..!.(c.wp.2`.|
00000020  6a b2 88 fd 41 80 00 bc  ce 61 e6 04 46 9f aa 26  |j...A....a..F..&|
00000030  78 75 76 d1 13 25 8a 18  a2 9f f0 53 91 3e 62 e5  |xuv..%.....S.>b.|
00000040  88 8a 69 38 ee b8 09 99  82 23 49 41 53 f3 14 94  |..i8.....#IAS...|
00000050  47 bb 4e 1e 5d d0 eb ef  45 0b e7 6b bd 68 8c 6a  |G.N.]...E..k.h.j|
00000060  20 54 e5 5b 34 ff 96 af  d5 7f 29 b2 c6 89 ae 0e  | T.[4.....).....|
00000070  fe 87 54 af 00 bd d8 c3  fb 0c ff 42 fa 3d 06 b4  |..T........B.=..|
00000080  9b a2 e4 ad 74 74 45 f9  a3 36 ca f2 3c f2 9c 77  |....ttE..6..<..w|
00000090  8c 45 fe 91 d6 35 fc e7  da 6d 87 97 45 14 8a 38  |.E...5...m..E..8|
000000a0  78 92 30 cc ed 29 27 07  11 d5 a5 99 b3 12 cb a4  |x.0..)'.........|
000000b0  66 3b a9 31 e8 63 b1 48  f7 06 41 d6 9e 41 72 70  |f;.1.c.H..A..Arp|
000000c0  79 5f e3 21 27 11 02 46  32 90 7b 5f 6e 77 02 7a  |y_.!'..F2.{_nw.z|
000000d0  c8 68 b5 cf 8e 35 ca 88  a4 b2 c8 54 78 99 cf ac  |.h...5.....Tx...|
000000e0  b1 1e 79 cb 83 67 23 f4  0b e8 a5 df d8 b0 e7 b0  |..y..g#.........|
000000f0  b6 3e 79 8a 6d 98 c3 e5  d1 d4 01 17 16 7c 12 e4  |.>y.m........|..|
00000100  ea 11 5a dd 72 b2 ec bc  81 74 da e9 eb d0 13 46  |..Z.r....t.....F|
00000110  51 b3 b8 ed 84 13 db b0  2d c5 9c 35 d0 70 63 5d  |Q.......-..5.pc]|
00000120  6b ab 8f b0 d3 45 24 99  9d 4a 92 2b b9 43 1c 9c  |k....E$..J.+.C..|
00000130  e0 4a 78 29 8d 89 6c 71  ad 9e 79 31 61 16 54 da  |.Jx)..lq..y1a.T.|
00000140  57 56 17 96 0b 61 24 b6  29 f8 51 9d 42 c5 d5 52  |WV...a$.).Q.B..R|
00000150  df 6e 49 b7 8d b2 7e 89  28 c1 1a 4b 44 51 08 86  |.nI...~.(..KDQ..|
00000160  62 dc 0a 4c 8f 1c 1e 4e  fc c1 f2 b9 ba 8f 11 3e  |b..L...N.......>|
00000170  39 4b a0 b6 ae 48 b8 06  fe 5b 46 02 15 ec 53 71  |9K...H...[F...Sq|
00000180  14 9c a5 00 c5 aa bd 63  86 7a d6 ff 55 0d 55 b4  |.......c.z..U.U.|
00000190  f4 67 2c 71 38 e4 42 3b  af 52 41 fc 1f 87 0b 9e  |.g,q8.B;.RA.....|
000001a0  fa de 6d 6a 55 e7 78 f3  a4 c6 dd 6a d7 93 07 a8  |..mjU.x....j....|
000001b0  62 83 31 12 4e df c1 43  df f6 46 ce a6 7a 00 fe  |b.1.N..C..F..z..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 d8 e1 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 d8  e1 00 00 c8 0b 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2010-12-27
sda1 
Boot sector type:  Unknown

this is what mine says:
    Boot sector type:  Windows XP

If post #8 using testdisk to rebuild bootsector did not work, you will have to use a windows XP CD and run repairs.

You should only have to run fixboot, but I am giving all the windows fix commands.

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
[COLOR=Red]FIXBOOT  C:[/COLOR]
BOOTCFG  /rebuild  # rebuilds boot.ini

COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

A discussion about the Bootcfg command and its uses fix boot.ini
[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

---

### Post by nm_geo on 2010-12-27
+1 on the [COLOR=Red]FIXBOOT  C:


[/COLOR]

---

