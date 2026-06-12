---
title: "when dual-boots attack - recovering a dead windows partition"
date: 2010-02-15
forum: General Help
---

### Post by Gideon Stargrave on 2010-02-15
Original config:
212 gb Vista partition + ~20 gig Win7 partition.

I installed Karmic over the win7 partition, that went fine. Went to boot into Windows again, and that menu option kept looping back to Grub. Somehow, Grub installed over my Windows bootloader on /dev/sda1 instead of wherever it's supposed to go.

I reinstalled Karmic, making sure grub was NOT pointed at /sda1 this time, then trying to boot into Windows gave me a "no such device" error.

I followed the guide [here](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/) in an attempt to repair my MBR, followed by grub-install /dev/sda. no change in the error, but I can still get into my Karmic install.

Discovered that the arsgeek article was for a version of ms-sys predating its Vista MBR support, so I installed a current version of ms-sys and installed a Vista MBR. No change in symptoms.

At this point I'm entirely past my level of knowledge and am really afraid to touch anything. (I probably should've stopped long ago, but eh) The fact that gparted no longer recognizes the Vista partition as NTFS is also scaring the crap out of me.

fdisk still sees it, though, as follows:
```
skiddyfisk@warhamster:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x71bb413c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27771   223070526    7  HPFS/NTFS
/dev/sda2           27772       30203    19535040   83  Linux
/dev/sda3           30204       30401     1590435    5  Extended
/dev/sda5           30204       30401     1590403+  82  Linux swap / Solaris

```

At this point I'm running a gpart scan as reccomended [here](https://help.ubuntu.com/community/DataRecovery#Data Recovery from damaged filesystem or drive), but I'm not sure if that even applies to my issue. I'm hoping I can restore this thing to booting Windows properly without imaging the drive or something equally absurd. Any help would be appreciated.


Update: Troubleshooting via IM has gotten me further, but not there yet. Updated and reinstalled grub, which doesn't even detect that there's a Windows installation present.

---

### Post by audiomick on 2010-02-15
Hallo Gideon,
to see what you have got, follow the instructions here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
to run meierfra's boot info script. It will show you the state of things. If you can't understand it or still need help, post the results.txt file here (use the code tag, the # button at the top of the post window. That will put the rather long text in a box with a scroll bar).
I might be able to help, and if I can't, I am sure someone else will be able to.

---

### Post by mk1w86 on 2010-02-15
As long as your Vista partition is still OK if you boot from a Vista installation disk you can choose to repair your computer which wil reinstall the Vista bootloader.  You can then boot from your Ubuntu live CD to reninstall grub which should automatically detect Windows and create a boot entry for it.

There is a guide on Vista startup repair here:

[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

By the way if you are running Windows 7 the process is similar. ;)

---

### Post by Gideon Stargrave on 2010-02-15
@mk1: I don't have a Vista DVD handy, or that would've been my first go-to. (OEM laptop with Vista = suck)


@audiomick:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x71bb413c

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   446,141,114   446,141,052   7 HPFS/NTFS
/dev/sda2         446,141,115   485,211,194    39,070,080  83 Linux
/dev/sda3         485,211,195   488,392,064     3,180,870   5 Extended
/dev/sda5         485,211,258   488,392,064     3,180,807  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        82f4e733-630a-4185-bf1e-92443c7de84c   ext4                                     
/dev/sda5        b0090f9f-5586-40ae-91a0-9e1e50ee82fd   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)


=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set 82f4e733-630a-4185-bf1e-92443c7de84c
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 82f4e733-630a-4185-bf1e-92443c7de84c
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=82f4e733-630a-4185-bf1e-92443c7de84c ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 82f4e733-630a-4185-bf1e-92443c7de84c
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=82f4e733-630a-4185-bf1e-92443c7de84c ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 046bd50c3577b5fa
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=82f4e733-630a-4185-bf1e-92443c7de84c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b0090f9f-5586-40ae-91a0-9e1e50ee82fd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 231.1GB: boot/grub/core.img
 230.8GB: boot/grub/grub.cfg
 231.3GB: boot/initrd.img-2.6.31-14-generic
 230.5GB: boot/vmlinuz-2.6.31-14-generic
 231.3GB: initrd.img
 230.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  33 c0 8e d0 bc 00 7c 8e  c0 8e d8 be 00 7c bf 00  |3.....|......|..|
00000010  06 b9 00 02 fc f3 a4 50  68 1c 06 cb fb b9 04 00  |.......Ph.......|
00000020  bd be 07 80 7e 00 00 7c  0b 0f 85 10 01 83 c5 10  |....~..|........|
00000030  e2 f1 cd 18 88 56 00 55  c6 46 11 05 c6 46 10 00  |.....V.U.F...F..|
00000040  b4 41 bb aa 55 cd 13 5d  72 0f 81 fb 55 aa 75 09  |.A..U..]r...U.u.|
00000050  f7 c1 01 00 74 03 fe 46  10 66 60 80 7e 10 00 74  |....t..F.f`.~..t|
00000060  26 66 68 00 00 00 00 66  ff 76 08 68 00 00 68 00  |&fh....f.v.h..h.|
00000070  7c 68 01 00 68 10 00 b4  42 8a 56 00 8b f4 cd 13  ||h..h...B.V.....|
00000080  9f 83 c4 10 9e eb 14 b8  01 02 bb 00 7c 8a 56 00  |............|.V.|
00000090  8a 76 01 8a 4e 02 8a 6e  03 cd 13 66 61 73 1e fe  |.v..N..n...fas..|
000000a0  4e 11 0f 85 0c 00 80 7e  00 80 0f 84 8a 00 b2 80  |N......~........|
000000b0  eb 82 55 32 e4 8a 56 00  cd 13 5d eb 9c 81 3e fe  |..U2..V...]...>.|
000000c0  7d 55 aa 75 6e ff 76 00  e8 8a 00 0f 85 15 00 b0  |}U.un.v.........|
000000d0  d1 e6 64 e8 7f 00 b0 df  e6 60 e8 78 00 b0 ff e6  |..d......`.x....|
000000e0  64 e8 71 00 b8 00 bb cd  1a 66 23 c0 75 3b 66 81  |d.q......f#.u;f.|
000000f0  fb 54 43 50 41 75 32 81  f9 02 01 72 2c 66 68 07  |.TCPAu2....r,fh.|
00000100  bb 00 00 66 68 00 02 00  00 66 68 08 00 00 00 66  |...fh....fh....f|
00000110  53 66 53 66 55 66 68 00  00 00 00 66 68 00 7c 00  |SfSfUfh....fh.|.|
00000120  00 66 61 68 00 00 07 cd  1a 5a 32 f6 ea 00 7c 00  |.fah.....Z2...|.|
00000130  00 cd 18 a0 b7 07 eb 08  a0 b6 07 eb 03 a0 b5 07  |................|
00000140  32 e4 05 00 07 8b f0 ac  3c 00 74 fc bb 07 00 b4  |2.......<.t.....|
00000150  0e cd 10 eb f2 2b c9 e4  64 eb 00 24 02 e0 f8 24  |.....+..d..$...$|
00000160  02 c3 49 6e 76 61 6c 69  64 20 70 61 72 74 69 74  |..Invalid partit|
00000170  69 6f 6e 20 74 61 62 6c  65 00 45 72 72 6f 72 20  |ion table.Error |
00000180  6c 6f 61 64 69 6e 67 20  6f 70 65 72 61 74 69 6e  |loading operatin|
00000190  67 20 73 79 73 74 65 6d  00 4d 69 73 73 69 6e 67  |g system.Missing|
000001a0  20 6f 70 65 72 61 74 69  6e 67 20 73 79 73 74 65  | operating syste|
000001b0  6d 00 00 00 00 62 7a 99  73 73 69 6e 67 00 0d 0a  |m....bz.ssing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by audiomick on 2010-02-15
Hallo.
I am sorry to say that the problem is a bit beyond me.
What the boot info script reports is that you have an intact Grub, including and entry for windows which points at a UUID that must have been the one for sda1.

At the end of the text, there is this
```
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  33 c0 8e d0 bc 00 7c 8e  c0 8e d8 be 00 7c bf 00  |3.....|......|..|
00000010  06 b9 00 02 fc f3 a4 50  68 1c 06 cb fb b9 04 00  |.......Ph.......|
00000020  bd be 07 80 7e 00 00 7c  0b 0f 85 10 01 83 c5 10  |....~..|........|
00000030  e2 f1 cd 18 88 56 00 55  c6 46 11 05 c6 46 10 00  |.....V.U.F...F..|
00000040  b4 41 bb aa 55 cd 13 5d  72 0f 81 fb 55 aa 75 09  |.A..U..]r...U.u.|

....<snip>
```which indicates that there is probably a corrupted (windows?) boot loader there.
I can't even say for sure if the windows partition is probably intact and just not being recognised ( I think so) or really corrupted. You could try and replace the windows mbr using the method that mk1w86 suggested, or one from here
[http://members.iinet.net.au/~herman546/p18.html](http://members.iinet.net.au/~herman546/p18.html)
I suspect that this will overwrite grub, and mean that you will then have to re-install grub.

Might be good to wait a bit and see if someone with a bit more experience can help.
sorry I can't be more helpful.

PS:I suspect that what happened originally was that the Win7 partition had taken over the boot process (I assume that the Win 7 was installed after the Vista), and the whole lot got overwritten by the Ubuntu install, but that is a guess.

---

### Post by Gideon Stargrave on 2010-02-15
I wouldn't doubt win7 mucked it up, though there was user error involved too. :x

Currently downloading a Vista recovery disk while my IM helper is afk, we'll see if that sorts it.

---

### Post by Gideon Stargrave on 2010-02-15
Vista recovery CD can't even see that there's a filesystem there, so I'm guessing the partition is bad somehow.

---

### Post by mk1w86 on 2010-02-15
If you need the data on the Vista partition and you cannot mount it in Linux you might want to take a look at TestDisk:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by audiomick on 2010-02-15
hmmm, doesn't sound good at all.
Maybe you will have to re-install the Vista. That will overwrite grub, which you will then have to re-install. What a pain...

---

### Post by oldfred on 2010-02-15
Windows only sees NTFS partitions with a boot flag. the boot info script did not see the boot flag and seemed to have some issues. Your original fdisk did show a boot flag. I would make sure you have a boot flag and try repairs to the NTFS partition. Then maybe the Vista repair will work.

You can set the flag with gparted or:
set boot flag on for sda1 (off on others)
sudo sfdisk -A1 /dev/sda

From Vista repair disk get to command line and try running checkdisk.

Vista or 7 repair
Always run chkdsk and run again until there are no errors, that may be all that is required
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by Gideon Stargrave on 2010-02-15
Thanks for the info. I took the boot flag off sda1 after the OP, but before trying the Vista recovery disk, as part of other troubleshooting efforts. Will try setting it back and running the VRD again, as soon as the current scan from testdisk finishes (and if it doesn't take care of it)

---

### Post by meierfra. on 2010-02-15
Nothing you have done would change the partition table. So do NOT use testdisk to  rewrite the partition table.  That can only make things worse.
Hang on for more advice.

---

### Post by meierfra. on 2010-02-15
From your description it seems that only your boot sector is messed up.   If your backup boot sector is not corrupted, testdisk should be able to restore your boot sector:

```

sudo testdisk /dev/sda
```

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"Backup BS"
Type "Y" to confirm.
Press q a few times to quit testdisk.

If you don't get a "BackUpBS" option, it means that also your backup boot sector is corrupted and we will have to take a different cause of action.

---

### Post by Gideon Stargrave on 2010-02-15
Thanks for that. (Though it came after I'd already done roughly the same thing XD)

I ran testdisk, and wound up restoring the backup boot sector. My Vista DVD no longer sees my NTFS partition as RAW, but merely a corrupted NTFS partition. A lateral move, but it's something. Maybe NTFS tools will avail me now.

Not touching anything until advised further!

The exact error chkdsk now gives me:

"unable to determine volume version or state"

---

### Post by meierfra. on 2010-02-15
I'm not sure what is going on, but I suggest to give testdisk "rebuildBS" a try.

At the same  testdisk screen as "BackupBS" choose "RebuildBS". Choose "write" on the next screen.

---

### Post by Gideon Stargrave on 2010-02-15
RebuildBS is in progress, will advise, thanks

---

### Post by Gideon Stargrave on 2010-02-15
Rebuilt the boot table, here's where testdisk is sitting:

```
Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1 12 27770 254 63  446141041

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are not identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.




[  Quit  ]  [  List  ]  [Org. BS ]  [Backup BS]  [Rebuild BS]  [  Dump  ]

```

if I go over to list it gives me this:

```
1 * HPFS - NTFS              0   1 12 27770 254 63  446141041



Can't open filesystem. Filesystem seems damaged.

```

Any suggestions?

E: I just ran the boot info script again, in case anything useful has changed.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows Vista/7
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x71bb413c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             74   446,141,114   446,141,041   7 HPFS/NTFS
/dev/sda2         446,141,115   485,211,194    39,070,080  83 Linux
/dev/sda3         485,211,195   488,392,064     3,180,870   f W95 Ext d (LBA)
/dev/sda5         485,211,258   488,392,064     3,180,807  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda5        aac4d662-cf95-49d4-9bf8-cfc92d2a46fe   ext4                                     
/dev/sda6        abfe93af-9781-464d-a165-e2479fceb9e1   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=skiddyfisk)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set aac4d662-cf95-49d4-9bf8-cfc92d2a46fe
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set aac4d662-cf95-49d4-9bf8-cfc92d2a46fe
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=aac4d662-cf95-49d4-9bf8-cfc92d2a46fe ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set aac4d662-cf95-49d4-9bf8-cfc92d2a46fe
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=aac4d662-cf95-49d4-9bf8-cfc92d2a46fe ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=aac4d662-cf95-49d4-9bf8-cfc92d2a46fe /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=abfe93af-9781-464d-a165-e2479fceb9e1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 251.6GB: boot/grub/core.img
 251.6GB: boot/grub/grub.cfg
 250.4GB: boot/initrd.img-2.6.31-14-generic
 250.0GB: boot/vmlinuz-2.6.31-14-generic
 250.4GB: initrd.img
 250.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3



=======Devices which don't seem to have a corresponding hard drive==============

sdb 
=============================== StdErr Messages: ===============================

hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
```

---

### Post by meierfra. on 2010-02-15
> Rebuilt the boot table,

???  I told you not to mess with the partition table:

> /dev/sda1    *            [COLOR="Red"] 74 [/COLOR]  446,141,114   446,141,041   7 HPFS/NTFS
/dev/sda2         446,141,115   485,211,194    39,070,080  83 Linux
/dev/sda3         485,211,195   488,392,064     3,180,870   f W95 Ext d (LBA)
/dev/sda5         485,211,258   488,392,064     3,180,807  82 Linux swap / Solaris

But you changed it.

I don't have time right now to tell you how to get out of this mess. But I'll get back with you  in a couple of hours. Don't do anything until then.

---

### Post by Gideon Stargrave on 2010-02-15
???

> **meierfra. said:**
> I'm not sure what is going on, but I suggest to give testdisk "rebuildBS" a try.

At the same  testdisk screen as "BackupBS" choose "RebuildBS". Choose "write" on the next screen.

I just did what you said.

Appreciate the help, in any case. Not going to mess with it till then.

---

### Post by audiomick on 2010-02-15
Hi.
I think you are in good hands with meierfra.
What he is referring to is this.
From your first post
```
/dev/sda1   *          [COLOR=Red] 1 [/COLOR]      27771   223070526    7  HPFS/NTFS
```From the first time you ran the boot info script
```
/dev/sda1                  [COLOR=Red]63[/COLOR]   446,141,114   446,141,052   7 HPFS/NTFS
```from the second time
```
/dev/sda1    *             [COLOR=Red]74[/COLOR]   446,141,114   446,141,041   7 HPFS/NTFS
```
However it came about, something has changed there, and I think it might be causing you problems.
Wait for meierfra to come back and see what he says.

---

### Post by meierfra. on 2010-02-15
Somehow the start point of your Vista partition has changed from 63 sector to 74 sectors. This command will set it back to 63:

```
echo 63| sudo sfdisk -uS --force /dev/sda -N1

```
 
Don't type it yourself, use copy and paste.


Reboot  to make sure your computer uses the new  partition table.

Now lets  try  testdisk  "Backup BS" and  "Rebuilds BS again:

First follow my instruction from post 13.  

Then follow the same instruction again, but instead of 

Backup BS
Press "Y"

do

"Rebuild BS"
Write.

Also  for further trouble shooting, post the screen before you choose "Rebuild BS and the screen after you chose "Rebuild BS".


After  testdisk "Backup BS" and "Rebuild BS" try to mount your vista partition:


```
sudo mount /dev/sda1 /mnt
ls /mnt
```

if that  does not work try


```
sudo mount -t ntfs-3g /dev/sda1 /mnt
ls /mnt
```

If mounting did not work post the output of

```

sudo fdisk -lu /dev/sda
sudo blkid -p /dev/sda1
```

also report any error messages.

---

### Post by Gideon Stargrave on 2010-02-15
> **meierfra. said:**
> Somehow the start point of your Vista partition has changed from 63 sector to 74 sectors. This command will set it back to 63:

```
echo 63| sudo sfdisk -uS --force /dev/sda -N1

```
 
Don't type it yourself, use copy and paste.


Reboot  to make sure your computer uses the new  partition table.

Did this, about to reboot.

Results of the command: [http://pastebin.com/mecb8fa](http://pastebin.com/mecb8fa)

Rebooting now, will move to the next bit when I get back into Linux.

---

### Post by Gideon Stargrave on 2010-02-15
Rebooted, got as far as grub. "ERROR: bad file system" and dumped to a grub recovery prompt. Now posting from a livecd of Karmic. Should I continue as you posted or was that not supposed to happen?

---

### Post by meierfra. on 2010-02-15
> Should I continue as you posted or was that not supposed to happen?
That definitely was not suppose to happen. When was the last time you  had rebooted?

You can to the same instructions from the Live CD, but you first have to install testdisk via "sudo apt-get install testdisk"  (and you have to enable the "universe" repository.)

While you do this, I will try to figure out what happened.  Don't reboot  until further notice.

---

### Post by Gideon Stargrave on 2010-02-15
> **meierfra. said:**
> 
Now lets  try  testdisk  "Backup BS" and  "Rebuilds BS again:

First follow my instruction from post 13.  

Then follow the same instruction again, but instead of 

Backup BS
Press "Y"

do

"Rebuild BS"
Write.

Also  for further trouble shooting, post the screen before you choose "Rebuild BS and the screen after you chose "Rebuild BS".

I've gotten this far. Screen before choosing rebuild is:

```
Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1 27770 254 52  446141041

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.

```

And after:

```
Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1 27770 254 52  446141041

filesystem size           446141041
sectors_per_cluster       8
mft_lcn                   10
mftmirr_lcn               1048576
clusters_per_mft_record   -10
clusters_per_index_record 1
Extrapolated boot sector and current boot sector are identical.
[  Dump  ]  [  List  ]  [  Quit  ]

```

Mounting:

```
root@ubuntu:/home/ubuntu# mount /dev/sda1 /mnt
root@ubuntu:/home/ubuntu# ls /mnt
aaw7boot.log  BOOTSECT.BAK  Documents and Settings  hiberfil.sys  logs          Multimedia Files  Program Files  SWSetup                    Virtual Machines
altrev        butts         Downloads               HP            MP4debug.log  My documents      $RECYCLE.BIN   System.sav                 Windows
autoexec.bat  Config.Msi    flvrecorder             IO.SYS        MSDOS.SYS     pagefile.sys      Setup          System Volume Information  WTablet
boot          config.sys    Folding                 IPH.PH        msvcp71.dll   PerfLogs          SetupCD.txt    Temp
bootmgr       cygwin        Games                   JIM           msvcr71.dll   ProgramData       stub.log       Users

```

I think this is a success, confirm?

My impluse is to dig up the Vista disk and try and recover from there, but still not touching anything without instructions.

E: I did go into the drive and poke around, and the couple random files I opened read fine.

---

### Post by meierfra. on 2010-02-15
> I think this is a success, confirm?
That looks really good.

I just  had a careful look at your last RESULTS.txt and it's pretty strange.
(looks like you had changed the  partition table and hadn't rebooted yet when you run the boot info script)

But I think  reinstalling Grub should take care of the Grub error you got.

```
sudo  mkdir /Ubuntu
sudo mount /dev/sda2 /Ubuntu
sudo grub-install --recheck --root-directory=/Ubuntu /dev/sda
```

After that reboot and see whether you can get into Vista and Ubuntu.

---

### Post by audiomick on 2010-02-15
I'm sitting on the edge of my chair.
I should be in bed, but I'm not going till I read what has happened!;)

---

### Post by Gideon Stargrave on 2010-02-15
Error encountered:

```
root@ubuntu:/# mkdir /Ubuntu
root@ubuntu:/# mount /dev/sda2 /Ubuntu
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by audiomick on 2010-02-15
errh...
Your first boot info script result had 9.10 on sda2 and swap on sda5, 
the second time sda2 was "unknown" and sda5 had become Ubuntu 9.10.:confused:

---

### Post by meierfra. on 2010-02-15
Yes. I just had realized my self that there  are more problems. Run the boot info script again and post the RESULTS.txt

---

### Post by Gideon Stargrave on 2010-02-15
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x71bb413c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   446,141,103   446,141,041   7 HPFS/NTFS
/dev/sda2         446,141,115   485,211,194    39,070,080  83 Linux
/dev/sda3         485,211,195   488,392,064     3,180,870   f W95 Ext d (LBA)
/dev/sda5         485,211,258   488,392,064     3,180,807  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        046BD50C3577B5FA                       ntfs                                     
/dev/sda2        82f4e733-630a-4185-bf1e-92443c7de84c   ext4                                     
/dev/sda5        b0090f9f-5586-40ae-91a0-9e1e50ee82fd   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /mnt                     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)

=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

I'm not worried about nuking the Ubuntu install if need be, it's 12 hours old and represents little loss. (In case it'd be easier to just reinstall it vs. recovering it)

---

### Post by meierfra. on 2010-02-15
> I'm not worried about nuking the Ubuntu install if need be, it's 12 hours old and represents little loss. (In case it'd be easier to just reinstall it vs. recovering it)
OK.  But let's try a file system check first:

```
sudo e2fsck -fyv /dev/sda2
```

If it correct some errors, run the same command again. Then try

```
sudo  mkdir /Ubuntu
sudo mount /dev/sda2 /Ubuntu
sudo grub-install --recheck --root-directory=/Ubuntu /dev/sda
```
again.

 Even if that works, don't reboot.  I still have to write up instructions to fix grub.cfg

---

### Post by Gideon Stargrave on 2010-02-15
```
sudo e2fsck -fyv /dev/sda2
```

is generating more text than I can feasibly paste here. Suffice to say it's correcting more than "some" errors. @.@

Whole lot of "Inode 45345 ref count is 2, should be 1. Fix? Yes" and such scrolling past.

---

### Post by meierfra. on 2010-02-15
Just stop the process and reinstall. Even if  you would be able  mount /dev/sda2 again,  a clean install sounds like the better option.

---

### Post by Gideon Stargrave on 2010-02-15
Righto. Will be back shortly (I hope) with results

---

### Post by meierfra. on 2010-02-15
I'm not quite sure what happened but I think the worries in my  first post in this thread came true:

> So do NOT use testdisk to rewrite the partition table. That can only make things worse.


Whatever you did the first time you used testdisk, it changed the partition table. You then continued to  work on a system with  a changed partition table and it seems your Ubuntu partition did not like that at all. 

But at least your  Vista partition seems to be back to normal.

If you aren't reinstalling Ubuntu yet, I suggest to boot into  Vista first: 


```
sudo apt-get install lilo
```
(ignore any warning you get. Just press enter)

```
sudo lilo -M /dev/sda  mbr
```

Reboot and you should boot directly into Vista

---

### Post by Gideon Stargrave on 2010-02-15
I wound up booting from my Vista recovery disk and using /fixmbr, and this time it actually worked! Posting from Vista now.

---

### Post by audiomick on 2010-02-15
> **Gideon Stargrave said:**
> I wound up booting from my Vista recovery disk and using /fixmbr, and this time it actually worked! Posting from Vista now.
I think that is effectively the same as the "lilo" commands would have done.
Glad to hear you are winning. Now you only have to re-install Ubuntu...;)

---

### Post by meierfra. on 2010-02-15
> Posting from Vista now.
Great.

Not that it matters, but I'm curios:   Did you try "lilo"  and it failed? Or did you go for "fixmbr" right-away?

---

### Post by Gideon Stargrave on 2010-02-16
> **meierfra. said:**
> Great.

Not that it matters, but I'm curios:   Did you try "lilo"  and it failed? Or did you go for "fixmbr" right-away?


Fixmbr first; I didn't see your post about lilo till I'd fired up Windows, having already rebooted when you made it.

Thanks for the help, mate, losing this partition would've ruined my whole weekend.

---

