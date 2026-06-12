---
title: "How to give UUID to /dev/sda1 and change TYPE to ext4?"
date: 2011-09-27
forum: General Help
---

### Post by baczko on 2011-09-27
First of all sorry for my English. I use a translator. Unfortunately I did not find in Polish forum help. I appeal to you to ask for help.

How to give UUID partition / dev/sda1?
How to change the TYPE partition / dev/sda1?

The partition / dev/sda1 UUID is not given.
The partition / dev/sda1 has erroneously given TYPE

```
BLKID: /dev/loop0: TYPE="squashfs"
/dev/sda1: TYPE="silicon_medley_raid_member"
/dev/sda5: UUID="8bec8143-c9ea-4d2d-80bb-478f8f22a3fe" TYPE="swap"
/dev/sdb1: LABEL="magazyn1" UUID="9fd1128b-0427-471e-97c8-45d11dc36353" TYPE="xfs"
```

and I want to do:
```
BLKID: /dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="a59826d3-c88c-4bb5-9feb-41540ff99720" TYPE="ext4"
/dev/sda5: UUID="8bec8143-c9ea-4d2d-80bb-478f8f22a3fe" TYPE="swap"
/dev/sdb1: LABEL="magazyn1" UUID="9fd1128b-0427-471e-97c8-45d11dc36353" TYPE="xfs"
```

More about the problem here: [http://ubuntu.pl/forum/viewtopic.php?f=127&t=150887&p=866400](http://ubuntu.pl/forum/viewtopic.php?f=127&t=150887&p=866400) (please use the translator)

---

### Post by seawolf167 on 2011-09-27
Do you have your drives set in a RAID array? Do you have a hardware RAID controller connecting your hard drives? Were the drives ever set in a RAID array?

If you don't have a RAID array setup, it could be caused because hard drives retain metadata and is thus causing the shown issue.

There is a post here you can try and see if it works ([see post #4]("http://ubuntuforums.org/showthread.php?t=1325650")). The first post [here ]("http://ubuntuforums.org/showthread.php?p=9274738#post9274738")has some additional information. Regardless of what you do, I highly recommend creating a backup image with [Clonezilla ]("http://www.clonezilla.org")before you start just in case something should happen.

---

### Post by baczko on 2011-09-27
I do not have RAID. Hardware RAID = no, Software RAID = no. I have not touched anything that is related to RAID. My problem is very similar to this: [https://bugzilla.redhat.com/show_bug.cgi?id=730502](https://bugzilla.redhat.com/show_bug.cgi?id=730502)

I run UbuntuLiveCD:
```
sudo dmraid -E -r /dev/sda1
no raid disks and with names /dev/sda1
```
```
sudo mount -t ext4 /dev/sda1 /media
```and I have access to this partition
```
ls /media
``` gives me /boot /etc /home etc...
For example, in /home/baczko all my files are still there.

Please look Boot Info Script log: [http://paste.ubuntu.com/696961/](http://paste.ubuntu.com/696961/)

> reiserfstune -u a59826d3-c88c-4bb5-9feb-41540ff99720 /dev/sda1 does not work.
I think first I need to set ext4.

Nobody knows how to do it? :-/

---

### Post by baczko on 2011-10-03
> ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda1

Disk /dev/sda1: 15.4 GB, 15414067200 bytes
255 heads, 63 sectors/track, 1873 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
[COLOR="Red"]Disk identifier: 0x00000000[/COLOR]

**Disk /dev/sda1 doesn't contain a valid partition table**

[[img]http://img546.imageshack.us/img546/7348/screenshotbdx.th.png[/img]](http://imageshack.us/photo/my-images/546/screenshotbdx.png/)

[[img]http://img64.imageshack.us/img64/8973/screenshot1fts.th.png[/img]](http://imageshack.us/photo/my-images/64/screenshot1fts.png/)

gparted log: [http://pastehtml.com/view/b9d362cjg.html](http://pastehtml.com/view/b9d362cjg.html)

```
ubuntu@ubuntu:~$ sudo hal-device |grep sda1 -A 9
  block.device = '/dev/sda1'  (string)
  block.major = 8  (0x8)  (int)
  block.minor = 1  (0x1)  (int)
  block.is_volume = true  (bool)
  volume.partition.start = 1048576  (0x100000)  (uint64)
  volume.num_blocks = 30105600  (0x1cb6000)  (uint64)
  volume.size = 15414067200  (0x396c00000)  (uint64)
  info.product = 'Volume (silicon_medley_raid_member)'  (string)
  volume.partition.media_size = 16139354112  (0x3c1fb0000)  (uint64)
  info.udi = '/org/freedesktop/Hal/devices/volume_part1_size_15414067200'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1f.1/host0/target0:0:0/0:0:0:0/block/sda/sda1'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_P_SSD1800_0208301025906'  (string)
  info.category = 'volume'  (string)
  info.capabilities = { 'volume', 'block' } (string list)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_P_SSD1800_0208301025906'  (string)
  volume.fstype = 'silicon_medley_raid_member'  (string)
  volume.fsusage = 'raid'  (string)
  volume.fsversion = '24941.26927'  (string)
  volume.uuid = ''  (string)
  volume.label = ''  (string)
```

---

### Post by baczko on 2011-10-04
So, time to format... :evil:

---

