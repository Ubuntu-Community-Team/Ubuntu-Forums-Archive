---
title: "wubi doesn´t  install in win 7"
date: 2012-05-20
forum: General Help
---

### Post by gurrunaki on 2012-05-20
Hi all, I just try install ubuntu 12.04 in my laptop Toshiba portege Z830 that is running win 7 64, I downloaded wubi from the oficial download site from ubuntu because I want dual boot win 7  and ubuntu, but when I try run wubi, nothing happen, I can not install it and doesn´t give me any error, is wubi still working?

Thanks in advance

---

### Post by wilee-nilee on 2012-05-20
> **gurrunaki said:**
> Hi all, I just try install ubuntu 12.04 in my laptop Toshiba portege Z830 that is running win 7 64, I downloaded wubi from the oficial download site from ubuntu because I want dual boot win 7  and ubuntu, but when I try run wubi, nothing happen, I can not install it and doesn´t give me any error, is wubi still working?

Thanks in advance

Sounds like maybe the launcher was installed. Download the regular install cd burn it or load to a usb/thumb the regular cd has the wubi installer, it will show in the admin computer area.

[http://www.ubuntu.com/](http://www.ubuntu.com/)

You are going to want to have the cd anyway it is about the best tool you can have.

---

### Post by gurrunaki on 2012-05-20
Thanks a lot for your fast reply, but my laptop doesn´t have cd rom, I will try in a usb, in my desktop I installed the version 11.04 with wubi and was working great, I would love use wubi for this installation but looks is not gonna be possible :(

---

### Post by wilee-nilee on 2012-05-20
> **gurrunaki said:**
> Thanks a lot for your fast reply, but my laptop doesn´t have cd rom, I will try in a usb, in my desktop I installed the version 11.04 with wubi and was working great, I would love use wubi for this installation but looks is not gonna be possible :(

It will most likely, the usb/thumb is what I have to use on a netbook I own, works just like a cd and is a little faster with a live setup to test.

---

### Post by Frogs Hair on 2012-05-20
Wubi is no longer included with the Ubuntu ISO starting with 12.04 . It will be developed separately  from now on .

---

### Post by gurrunaki on 2012-05-20
got it!!! Thanks a lot, I'm now trying 12.04, I used unetbooting and no problems at all, now at the moment I figure out how to make the partitions I will install in the hard drive.

Thanks a lot for your help :P

---

### Post by wilee-nilee on 2012-05-20
> **gurrunaki said:**
> got it!!! Thanks a lot, I'm now trying 12.04, I used unetbooting and no problems at all, now at the moment I figure out how to make the partitions I will install in the hard drive.

Thanks a lot for your help :P

You can give us a screenshot of the gparted partitioner on the live cd, make sure to show all HD's there is a dropdown in the top right panel of it to change the HD or usb being read, and we can get you going.

I was not aware that wubi was not part of 12.04 cd download, loading a 12.04 at this moment to confirm though anyway.

---

### Post by gurrunaki on 2012-05-20
Here you go the screen shot, I would like give 25 GB to the 12.04, but not idea how to manage it

---

### Post by wilee-nilee on 2012-05-20
> **gurrunaki said:**
> Here you go the screen shot, I would like give 25 GB to the 12.04, but not idea how to manage it

Actually use gparted for a screen shot but, you have 4 primary partitions that is the max on a single HD. We can work with this but it will be helpful to know where all the boot stuff is on the HD, you will have to lose a partition, and we want to make sure you're covered. So run these command and look in the home of the live cd for results.txt and copy and paste the whole text from it to a reply.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
``` ```
chmod a+x bootinfoscript
``````
sudo bash bootinfoscript
```@Frogs Hair wubi is on the 12.04 here is what it looks like from my W7 set up.
[ATTACH]218352[/ATTACH]
[ATTACH]218353[/ATTACH]

So OP you do still have the option of wubi if you want to just check out Ubuntu, this wubi install can be moved to a partition if you like it and it will be a regular partitioned install then.

This gives you the chance to look without messing with removing partitions and such at this point.

---

### Post by gurrunaki on 2012-05-20
Here it is the txt document, and thanks a lot for your time and your help.

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>........._7...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 15260440 of /dev/sdb1 for 
                       its second stage. SYSLINUX is installed in the  
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2           3,074,048   212,783,103   209,709,056   7 NTFS / exFAT / HPFS
/dev/sda3         212,783,104   229,560,319    16,777,216  84 OS/2 hidden C: drive
/dev/sda4         229,560,320   250,068,991    20,508,672  17 Hidden NTFS / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8011 MB, 8011120640 bytes
41 heads, 41 sectors/track, 9307 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,064    15,646,719    15,638,656   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0032A1D732A1D1C8                       ntfs       System
/dev/sda2        F620A65D20A62499                       ntfs       TI30828000A
/dev/sda4        9240B1F840B1E2E1                       ntfs       HDDRECOVERY
/dev/sdb1        4E63-BD39                              vfat       XAVITO

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32 
prompt 0 
menu title UNetbootin 
timeout 100 
 
label unetbootindefault 
menu label Default 
kernel /ubnkern 
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
 
label ubnentry0 
menu label ^Help 
kernel /ubnkern 
append initrd=/ubninit  
 
label ubnentry1 
menu label ^Try Ubuntu without installing 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash -- 
 
label ubnentry2 
menu label ^Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash -- 
 
label ubnentry3 
menu label ^Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- 
 
label ubnentry4 
menu label Test ^memory 
kernel /install/mt86plus 
append initrd=/ubninit  
 
label ubnentry5 
menu label ^Boot from first hard disk 
kernel /ubnkern 
append initrd=/ubninit  
 
label ubnentry6 
menu label Try Ubuntu without installing 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
 
label ubnentry7 
menu label Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash -- 
 
label ubnentry8 
menu label Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash -- 
 
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  6e c1 6c e7 0e 07 0d 02  7a e2 ff 7f 00 00 00 00  |n.l.....z.......|
00000010  00 00 00 00 00 00 00 c0  ff ff ff 3f 00 00 00 00  |...........?....|
00000020  00 00 00 00 f0 63 00 00  00 00 40 00 00 00 00 00  |.....c....@.....|
00000030  00 00 00 00 fe ff ff ff  00 e0 ff 00 7e f9 ff ff  |............~...|
00000040  40 f0 ff 3f fc 00 fe ff  41 80 00 82 fe ff ff ff  |@..?....A.......|
00000050  83 e0 ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
00000060  9f 18 e8 ff fe ff f7 ff  7f 80 fa ff ff ff ff ff  |................|
00000070  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
00000090  ff ff ff ff ff ff f1 ff  e9 ff ff ff bf f0 ef 83  |................|
000000a0  d7 ff ff ff ff ff df fd  ff ff ff ff ff 8f 7f ff  |................|
000000b0  ff ff ff ff ff ff ff fe  ff ff ff ff ff ff bf ff  |................|
000000c0  ff ff ff ff ff ff ff ff  82 00 10 10 fe ff ff ff  |................|
000000d0  00 29 28 01 fe ff ff ff  08 08 33 10 fe ff ff ff  |.)(.......3.....|
000000e0  ce 19 28 9e fe ff ff ff  9e 9d a8 87 fe ff ff ff  |..(.............|
000000f0  86 03 63 de fe ff ff ff  34 06 50 0e fe ff ff ff  |..c.....4.P.....|
00000100  b6 1b 02 08 ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
00000110  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
00000160  ff ff ff ff ff ff ff ff  fe ff ff ff 7f ff f1 ff  |................|
00000170  ff ff ff ff bf f9 ff 9b  ff ff 9f 60 f8 7f df 7f  |...........`....|
00000180  ff ff 0f 38 00 00 03 06  b2 3c c0 0b ff ff ff ff  |...8.....<......|
00000190  02 20 18 22 ff ff ff ff  a0 0d 10 03 fe ff ff ff  |. ."............|
000001a0  82 23 71 1b fe ff ff ff  12 09 59 07 fe ff ff ff  |.#q.......Y.....|
000001b0  00 24 8b 1c fe ff ff ff  22 6d db 18 fe ff ff ff  |.$......"m......|
000001c0  60 88 f9 00 fe ff ff ff  78 9d 92 19 fe ff ff ff  |`.......x.......|
000001d0  20 f1 4e 09 fe ff ff ff  00 61 86 60 fe ff ff ff  | .N......a.`....|
000001e0  86 07 0f 2a fe ff ff ff  94 a5 4c 10 fe ff ff ff  |...*......L.....|
000001f0  96 a1 dc 41 fe ff ff ff  0c 8a c4 19 fe ff ff ff  |...A............|
00000200


=============================== StdErr Messages: ===============================

bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
```

---

### Post by wilee-nilee on 2012-05-20
No problem with the help, :) I'm not really best at teasing out which exact partition should be removed, this set up has a little extra notation in the windows partitions I'm not fully familiar with. But there are others on the forum that are good at this.

One of the keys here though is that making a backup a full image of the C partition if that is where everything is at is your best insurance policy. All the manufacturer starter W7 installs allow a one time full backup and a recovery disc so if you have not done that I would before doing any partition changes. 

You have a recovery partition, but it can get lost in the scuffle at times with removing a partition, probably wont happen but best to always be prepared as the boy scouts would say. :)

---

### Post by gurrunaki on 2012-05-20
Yes, like you said, I think is good idea make the back up and I will, more or less I know where to make the partition for install ubuntu 12.04, should be I  think in the one that has more GB, there is the only place where I can give the 25 GB to ubuntu, the thing is that in the picture that I post before, there is where I can not find out how to resize it for take 25 GB from it.

---

### Post by wilee-nilee on 2012-05-20
> **gurrunaki said:**
> Yes, like you said, I think is good idea make the back up and I will, more or less I know where to make the partition for install ubuntu 12.04, should be I  think in the one that has more GB, there is the only place where I can give the 25 GB to ubuntu, the thing is that in the picture that I post before, there is where I can not find out how to resize it for take 25 GB from it.

You can't add another partition without removing one if that is what you mean you will make the HD dynamic and have huge problems. 

If you figure out one that you see in windows like a D partition and it is empty you can put a extended in its place with gparted in the ubuntu, and then the ext4 logical for ubuntu and a swap.

With a single HD in a standard mbr set up it is 4 primaries max or 3 and an extended, for many logicals. Windows needs to stay as a primary to boot, but linux installs can be in a extended.

Also W7 has a virtual partitioner for changing the size while running, it is in the admin, disk manager I think, best to use the W7 for changing its partitions. You would use gparted though to switch a windows to a extended or the partitioner that you posted first as a screen shot in the something other section of the install. You can do full partition adding like the logicals and changing there for the ubuntu.

Hope this all makes sense you seem to have a idea of what&#8217;s up, we never know helping so I tend to be really careful. :)

---

### Post by gurrunaki on 2012-05-20
Thanks a lot, I will try and let you know :)

---

