---
title: "ubuntu won't boot, made a live usb, but can't access internal HDD"
date: 2011-03-24
forum: General Help
---

### Post by laerub18 on 2011-03-24
hey

the other day my pc (asus eeepc) ran out of battery and i tried turning it on, but it shut down while booting, which apparently damaged the system.

when i turn it on, grub asks me to choose between different versions of ubuntu, but which ever i choose, it doesn't work and brings me to a initramfs prompt and a busybox thingy:


> mount: mounting /dev on/root/dev failed: No such file or directory
Done.
Mount: mounting /sys on/root/sys failed: No such file or directory
Mount: mounting/ proc on/root/proc failed: No such file or directory
Target filesystem doesn't have rquested /sbin/init.
No init found. Try passing init= bootarg.

BusyBox V1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) Built-in shell (ash)
Enter 'hel' for a list of built-in commands.

(initramfs)_

so my idea was to reinstall ubuntu but before i want to save some files that i have on the internal HDD. i made a live USB of ubuntu 10.10, which works well. Under places, i can see my internal hard drive, but if i click on it it doesn't open. I tried going to my computer and right clicking on it and selecting mount, but still no luck.
i get the following error message:

> DBus Error org.gtk.Private.RemoteVolumeMonitor.Failed:An operation is already pending

or sometimes it'll take some time and give this error message:
> DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.



* i tried mounting it with the terminal with 
> sudo mkdir /mnt/harddrive
sudo mount -t auto /dev/sda1 /mnt/harddrive
still with no luck (and i also tried to do it with -o force). when i do this, the terminal cursor keeps blinking but doesn't do anything.

* check for errors with Gparted did not work

* i also tried:
> sudo mkfs -t ext4 -c /dev/sda1
which gave me the following error:
> /dev/sda1 is apparently in use by the system; will not make a filesystem here!

* i tried fsck
> /dev/sda1 is apparently in use by the system; will not make a filesystem here!
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

*also tried e2fsck:
> e2fsck -f -y -v /dev/sda1
> e2fsck 1.41.12 (17-May-2010)
e2fsck: Permission denied while trying to open /dev/sda1
You must have r/w access to the filesystem or be root

i tried doing that with root powers:
> Filesystem mounted or opened exclusively by another program ?
e2fsck:Device or resource busy while trying to open /dev/sda1

*the same command done by gparted gives the same result in the error file:
> Filesystem mounted or opened exclusively by another program ?
e2fsck:Device or resource busy while trying to open /dev/sda1

*finally i figured that a process was probably keeping the device or ressource busy. On the ps aux output, there are some processes that could be related, but when i restart, they are not there and thus don't conflict with the commands. i probably created them when typing all the commands above (plus, i can't kill them anyway - they stay on the list)

So this is where i'm at! :D I really hope you guys can help 




here is the output for sudo fdisk -l

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00031334

Device Boot Start End Blocks Id System
/dev/sda1 * 1 19087 153312256 83 Linux
/dev/sda2 19087 19458 2975745 5 Extended
/dev/sda5 19087 19458 2975744 82 Linux swap / Solaris

Disk /dev/sdb: 2021 MB, 2021654528 bytes
63 heads, 62 sectors/track, 1010 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c7063

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 1010 1972499 c W95 FAT32 (LBA)


info (from Gparted) on sda1:

> fs: ext4
flags: boot
path: /dev/sda1
status: not mounted


df -h output:
> Filesystem Size Used Avail Use% Mounted on
aufs 124M 91M 28M 77% /
none 491M 252K 491M 1% /dev
/dev/sdb1 1.9G 822M 1.1G 43% /cdrom
/dev/loop0 661M 661M 0 100% /rofs
none 497M 104K 497M 1% /dev/shm
tmpfs 497M 32K 497M 1% /tmp
none 497M 92K 497M 1% /var/run
none 497M 4.0K 497M 1% /var/lock

mount output:
> aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


---

### Post by oldfred on 2011-03-24
Abnormal shutdown can corrupt file system and then you do need to run e2fsck. One or two other users had similar issues of partition already mounted. They found they could create a boot CD with Slitaz and then run the filechecks. Not sure what difference a Ubuntu liveCD has. Are you sure you did swap off on swap partition as that will hold all the partitions in an extended partition open.

[http://www.slitaz.org/en/get/](http://www.slitaz.org/en/get/)

I do not think slitaz uses sudo.

e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by laerub18 on 2011-03-25
i'll give slitaz a shot, and let you know !

> e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

that did not work, as i posted earlier:

> 
[QUOTE]e2fsck 1.41.12 (17-May-2010)
e2fsck: Permission denied while trying to open /dev/sda1
You must have r/w access to the filesystem or be root 

i tried doing that with root powers:

> Filesystem mounted or opened exclusively by another program ?
e2fsckevice or resource busy while trying to open /dev/sda1[/QUOTE]

---

### Post by laerub18 on 2011-03-25
ok, fixed this by booting with slitaz and running e2fsck

for other people having the same problem:

download slitaz livecd .iso file on their website
install unetbootin (live usb creator) with:
sudo apt-get install unetbootin or through software center
make bootable usb

boot with slitaz

run terminal login as root (type su). the password is 'root' by default.
then run:
e2fsck
in my case it was
e2fsck /dev/sda1

it fixed the partition. turn off computer, remove usb and voila !

---

### Post by oldfred on 2011-03-25
Glad that worked.

You must be the third or fourth I have seen with this issue. There must be a bug somewhere.

Since you documented the steps to follow I will link to this thread, if I suggest Slitaz again.

---

### Post by laerub18 on 2011-03-25
also can be any other os (such as flax) than ubuntu live
thanks for the help too !

---

### Post by Vortex_nc on 2011-03-26
OK guys I have the same problem as above. My problem however was caused by Windows XP that somehow or other messed with my kubuntu filesystem because it was after switching to xp that I couldn't boot to linux.

Anyway I downloaded SliTaz and ran e2fsck for sda1 and it says It can't find the superblock for the device. or maybe that the sda1 partition is a swap partition, which it is not.

Any ideas?

SOLVED: Hi guys please be wary of the type of Harddrive when using e2fsck. SATA will use sda1 and IDE devices use hda1. I had to go into GParted in SliTaz to realize this. 

e2fsck -f -y -v worked for me. It didn't find a superblock in sda1 because it was scanning a ntfs harddrive.

---

### Post by oldfred on 2011-03-26
Thanks Vortex_nc, that is good to know.

For NTFS you need to use a windows disk and run chkdsk. I have not found anything that runs chkdsk except a windows repair CD, but you can use a Vista or Win7 repair CD to run chkdsk on XP NTFS partitions. You cannot make many other repairs from Vista/7 to XP. 

Although you can also use "ntfsfix" in Ubuntu:
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdXY x- drive y - partition

But that will only do minor repairs and check the internal flag to run chkdsk on the next boot of windows.

---

### Post by laerub18 on 2011-03-26
to check wether it's sda or hda, type:
> sudo fdisk -l

even though using gparted (ubuntu or slitaz) is probably better since it also gives the partition numbers

---

