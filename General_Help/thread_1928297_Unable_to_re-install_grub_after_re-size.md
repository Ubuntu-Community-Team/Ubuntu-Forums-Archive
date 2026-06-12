---
title: "Unable to re-install grub after re-size"
date: 2012-02-19
forum: General Help
---

### Post by yelojakit on 2012-02-19
Hi all,

I had created a small partition for Ubuntu 11.10 when I installed Ubuntu. Unfortunately, the only way was to reduce my Win7 partition and move the Ubuntu partition to the left.

Using a live USB of Ubuntu and GParted, I first took off the amount of memory I wanted to add to Ubuntu. Re-booted into Win7 just to make sure everything was copacetic. It was.

I next increased the size. Partway through, GParted freaked out and it went to a list of command lines and caused a panic. I was forced to restart. It couldn't boot to either. I used Boot-Repair to get Windows back. Then I have been following various posts to get grub loader back onto sda3, where the linux partition is. 

Here is a list of ones I've tried:
- Last post of: [http://ubuntuforums.org/showthread.php?t=1485445](http://ubuntuforums.org/showthread.php?t=1485445)
- [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
- Presence1960's first post of: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Right now:[LIST]
[*]Windows boots fine
[*]GParted shows Linux partition correctly sized and has ~5GB of data used, so I'm pretty sure my data is still there
[*]Had installed Ubuntu 10.04 before but it wasn't compatible with my touchscreen (I got too busy to fix it)
[*]When I installed 11.10 it gave a grub2 loader, which if you choose Win7 it will go into another boot that allowed me to choose Ubuntu, which loaded the old grub loader for 10.04
[*]No grub2 now
[/LIST]

Sorry for the long post and random information but I wanted everything to be there. Thank you in advance and please let me know if you need any other information.

---

### Post by wolfen69 on 2012-02-19
Did you look [here]("https://help.ubuntu.com/community/Grub2")?

---

### Post by yelojakit on 2012-02-20
Yes, I've taken a look at it. I just don't know how to implement it.

This is where I am now:
-using find boot/grub/stage1 finds the grub that I originally installed on 10.04 (which for some reason is along with my windows partition)
-attempts at restoring the grub seems to just restore that grub. It makes the boot screen go to grub command-line (using root, setup, and boot) just makes it reboot to grub again.

So what I need to do is get grub back on sda3 where my linux partition is and then eventually, get rid of the old grub.

Thanks

---

### Post by YesGood on 2012-02-20
Hi

Try with Super Grub Disk.

---

### Post by oldfred on 2012-02-20
Supergrub may work, if system has bootable kernel it will boot it and you can fix it from inside your install by uninstalling grub & grub2 and reinstalling grub2.

chroot not required if you can boot.
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

If you still have issues then run the boot info script or use Boot-Repair to run script.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by yelojakit on 2012-02-20
> **oldfred said:**
> 
chroot not required if you can boot.
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)


Boot repair only gives me a grub message. I did not try Super Grub as it seems it would do the same as Boot Repair. Also, I would need to find another USB to put it in (I know these are cheap and easy to find but I don't know where my closest one is)

I was following the quoted site with the "Copy Partition Files" part. But got stuck when I was supposed to run:

```

sudo grub-setup -d /media/XXXX/boot/grub /dev/sda
```

With the following error: cannot stat /media/XXX/boot/grub/boot.img

I checked that directory and found that boot.img isn't in there. I was going to find it from the LiveDistro but boot.img wasn't in there either. 

Using the LiveCD, I've found that my files are definitely still on that partition. I've also found that there is a boot folder in my Windows partition (I believe this is from the previous 10.04 install), should I remove these? My reason/guess for this is that it will cause Boot Repair to fix the linux partition's grub instead of the old grub.

Thanks for the replies. Sorry for the late responses, I don't get a lot of free time and when I do get them, I don't always have the broken computer with me.

---

### Post by oldfred on 2012-02-21
Supergrub often bypasses grub and just boots a kernel it finds. It can also repair in some cases. Boot-Repair often can repair a system, backs up many things and can run the boot-info script so we can see what is wrong.

You can run the new git/test version of boot repair from a liveCd.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

Or the standard version that also has instructions:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by yelojakit on 2012-02-21
Here is the boot-info-script resuts.txt as requested. Let me know if you need anything else. This looks promising, I just don't know how to fix it.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda3 and looks at sector 1166426584 of the same 
                       hard drive for the stage2 file.  A stage2 file is at 
                       this location on /dev/sda.  Stage2 looks on partition 
                       #3 for /boot/grub/menu.lst.
    Operating System:  Ubuntu 11.10
    Boot files:        /etc/fstab

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:   Syslinux looks at sector 30570 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   830,619,647   830,210,048   7 NTFS / exFAT / HPFS
/dev/sda3         830,619,648 1,250,050,047   419,430,400  83 Linux
/dev/sda4       1,250,050,048 1,250,261,679       211,632   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4018 MB, 4018143232 bytes
84 heads, 20 sectors/track, 4671 cylinders, total 7847936 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          1,112     7,847,935     7,846,824   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        1686025D86023DAD                       ntfs       SYSTEM
/dev/sda2        D0DC4AE4DC4AC506                       ntfs       
/dev/sda3        06064391-c4c4-44c9-a738-5f8925497cff   ext4       
/dev/sda4        2802-C848                              vfat       HP_TOOLS
/dev/sdb1        1AE1-1862                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=06064391-c4c4-44c9-a738-5f8925497cff /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 556.195674896 = 597.210558464  boot/grub/stage2                               1

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

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 ca 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 40 82 4a  |........?....@.J|
00000020  b0 3a 03 00 1b 03 00 00  00 00 00 00 02 00 00 00  |.:..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 48 c8 02 28 4e  4f 20 4e 41 4d 45 20 20  |..)H..(NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200



```

---

### Post by yelojakit on 2012-02-21
New update, I was able to uninstall the old grub and ubuntu (the 10.04), I ran Boot-Repair again hoping to get it to run, but it still didn't work. Here is the updated Results file or the number  851503 for where they post it.

```
                 Boot Info Script 0.60-git      [2 Jan 2012]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

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
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:  Grub Legacy (v0.97) is installed in the boot sector 
                       of sda3 and looks at sector 1166426584 of the same 
                       hard drive for the stage2 file.  A stage2 file is at 
                       this location on /dev/sda.  Stage2 looks on partition 
                       #3 for /boot/grub/menu.lst.
    Operating System:  Ubuntu 11.10
    Boot files:        /etc/fstab

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:  Syslinux looks at sector 30570 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   830,619,647   830,210,048   7 NTFS / exFAT / HPFS
/dev/sda3         830,619,648 1,250,050,047   419,430,400  83 Linux
/dev/sda4       1,250,050,048 1,250,261,679       211,632   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4018 MB, 4018143232 bytes
84 heads, 20 sectors/track, 4671 cylinders, total 7847936 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          1,112     7,847,935     7,846,824   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        1686025D86023DAD                       ntfs       SYSTEM
/dev/sda2        D0DC4AE4DC4AC506                       ntfs       
/dev/sda3        06064391-c4c4-44c9-a738-5f8925497cff   ext4       
/dev/sda4        2802-C848                              vfat       HP_TOOLS
/dev/sdb1        1AE1-1862                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=06064391-c4c4-44c9-a738-5f8925497cff /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 556.195674896 = 597.210558464  boot/grub/stage2                               1

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
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)


ADDITIONAL INFORMATION :
**************** log of boot-repair 2012-02-21__15h50 ****************
boot-repair version : 3.16-0ppa5~oneiric
boot-sav version : 3.17-0ppa9~oneiric
glade2script version : 0.3.2.1-0ppa7~oneiric
internet: connected
/usr/share/boot-sav/gui-update.sh: line 232: hash: os-uninstaller: not found
/usr/share/boot-sav/gui-update.sh: line 234: hash: cleanubiquitybefore: not found
python-software-properties version : 0.81.10
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.zDVM4tf3mi --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 3C48D16124B50277AF10D27F32B18A1260D8DA0B
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: key 60D8DA0B: "Launchpad PPA for YannUbuntu" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
Warning: no /etc/apt/sources.list
W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/Release  Unable to find expected entry 'restricted/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists...SET@_progressbar1.pulse()

Building dependency tree...SET@_progressbar1.pulse()

Reading state information...
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 372 not upgraded.
Need to get 118 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ oneiric/main boot-repair all 3.16-0ppa5~oneiric [118 kB]
Download complete and in download only mode
W: Duplicate sources.list entry cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/ oneiric/main i386 Packages (/var/lib/apt/lists/Ubuntu%2011.10%20%5fOneiric%20Ocelot%5f%20-%20Release%20amd64%20(20111012)_dists_oneiric_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
apt-get purge -y --force-yes boot-repair
apt-get purge -y --force-yes boot-sav-gui
apt-get purge -y --force-yes boot-sav
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
apt-get purge -y --force-yes clean-gui
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
apt-get purge -y --force-yes clean
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
apt-get purge -y --force-yes boot-repair-common
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
apt-get purge -y --force-yes clean-ubiquity-common
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
apt-get install -y --force-yes boot-repair
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
dpkg-preconfigure: unable to re-open stdin:
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
LIVESESSION is : yes (Ubuntu 11.10 , oneiric , Ubuntu , x86_64  )
BYTES_BEFORE_PART[1] (sda) = 2048 sectors * 512 bytes = 1048576 bytes.

OSPROBER:
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda2:Windows Recovery Environment (loader):Windows1:chain
/dev/sda3:Ubuntu 11.10 (11.10):Ubuntu:linux

BLKID:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="SYSTEM" UUID="1686025D86023DAD" TYPE="ntfs"
/dev/sda2: UUID="D0DC4AE4DC4AC506" TYPE="ntfs"
/dev/sda3: UUID="06064391-c4c4-44c9-a738-5f8925497cff" TYPE="ext4"
/dev/sda4: LABEL="HP_TOOLS" UUID="2802-C848" TYPE="vfat"
/dev/sdb1: LABEL="PENDRIVE" UUID="1AE1-1862" TYPE="vfat"

1 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.
Total of 3 OS detected on sda disk.
sudo: cannot get working directory
TABLE_TYPE of sda is MSDos
sda1 : sda, not-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda1, with-os, no-gpt, notEFItable, no-fstab.
sda2 : sda, not-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda2, with-os, no-gpt, notEFItable, no-fstab.
sda3 : sda, not-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 64, with boot, /mnt/boot-sav/sda3, with-os, no-gpt, notEFItable, fstab-without-efi.
sda4 : sda, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda4, no-os, no-gpt, notEFItable, no-fstab.

PARTED:

Model: ATA WDC WD6400BEVT-6 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      1049kB  210MB  209MB  primary  ntfs         boot
2      210MB   425GB  425GB  primary  ntfs
3      425GB   640GB  215GB  primary  ext4
4      640GB   640GB  108MB  primary  fat32        lba


Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sdb: 4018MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
1      569kB  4018MB  4018MB  primary  fat32        boot, lba


MOUNT:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type ext4 (rw)
/dev/sda4 on /mnt/boot-sav/sda4 type vfat (rw)


/sys/block/sda:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/dev:  agpgart autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency disk dri ecryptfs fb0 fb1 fd freefall full fuse hidraw0 hidraw1 hpet input kmsg log mapper mcelog mei mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sdb sdb1 sg0 sg1 shm snapshot snd stderr stdin stdout uinput urandom usb usbmon0 usbmon1 usbmon2 v4l vga_arbiter video0 zero
/dev/mapper:  control

DF:

Filesystem    Type    Size  Used Avail Use% Mounted on
/cow     overlayfs    2.9G  137M  2.7G   5% /
udev      devtmpfs    2.9G   12K  2.9G   1% /dev
tmpfs        tmpfs    1.2G  896K  1.2G   1% /run
/dev/sdb1     vfat    3.8G  697M  3.1G  19% /cdrom
/dev/loop0
squashfs    663M  663M     0 100% /rofs
tmpfs        tmpfs    2.9G   28K  2.9G   1% /tmp
none         tmpfs    5.0M     0  5.0M   0% /run/lock
none         tmpfs    2.9G  228K  2.9G   1% /run/shm
/dev/sda1  fuseblk    199M   38M  162M  20% /mnt/boot-sav/sda1
/dev/sda2  fuseblk    396G  110G  287G  28% /mnt/boot-sav/sda2
/dev/sda3     ext4    197G  2.8G  185G   2% /mnt/boot-sav/sda3
/dev/sda4     vfat    100M  6.4M   93M   7% /mnt/boot-sav/sda4

FDISK:

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc297eb30

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   830619647   415105024    7  HPFS/NTFS/exFAT
/dev/sda3       830619648  1250050047   209715200   83  Linux
/dev/sda4      1250050048  1250261679      105816    c  W95 FAT32 (LBA)

Disk /dev/sdb: 4018 MB, 4018143232 bytes
84 heads, 20 sectors/track, 4671 cylinders, total 7847936 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00024857

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        1112     7847935     3923412    c  W95 FAT32 (LBA)



************************Before mainwindow
FSCK_ACTION no PASTEBIN_ACTION yes
recommendedrepair, restore, REINSTALL_POSSIBLE no PURGE_POSSIBLE
UNHIDEBOOT_ACTION yes (10s), noflag (sda1)
PART_TO_REINSTALL_GRUB , PART_TO_REINSTALL_GRUB_PURGE , FORCE_GRUB  () REMOVABLEDISK
USE_SEPARATEBOOTPART  ()  ()
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) ( )
internet: connected

************************Actions
FSCK_ACTION no PASTEBIN_ACTION yes
recommendedrepair, restore, REINSTALL_POSSIBLE no PURGE_POSSIBLE
UNHIDEBOOT_ACTION yes (10s), noflag (sda1)
PART_TO_REINSTALL_GRUB , PART_TO_REINSTALL_GRUB_PURGE , FORCE_GRUB  () REMOVABLEDISK
USE_SEPARATEBOOTPART  ()  ()
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) (sda 1)
Will restore the MBR_TO_RESTORE : sda (mbr) into sda
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 records in
0+1 records out
bootflag_action sda1 (=sda1)
parted /dev/sda set 2 boot off
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory

                                                                          
Information: You may need to update /etc/fstab.

parted /dev/sda set 3 boot off
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory

                                                                          
Information: You may need to update /etc/fstab.

parted /dev/sda set 4 boot off
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory

                                                                          
Information: You may need to update /etc/fstab.

parted /dev/sda set 1 boot on
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory

                                                                          
Information: You may need to update /etc/fstab.

internet: connected
pastebinit  packages needed
internet: connected
sh: getcwd() failed: No such file or directory
W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/Release  Unable to find expected entry 'restricted/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
E: Package 'pastebinit' has no installation candidate
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
dpkg-preconfigure: unable to re-open stdin:
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory
sh: getcwd() failed: No such file or directory

```

---

### Post by oldfred on 2012-02-21
Does Windows work ok?

It looks like you uninstalled wubi, but your install in sda3 is not complete. It does not show kernels & init files.

 It might be repairable, but a reinstall would be quicker.

---

### Post by yelojakit on 2012-02-21
> **oldfred said:**
> Does Windows work ok?

It looks like you uninstalled wubi, but your install in sda3 is not complete. It does not show kernels & init files.

 It might be repairable, but a reinstall would be quicker.

Yes, Windows works ok.

Yeah, a re-install might be quicker but unfortunately, that's not what I need. It took a lot of extra scripts and installations to get it working well for me and I don't want to re-do all that. Plus, that would make this a waste of a thread ;).

I will keep re-installing as a back up plan. I'm going to re-try some of the previous strategies now that I got the old Ubuntu off. I welcome other suggestions as well.

---

### Post by oldfred on 2012-02-21
You can just about manually re-install a full system from chroot and command line.

First chroot into your system and then run updates including adding the latest kernel and grub install.

drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)


#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
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

#reinstall kernel:
sudo apt-get update
sudo apt-get install linux-image
sudo update-grub

sudo dpkg-reconfigure grub-pc

---

### Post by YannBuntu on 2012-02-21
> **yelojakit said:**
> 
```
 sda3  Boot files:        /etc/fstab

(...)

sudo: cannot get working directory
(...)
sda3 : sda, not-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 64, with boot, /mnt/boot-sav/sda3, with-os, no-gpt, notEFItable, fstab-without-efi.

(...)
REINSTALL_POSSIBLE no

```

First time i see such a Boot-Repair log. I guess it is due to the impossibility to chroot in your Ubuntu system ([http://ubuntuforums.org/showpost.php?p=11707741&postcount=201](http://ubuntuforums.org/showpost.php?p=11707741&postcount=201))
If i were you, i would try SuperGrubDisk to boot into Ubuntu, then try repairing it from inside (same commands as oldfred suggested above, but without chroot).

---

### Post by yelojakit on 2012-02-21
> **YannBuntu said:**
> First time i see such a Boot-Repair log. I guess it is due to the impossibility to chroot in your Ubuntu system ([http://ubuntuforums.org/showpost.php?p=11707741&postcount=201](http://ubuntuforums.org/showpost.php?p=11707741&postcount=201))
That does not sound good. There's no way to get chroot to work?

> **YannBuntu said:**
> If i were you, i would try SuperGrubDisk to boot into Ubuntu, then try repairing it from inside (same commands as oldfred suggested above, but without chroot).
I just tried Super Grub Disk (USB did not work for others who are wondering, I had to burn it on a disc). It did not work.

Detect any OS just gives me a Grub 1.99-12 (same one from bootup), with only Windows partition displayed.

Detect any Grub config gives error, no Grub config available.

Detect any Grub2 installation would show my partition with linux on it, clicking on it puts me back at grub command line (how bootup looks like after attempting any fix, recall that boot repair makes boot automatically go to Windows)

---

### Post by YannBuntu on 2012-02-22
ok. Looks like resizing broke everything. If i were you, i would backup the documents, and reinstall Ubuntu (there is a "Upgrade 11.10 to 11.10" option in 11.10's installer that preserves the conf files).

---

### Post by oldfred on 2012-02-22
Because script shows no kernel at all there is nothing for supergrub to boot with. Also it only shows part of grub legacy & an fstab.

Chroot uses the kernel from the liveCD to boot and then CHanges ROOT to your install so you then can try to run all the updates from inside the broken system.

---

### Post by yelojakit on 2012-02-22
> **YannBuntu said:**
> ok. Looks like resizing broke everything. If i were you, i would backup the documents, and reinstall Ubuntu (there is a "Upgrade 11.10 to 11.10" option in 11.10's installer that preserves the conf files).

This sounds like a good idea. How do I backup the files though? I tried cp but I don't have access to the files as it thinks I'm not the owner and I'm not able to chroot into it. Also, just to confirm: the upgrade option appears after I select Install Ubuntu from the liveCD correct?

> **oldfred said:**
> Because script shows no kernel at all there is nothing for supergrub to boot with. Also it only shows part of grub legacy & an fstab.

Chroot uses the kernel from the liveCD to boot and then CHanges ROOT to your install so you then can try to run all the updates from inside the broken system.

I see. What does that mean in terms of next steps? Based off what you're saying, chroot should run fine since it's using the kernel from the liveCD not my install. But this isn't the case. Also, it should not be running Grub legacy. It should have Grub2 on there.

---

### Post by oldfred on 2012-02-22
Where does the chroot fail from post #12?

If kansasnoob's one line version does not work, you have to run it line by line to see what is not working. I think that is more like drs305's version of chrooting.

---

### Post by YannBuntu on 2012-02-22
> **yelojakit said:**
> How do I backup the files though?

If you boot on a Ubuntu CD, choose "Try Ubuntu", then open a file browser with sudo rights (gksudo nautilus), can you access and backup your documents?
if no, i see no other choice than using TestDisk.

---

### Post by yelojakit on 2012-02-22
> **oldfred said:**
> Where does the chroot fail from post #12?

If kansasnoob's one line version does not work, you have to run it line by line to see what is not working. I think that is more like drs305's version of chrooting.

It fails when I try "sudo chroot /mnt/temp" it says that I cannot chroot because it cannot find directory /bin/bash. I did not do the one line version. I used drs305's version.

> **YannBuntu said:**
> If you boot on a Ubuntu CD, choose "Try Ubuntu", then open a file browser with sudo rights (gksudo nautilus), can you access and backup your documents?
if no, i see no other choice than using TestDisk.

When I try to use gksudo nautilus, it doesn't have any of the partitions. I tried gksudo nautilus /mnt/temp/home/XXX but it gives two files, a README and an executable. The README states that the drive has been unmounted for my protection and that I can access it by double clicking the executable. Double-clicking the executable causes a terminal to pop up for half a second then close.

---

### Post by yelojakit on 2012-02-22
> **YannBuntu said:**
> if no, i see no other choice than using TestDisk.

How do you run TestDisk? I downloaded the bz file onto a USB drive, unzipped it but was not able to run the executable from the command-line and the folder. I tried booting to it (as a desperate try).

Also, how does TestDisk differ from the data recovery on GParted?

---

### Post by YannBuntu on 2012-02-22
How do you run TestDisk? > it's in Ubuntu repositories. so boot on a Ubuntu CD and in a terminal type:

```
sudo apt-get install testdisk
```

how does TestDisk differ from the data recovery on GParted? > i don't know

---

### Post by oldfred on 2012-02-22
More info on testdisk:

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

### Post by yelojakit on 2012-02-23
YannBuntu, it is not in the repositories I don't think. I can't find it in the software center or by using the command-line.

Oldfred, thank you. I already found most of those. I just needed help on getting it to run. Most of the documentation you gave was for once you already got it running.

---

### Post by oldfred on 2012-02-23
I have always downloaded with synaptic but you may have to download synaptic also with the very newest versions of Ubuntu

sudo apt-get install synaptic
sudo apt-get install testdisk

In synaptic you may have to turn on universe repositories. Not sure how to do that from command line.

---

### Post by yelojakit on 2012-02-23
> **oldfred said:**
> I have always downloaded with synaptic but you may have to download synaptic also with the very newest versions of Ubuntu

In synaptic you may have to turn on universe repositories. Not sure how to do that from command line.

Yes, I had to turn on universe repositories by going into Software Center->Edit->Software Sources->Select universe repository.

YannBuntu,

TestDisk could not recover any data. It shows the same two files (the README and the Desktop) because it is still locked/encrypted.

---

### Post by yelojakit on 2012-02-23
I used to be able to do
```
sudo grub-install --root-directory=/mnt /dev/sda3
```and boot to grub, but now when I run it I get this error message:

```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda3
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.
```Does this mean that I won't be able to recover anymore?

Relevant new boot information is on this link: [http://paste.ubuntu.com/854878/](http://paste.ubuntu.com/854878/)

---

### Post by oldfred on 2012-02-24
You are trying to install grub2 boot loader to sda3 a partition when you need to install to a drive sda with no number.

Unless you have another boot loader that can chain load, installing grub2 to partition does not let you boot.

---

### Post by yelojakit on 2012-02-24
> **oldfred said:**
> You are trying to install grub2 boot loader to sda3 a partition when you need to install to a drive sda with no number.

Unless you have another boot loader that can chain load, installing grub2 to partition does not let you boot.

Right. That is incorrect.  Based off what I can find, the only reason I can't boot is because it can't find the kernel image. Can I just find the image elsewhere and place it in the correct partition?

Thank you for sticking with me. I know this is a long and arduous process but I really want to fix this.

---

### Post by oldfred on 2012-02-24
You mention encrypted. Is your partition encrypted? That makes for a whole different can of worms. (Laurel and Hardy phrase?).

---

### Post by yelojakit on 2012-02-24
> **oldfred said:**
> You mention encrypted. Is your partition encrypted? That makes for a whole different can of worms. (Laurel and Hardy phrase?).

It was encrypted using eCryptFS, the one that came with Ubuntu. 

So I went with YannBuntu's advice to just upgrade. It copied over some config files (ThunderBird and others, including Chrome). The re-install caused me to not be able to log in, but was fixed by [http://askubuntu.com/questions/65852/cannot-login-to-my-user-account](http://askubuntu.com/questions/65852/cannot-login-to-my-user-account).

I've lost all the applications and software that I've downloaded from what I can tell, including Chrome and it's bookmarks and whatnot (computer broke before I logged onto Chrome and could keep bookmarks).

---

### Post by iamuser_2007 on 2012-02-25
I found some useful topics on [**http://www.NoobsLab.com**]("http://www.NoobsLab.com"), hope this will help you.

[**Noobslab.com - Install Grub2 from live CD/USB**]("http://www.noobslab.com/2011/10/install-grub2-from-live-cdusb-after.html")
[**Noobslab.com - Grub2 customizer/editor for gnome and kde**]("http://www.noobslab.com/2012/01/grub2-customizereditor-for-gnome-and.html")

other grub tweaks from NoobsLab.com
[**Noobslab.com - Add image to grub**]("http://www.noobslab.com/2011/11/add-image-to-your-grub-in-ubuntulinux.html")
[**Noobslab.com - Remove unwanted entries from grub**]("http://www.noobslab.com/2011/12/remove-entries-from-grubgrub2-in.html")

---

### Post by oldfred on 2012-02-25
If you are using encryption you have to have a very good backup policy. The purpose of encryption is to prevent recovery of data from a device. So good backups are your only way to salvage data after system issues.

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

I like rsync but do not know if encryption creates any issues.

---

