---
title: "Can't mount volume because locked by fsck, caused by setting fsck=2 in /etc/fstab"
date: 2010-03-31
forum: General Help
---

### Post by wesli_1 on 2010-03-31
Hi guys

I have a lvm volume which is listed in /etc/fstab. If in /etc/fstab I set fsck=0 I have no problems. If however I set fsck=2, I can't mount the volume, apparently because it is locked by an fsck process.

There is no message during the boot process to say fsck is being run, and besides I thought if fsck runs it holds up the boot process until it is completed...

I am completely stumped so if anybody can help that would be great!


Here is all the relevant info:

I am running Ubuntu 9.10
```
wes@Mario:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic

```/etc/fstab
```
wes@Mario:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>     <mount point>   <type>  <options>           <dump>  <pass>
proc                /proc           proc    defaults            0       0
/dev/mapper/mario-root     /               ext4    errors=remount-ro     0       1
# /boot was on /dev/sda5 during installation
UUID=26c468d8-1683-4ddc-9cc4-b3cb4acdc396 /boot ext2    defaults        0       2
/dev/mapper/mario-swap none                swap    sw                  0       0

/dev/mapper/mario-data  /data  ext3  defaults  0  2

```When I try to mount it:
```
wes@Mario:~$ sudo mount -a
mount: /dev/mapper/mario-data already mounted or /data busy

```When I try to mount it somewhere else:
```
wes@Mario:~$ sudo mkdir /media/mountdatahere
wes@Mario:~$ sudo mount /dev/mapper/mario-data /media/mountdatahere/
mount: /dev/mapper/mario-data already mounted or /media/mountdatahere/ busy

```When I check for processes using the volume, it looks like fsck is running on the partition I am trying to mount:
```
wes@Mario:~$ sudo lsof | grep mario-data
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/wes/.gvfs
      Output information may be incomplete.
fsck.ext3  475       root    3u      BLK      252,2 0x75d295a000       2140 /dev/mapper/mario-data
udevd      589       root    4r      DIR       0,15           60       2184 /dev/.udev/links/disk\x2fby-id\x2fdm-name-mario-data

```Mounted file systems:
```
wes@Mario:~$ mount
/dev/mapper/mario-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda5 on /boot type ext2 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/wes/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=wes)

```Partition table:
```
wes@Mario:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5669258f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121570   976510993+  8e  Linux LVM
/dev/sda2          121571      121601      249007+   5  Extended
/dev/sda5          121571      121601      248976   83  Linux

```

---

