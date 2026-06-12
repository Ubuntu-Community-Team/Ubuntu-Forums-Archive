---
title: "Ubuntu won't boot anymore."
date: 2011-02-18
forum: General Help
---

### Post by iguanaboy on 2011-02-18
I've been using Lynx for quite some time without trouble. However, I turned off my laptop for the first time in weeks a few days ago, and now it won't boot anymore. I don't know if that's related, but a week or so ago Ubuntu suggested that I delete a program that wasn't working well (can't remember what it was, though) and I did - expecting that the next update would give me a new and improved version of that faulty program.

Anyway, here's what I get when I try to launch Ubuntu:

[long list of numbers and unrecognized commands]
[Killed]
[mount: mounting /devbon /root/dev failed: no such file or directory]
[mount: mounting /devbon /root/sys failed: no such file or directory]
[mount: mounting /devbon /root/proc failed: no such file or directory]
[Target filesystem doesn't have /sbin/init.]
[No init found. Try passing init= bootarg]

[BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)]
[Enter 'Help' for a list of built-in commands.]

[(initramfs) [(some numbers)] ieee1394: Host added: ID:BUS[0-00:1023] GUID[(some letters and numbers)]



Is there a way to re-open Ubuntu in "safe mode" or something, and extract my files (and hopefully Firefox bookmarks) before re-installing Ubuntu? Even better, is there a way to simply fix the problem?

Any help much appreciated.

---

### Post by oarenj on 2011-02-18
I can't help you but I am having the same exact issue on one of my ubuntu boxes. Just started this morning

Please post if you find anything

---

### Post by kiyop on 2011-02-19
The error message means that kernel and initramfs could not find the correct root partition.

How did you installed ubuntu? Wubi? Into the partition? 

Boot with Ubuntu LiveCD and try to find and mount the partition your ubuntu is installed.

(initramfs) blkid
may display some info. of partitions in your HDD.

---

### Post by Daouuu on 2011-02-19
I woke up to the exact same issue this morning.  The computer was left on overnight and when I went to use it this morning the screen was displaying a bunch of horizontal lines and was unresponsive so I had to do a hard reset.  I would imagine this is what caused the error.   Anyway, I'm using 10.10 installed on a laptop partitioned to use Ubuntu and XP.  I've tried safe mode and the older kernals and it results in the same issue.  XP booted up just fine though.

---

### Post by kiyop on 2011-02-20
As I wrote in the former post, boot with LiveCD and find and mount the partition where ubuntu was installed.
Open "Application"->"Accessory"->"Terminal"
and type 
$ sudo parted -l
and post the result.
Type
$ sudo blkid
and post the result.
Open the **partition** and open
/boot/grub/grub.cfg
or
/boot/grub/menu.lst
**in the partition (where your ubuntu was installed)**
and post the contents of it.

And one more thing to be care.
When your machine freezes, 
press 
r
s
e
i
u
b
successively, **while pressing "ALT" key and "SysRq" key**.
If it does not restarted, press "CTRL" + "ALT" + "DEL".

---

### Post by Daouuu on 2011-02-20
Here's what I get for the first two things you asked for.


Model: ATA HTS541010G9AT00 (scsi)
Disk /dev/sda: 100GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  21.4GB  21.4GB  primary   ntfs            boot
 2      21.4GB  95.4GB  74.0GB  primary   ext4
 3      95.4GB  100GB   4594MB  extended
 5      95.4GB  100GB   4594MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label    

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="74F0C084F0C04E54" TYPE="ntfs" 
/dev/sda2: UUID="f22212ce-74f9-4049-a550-58fe9df7cc93" TYPE="ext4" 
/dev/sda5: UUID="c6c00ed2-8d54-43b9-ad8f-7c6aff382a3f" TYPE="swap"

  I'm having trouble finding /boot/grub/grub.cfg or /boot/grub/menu.lst.    When I try to mount the partition that Ubuntu is installed on I get  this message,

Unable to mount 74 GB Filesystem
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

---

### Post by kiyop on 2011-02-21
"DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending" !!

A short period of Googling, I found:
[http://ubuntuforums.org/showthread.php?t=1175638](http://ubuntuforums.org/showthread.php?t=1175638)

Some problem may be in your partition.
fsck is one way, but sometimes, fsck damages the partition.

$ sudo umount -l /dev/sda2
$ sudo e2fsck -n -v /dev/sda2
may be better.

Do you think there was enough free space in your partition (/dev/sda2)?

If you want to mount, 
$ sudo mount -t ext4 /dev/sda2 /mnt -o ro && nautilus /mnt

---

### Post by Daouuu on 2011-02-27
Well I couldn't do anything with the affected file system from the 10.10 live CD, so I thought I'd give 10.04 a try. It had no trouble at all mounting that partition.  So I unmounted it and ran the check function in gparted, restarted, and everything is back to normal.

Thanks for the help.

---

