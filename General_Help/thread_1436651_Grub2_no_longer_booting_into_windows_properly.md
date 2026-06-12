---
title: "Grub2 no longer booting into windows properly"
date: 2010-03-22
forum: General Help
---

### Post by unc0nn3ct3d on 2010-03-22
so after my upgrade to 10.04 I'm experiencing a puzzling problem with Grub2.  It can load everything fine except for XP.  I have XP on a separate partition, it is detecting fine and the grub.cfg file is created withou a problem when I the appropriate commands to update and upgrade grub.  What happens is that I select Windows XP from the list and it goes to a black screen where a cursor in the top left corner blinks 3-5 times and then immediately kicks me back to the Grub menu.  I can do this forever but the grub menu just gets reloaded every time.  Any ideas?

Here is the windows portion of my Grub.cfg:

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
        insmod ntfs
        set root='(hd0,2)'
        search --no-floppy --fs-uuid --set 8cf8cc34f8cc1df8
        drivemap -s (hd0) ${root}
        chainloader +1

Here is my boot.ini on the ntfs partion I am trying to boot into

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

---

### Post by prodigy_ on 2010-03-22
I think this forum needs a big flashing reminder: "If you're posting about boot problems, **always** include ```
sude fdisk -l
``` output."

---

### Post by oldfred on 2010-03-23
Even better run this script. I have seen the same problem where grub was installed to the windows partition overwritting the windows partition boot sector.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by unc0nn3ct3d on 2010-03-23
Here is the results from the boot_info script.  I've taken out everything from the grub.cfg that was to do with my linux images as they are all working fine and dandy.  Thanks for pointing me to that script, hope this will lead to be getting back into windows.


============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 292587320 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 292412160 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     2,099,199     2,097,152  27 Hidden HPFS/NTFS
/dev/sda2    *      2,099,200   292,138,999   290,039,800   7 HPFS/NTFS
/dev/sda3         292,139,008   390,717,439    98,578,432  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4075 MB, 4075290624 bytes
7 heads, 6 sectors/track, 189513 cylinders, total 7959552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,192     7,959,551     7,951,360   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7046E66146E62794                       ntfs       WINRE                         
/dev/sda2        8CF8CC34F8CC1DF8                       ntfs                                     
/dev/sda3        9b7fc77b-1088-4874-b53a-0f2f2f009fe5   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F009-64A5                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /media/ntfs              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/usb0              vfat       (rw,noexec,nodev,sync,noatime,nodiratime)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=ryanw)


================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 9b7fc77b-1088-4874-b53a-0f2f2f009fe5
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 9b7fc77b-1088-4874-b53a-0f2f2f009fe5
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 8cf8cc34f8cc1df8
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

=============================== sda3/etc/fstab: ===============================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=9b7fc77b-1088-4874-b53a-0f2f2f009fe5 /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda2	/media/ntfs	ntfs-3g

=================== sda3: Location of files loaded by Grub: ===================


 149.7GB: boot/grub/core.img
 163.9GB: boot/grub/grub.cfg
 150.1GB: boot/initrd.img-2.6.31-14-generic
 150.4GB: boot/initrd.img-2.6.31-16-generic
 150.3GB: boot/initrd.img-2.6.31-17-generic
 151.6GB: boot/initrd.img-2.6.31-19-generic
 181.3GB: boot/initrd.img-2.6.31-20-generic
 180.0GB: boot/initrd.img-2.6.32-16-generic
 150.1GB: boot/vmlinuz-2.6.31-14-generic
 150.1GB: boot/vmlinuz-2.6.31-16-generic
 151.0GB: boot/vmlinuz-2.6.31-17-generic
 151.3GB: boot/vmlinuz-2.6.31-19-generic
 160.3GB: boot/vmlinuz-2.6.31-20-generic
 181.3GB: boot/vmlinuz-2.6.32-16-generic
 180.0GB: initrd.img
 181.3GB: initrd.img.old
 181.3GB: vmlinuz
 160.3GB: vmlinuz.old

---

### Post by oldfred on 2010-03-23
You have to be the third or fourth user that I have seen in the last couple days where grub is installed to the windows partition overwriting the windows partition boot files. Windows in the MBR just jumps to the PBR or grub jumps to the windows PBR to continue the windows boot process. Did you unintentially install grub2 to sda2 not sda? I  see you also installed grub2 to sda3 but that does not link correctly.

You need to reinstall the windows boot sector. I show all the standard windows commands but you should just need fixboot.

To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:    #Do not run if you still want grub in the MBR
FIXBOOT  C:   # Should be all you need
If other issues these are the standard commands:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
BOOTCFG  /rebuild

---

### Post by unc0nn3ct3d on 2010-03-23
It definitely wasn't intentional.  This all happened after my upgrading my Koala to a Lynx.  I'll go through and attempt the repair here, there isn't any way I can do this repair from inside linux is there?

PS - what was it that gave it away that this is the problem?  Was it the fact that GRUB2 is installed in the MBR of SDA2 and SDA3 ?  Is it only supposed to be installed on one MBR ?

---

### Post by oldfred on 2010-03-23
I have not tried it but you can recover the boot sector with test disk from a backup that windows has. Each drive has only one master boot record and each partition has a partition boot record or boot sector. Windows uses the boot sector but grub does not normally.

repairs including testdisk info & link to testdisk
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
As described, it has an option to "Recover NTFS boot sector from its backup"
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Windows has to have its boot loader in the PBR. Grub2 usually complains about any install to a partition boot and is not normally installed to a partition. Old grub does not complain but the only reason to install to the partition is to chainboot. With grub2 able to find other operating system so well, the need to chainboot is reduced. Chainbooting is loading from one operating systems boot loader to another operating systems boot loader. I have three drives so I do chainboot using the MBR and have old grub in only one of many partitions PBR.

---

### Post by unc0nn3ct3d on 2010-03-24
that definitely looks to be the problem and solution.. I removed grub from that partition fixed up the xp mbr and we're right as rain.

:popcorn:

---

