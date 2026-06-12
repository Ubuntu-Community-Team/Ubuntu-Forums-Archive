---
title: "dual boot with xp prob: ntldr is missing"
date: 2010-08-08
forum: General Help
---

### Post by evolmachine on 2010-08-08
I got this message today after cleaning out the inside of my computer.  Didn't really mess with anything.  Booted into Windows XP just fine, had to restart for an update.  Burg loaded, I selected Windows and I get:

"NTLDR is missing. Press CTRL-ALT-DEL to restart."

WTF? Windows breaks itself. Great. My ubuntu install works just fine.  I have 2 separate hard drives, with one OS on each.  I can't access the other drive from ubuntu.  It says

Unable to mount location
Error mounting: mount exited with exit code 13: Index entry out of bounds in directory inode 5.
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


Any help?

---

### Post by wilee-nilee on 2010-08-08
Lets see if it is missing, post the bootscript in my signature in code tags as described.

Do you have a XP install disc?

---

### Post by evolmachine on 2010-08-08
my xp cd got scratched all to hell and wouldn't boot.  i'm downloading another copy now.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/burg.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    72,276,434    72,276,372   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1          67,296,285    72,292,499     4,996,215  82 Linux swap / Solaris
/dev/sdb2                  63    67,296,284    67,296,222   5 Extended
/dev/sdb5                 126    67,296,284    67,296,159  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1999.7 GB, 1999696297984 bytes
255 heads, 63 sectors/track, 243115 cylinders, total 3905656832 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048 3,905,656,831 3,905,654,784   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        82F84E53F84E461F                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2ccfd9b5-e2a7-4d84-94ce-51883a21b82a   swap                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        a8d5b318-7151-4860-9105-2def109eb202   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        40284A46284A3AE4                       ntfs       My Book                       
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,relatime,errors=remount-ro)
/dev/sr2         /media/WD SmartWare      udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)
/dev/sdc1        /media/My Book           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set a8d5b318-7151-4860-9105-2def109eb202
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x1024
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set a8d5b318-7151-4860-9105-2def109eb202
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=30
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
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set a8d5b318-7151-4860-9105-2def109eb202
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=a8d5b318-7151-4860-9105-2def109eb202 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set a8d5b318-7151-4860-9105-2def109eb202
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=a8d5b318-7151-4860-9105-2def109eb202 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

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
UUID=a8d5b318-7151-4860-9105-2def109eb202 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb1 during installation
UUID=2ccfd9b5-e2a7-4d84-94ce-51883a21b82a none            swap    sw              0       0
#/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/scd2       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
   2.9GB: boot/grub/grub.cfg
   9.3GB: boot/initrd.img-2.6.32-24-generic
   4.7GB: boot/vmlinuz-2.6.32-24-generic
   9.3GB: initrd.img
   4.7GB: vmlinuz
=============================== StdErr Messages: ===============================

ls: reading directory sda1/: Input/output error
```

---

### Post by wilee-nilee on 2010-08-08
I'm not seeing any of the XP boot ntldr or boot.ini files in the bootscript, or the others usually there, or a uuid in the Ubuntu grub.cfg file.

Bascially Xp should have this to boot,
Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

I would open the XP partition from Ubuntu to see whats still there, and if you need for a reinstall pull out what you need.

You installed burg have you run ```
sudo update-burg
```
and did you remove grub-pc as burg is grub and is best used by itself.

The funny thing is you have grub in sda but Ubuntu in sdb and it boots, generally on the forums this isn't the case, but this could be due to other issues.

---

### Post by oldfred on 2010-08-08
As it says run chkdsk on sda1.

To repair windows with mounting issues from your Windows XP CD - Do not run fixMBR unless you want windows boot loader in the MBR.
chkdsk c: /r
XP CHKDSK info:
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information.
chkdsk drive /p /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect.

---

### Post by wilee-nilee on 2010-08-08
> **oldfred said:**
> As it says run chkdsk on sda1.

To repair windows with mounting issues from your Windows XP CD - Do not run fixMBR unless you want windows boot loader in the MBR.
chkdsk c: /r
XP CHKDSK info:
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information.
chkdsk drive /p /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect.

+1 This is actually the best start before anything else, I forgot to mention that, since you will have a XP cd.

---

### Post by evolmachine on 2010-08-09
well I now have 2 xp cds that aren't any help.  Shortly after pressing any key to boot from CD, "inspecting hardware configuration" (or something to that effect) flashes by, then both cds simply freeze.  Im staring at a black screen...  waited 10 mins.  nothing.

is there a way run chkdsk without the recovery cd? or anything else i could try?

and the drive is not accessible from Ubuntu. When I try to open it, it simply says: 

```
Unable to mount 37 GB Filesystem
Error mounting: mount exited with exit code 13: Index entry out of bounds in directory inode 5.
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```

update-burg gives:
```
Generating burg.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
ls: reading directory /var/lib/os-prober/mount: Input/output error
ls: reading directory /var/lib/os-prober/mount: Input/output error
ls: reading directory /var/lib/os-prober/mount: Input/output error
ls: reading directory /var/lib/os-prober/mount: Input/output error
done
```

So I should remove grub-pc (and grub2, as it is a dependency)?

---

### Post by wilee-nilee on 2010-08-09
Here is a link to a legit XP ISO.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

Here are more instructions on how to follow oldfreds advice.
[http://kb.wisc.edu/helpdesk/page.php?id=5097](http://kb.wisc.edu/helpdesk/page.php?id=5097)

---

### Post by evolmachine on 2010-08-09
okay so here's the update.  I have tried *5* different windows xp images, including the 2 you linked to from acer and one directly from MS.  I have tried different cd-r's, cd-rw's, dvd-rw's, and even 2 usb sticks.  

All of the cds or dvds get to the "press any key to boot from cd" and then "inspecting your computers hardware configuration" flashes briefly and then a black screen.  I get nothing.  

The usb sticks were an abysmal failure. I used unetbootin to create the bootable usb with all 5 images on 2 different 1GB usb sticks.  The unetbootin menu comes up with "Default" as the only option and infinitely loops a countdown.  Pressing enter only restarts the countdown. Tab gives me some boot gibberish but there is no help: i have no idea what i'd type.

I give up.  This drive has nothing important on it anyway.  How to I just mount the drive, format the damn thing, and use it as a second drive in linux?

---

### Post by efflandt on 2010-08-09
If there was anything essential on it, you could try a USB drive enclosure.  But that might or might not reveal anything if the drive is physically failing and Windows cannot recognize or chkdsk it (how would you know what drive letter to chkdsk?).  Maybe that is why the Windows boot disks hang trying to do anything with it.

I attempted to fix or recover data from a laptop drive that refused to boot. At first I could mount it from an Ubuntu CD, but could hardly copy any files from it before it hung.  In an external USB enclosure neither Ubuntu nor WinXP on another computer could mount it.  But a couple of weeks later I connected it to my Ubuntu desktop and it magically auto mounted and I was able to copy most of the user's dir except for a couple of directories/files.

Later the replacement drive again refused to boot.  In that case chkdsk /f in the USB enclosure on another PC fixed it (one apparently unimportant file lost) and a virus scan removed a virus.

Some drive manufacturers have utilities (like Seagate/Maxtor SeaTools and Western Digital DataLifeguard) to more thoroughly test a drive.  Normally a drive reserves some space to map good sectors in place of bad sectors, but if all the error sectors are used up, that is a bad sign of a failing drive.

Note that you do not "mount" a drive to partition or format it, in fact you cannot do that while it is mounted.  And if it has bad sectors, you may have trouble partitioning or formatting it.

---

### Post by evolmachine on 2010-08-09
there is nothing important on the drive.  the thing that gets me is that i booted into windows and was browsing the web just fine on it, and it needed to restart to "update".  When I restarted, this whole thing happened.  It was working just fine one minute, then the next its not.  Since I never use the drive, I have a hard time believing its failing.  I think it may have been a bad update or something...

again i don't care to save any files from it.  It's literally a windows install and pretty much nothing else. I just want my drive back!  Right now its a friggin paperweight!

I read something about ntfsfix?  i know its not checkdisk but maybe that might help get the drive back?  Right now it seems like linux doesnt want to even touch it, and I'm afraid to just format it through gparted because wilee-nilee said grub is installed on that drive... which is weird.

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/burg.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
```

What concerns me is the first line. How can Grub 2 be installed in the MBR of */dev/sda and looks on the same drive in partition #5* for /boot/burg if there is no partition 5 on sda? not to mention if sda is corrupted or failing, how the hell is grub even loading? forgive me if this is basic i'm still learning here, but logically to me this makes no sense.

---

### Post by oldfred on 2010-08-10
There is a bug in either grub2 or the script that mis-identifies the drive. You will want to reinstall grub2 to sdb and set BIOS to boot sdb before doing anything to the sda drive. Boot into your system and run this:

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose drive, enter to accept, do not choose partitions

If you remove sda for any reason rerun the dpkg command to make sure grub installs to the correct drive on updates.

---

### Post by evolmachine on 2010-08-12
Thanks for all the help.  Reinstalled burg on sdb and unmounted and formatted sda through gparted.  sda is now my /home partition.  goodbye winblowz!

---

