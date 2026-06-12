---
title: "USB Disk mounting Problem"
date: 2011-11-19
forum: General Help
---

### Post by madoba on 2011-11-19
Help, I have this  error when trying to mount a usb disk. 
[COLOR=Red]wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/COLOR]
that, I might add, would mount automatically perfectly fine, prior to when I created a backup of my picture directory with a tar command. 

ok I backed it up with this command [COLOR=Black](**sudo tar cvf /dev/sbd1 . **  )[/COLOR]

Ok here are the details, after executing this command it put a bunch of  gibberish files on the usb thumb disk but apparently that's what is was  suppose to do because I could  untar the files 
(**tar xvf /dev/sdb1**)
into another directory and recover the files I just backed up. Ok  everything seems fine. 

However when I unmounted the usb and plugged it back in and restarted the computer, the usb would not mount.

I did a lsusb and found it.
**lsusb**
Bus 001 Device 006: ID 0781:5530 SanDisk Corp. 

I then looked in the dmesg to identify the correct device
**dmesg**
[  247.185730] sd 7:0:0:0: [sdb] Write Protect is off
[  247.185737] sd 7:0:0:0: [sdb] Mode Sense: 43 00 00 00
[  247.185741] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  247.190405] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  247.195803]  sdb: sdb1
[  247.198478] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  247.198487] sd 7:0:0:0: [sdb] Attached SCSI removable disk

when i attempted to mount it with this command. (yes another google page)
**sudo mount -t vfat uid=me gid=users /dev/sdb /home/me/Desktop/flash**

  I got this error
mount: [COLOR=Red]wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/COLOR]

**dmesg** shows
[  360.981267] FAT: bogus number of reserved sectors
[  360.981274] VFS: Can't find a valid FAT filesystem on dev sdb.
[  402.113575] EXT3-fs (sdb): error: can't find ext3 filesystem on dev sdb.

Help, How in the world was it working fine when I first backedup to the  usb thumb drive, only to give me the finger when I rebooted and  attempted to remount the disk thumb drive.

---

### Post by gordintoronto on 2011-11-19
This is a completely incorrect way to access a USB drive: sudo tar cvf /dev/sbd1

The drive should appear on your desktop or in the launcher if you are using Unity. Open it, and use the Paste command to copy files over. Even better, make folders on your USB drive, and copy into the folders.

What version of Ubuntu? I suggest using Gparted (sudo gparted) to format the drive, then do use the File Manager to access it. You might need to install gparted.

---

