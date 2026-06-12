---
title: "Doesn't boot from md"
date: 2010-02-13
forum: General Help
---

### Post by FiloSottile on 2010-02-13
I created three broken RAID 1 arrays with mdadm
```
mdadm --create ... /dev/md0 /dev/sdb1 missing
...
```
Saved the mdadm.conf
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE /dev/sda1 /dev/sdb1 /dev/sda2 /dev/sdb2 /dev/sda3 /dev/sdb3

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=46c87704:75be5bd3:adf78dfd:3b0fefb6
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=d7bb5abf:78c0b127:adf78dfd:3b0fefb6
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=ba9969ae:be26c114:adf78dfd:3b0fefb6

```
Then I copied all my data on them, setted up fstab
```
/dev/md2        /               ext3    relatime,errors=remount-ro 0       1
/dev/md0        /boot           ext2    relatime                   0       2
/dev/md1        /home           ext2    relatime                   0       2
/dev/sda4       none            swap    sw                         0       0
/dev/sdb4       none            swap    sw                         0       0

```
and grub/menu.lst
```
title		Ubuntu 9.10, kernel 2.6.31-19-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.31-19-generic root=/dev/md2 ro nodmraid quiet splash 
initrd		/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.31-19-generic root=/dev/md2 ro nodmraid  single
initrd		/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin

```

Now if i boot from liveCD, without any mdadm.conf, as it should be, and I run ```
mdadm -As
``` it creates my three broken arrays.

Now i want to boot from them, and then add other disk.
The BIOS loads the right GRUB, md seems to be charged, but it says that it can't find root device.
From the initram shell i see /dev/sdb1, 2 and 3 but if I run ```
mdadm -As
``` it says that no config or superblocks found...

I don't know what to do.

Thank you

P.S. I already boot the kernel with "nodmraid" parameter.

---

### Post by FiloSottile on 2010-02-13
Ah, right, you may need that...

```
root@ubuntu:/home/ubuntu# fdisk -l /dev/sdb

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93b893b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      104391   fd  Linux raid autodetect
/dev/sdb2            7978       30400   180112747+  fd  Linux raid autodetect
/dev/sdb3             145        7977    62918572+  fd  Linux raid autodetect
/dev/sdb4              14         144     1052257+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by FiloSottile on 2010-02-15
Created a lauchpad question:
[https://answers.launchpad.net/ubuntu/+source/mdadm/+question/101149](https://answers.launchpad.net/ubuntu/+source/mdadm/+question/101149)

> 
Doesn't boot from a new degraded RAID1 array

   1. Ubuntu
   2. “mdadm” package
   3. Questions
   4. Question #101149

I decided to put my system on a raid1 array with md.
So, I duplicated the partition table, setted partition types on fd, created the degraded array (with "missing" disk) and finally copied my data and installed grub.
Then I found bug #462258 where I discovered that Ubuntu doesn't boot from degraded array (strange, I said, here [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/120375/comments/145](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/120375/comments/145) I read that it should ask me what I want to do...), anyway, I've tried all:
* bootdegraded=true kernel parameter
* dpkg-reconfigure mdadm
* editing /etc/initramfs-tools/conf.d/mdadm with BOOT_DEGRADED=true and update-initramfs
None works. It always says me that it can't find /dev/md2 (the root) and drops to the busybox, where mdadm -As doesn't work.
If in busybox I look for conf/conf.d/mdadm BOOT_DEGRADED is always on false...

If I boot from a LiveCD and run mdadm -As all works without a problem.
I work on a FakeRAID chip, but i boot with nodmraid option, so it shouldn't be a problem.

On busybox raid1 module seems to be charged.
I can provide fast shoots of the boot process.

P.S. all changes that I made to get it working was done chrooting on the md array from LiveCD

Related bug: [Bug #462258: installer's boot-degraded debconf answer not written to installed disk]("https://bugs.launchpad.net/bugs/462258")

---

### Post by FiloSottile on 2010-02-15
A lot of informations on the web like bug #120375 and [https://wiki.ubuntu.com/BootDegradedRaid](https://wiki.ubuntu.com/BootDegradedRaid) are outdated.

See at the Karmic changelog [https://wiki.ubuntu.com/KarmicKoala/ReleaseNotes#Automatic%20boot%20from%20a%20degraded%20RAID%20array%20not%20configured%20upon%20installation](https://wiki.ubuntu.com/KarmicKoala/ReleaseNotes#Automatic%20boot%20from%20a%20degraded%20RAID%20array%20not%20configured%20upon%20installation) and the mdadm lucid version changelog:
--------------
mdadm (2.6.7.1-1ubuntu14) lucid; urgency=low

  * Fix boot_degraded handling during installation (LP: #462258):
    - Source /lib/preseed/preseed.sh in check.d/root_on_raid.
    - Change mdadm/boot_degraded default in templates file to match the
      apparently-intended behaviour (i.e. false), and stop overriding
      debconf preseeding if BOOT_DEGRADED is not already set in the
      initramfs configuration file.
--------------

I am suspecting that there is something in my kernel/initram/modules unrelated to degraded array that doesn't work. Any clue about how to discover what is missing?

------------------------

Interesting also [bug #259145]("https://bugs.launchpad.net/bugs/259145") and [https://wiki.ubuntu.com/ReliableRaid](https://wiki.ubuntu.com/ReliableRaid)

I will try editing mdadm.conf as in [bug #136252]("https://bugs.launchpad.net/bugs/136252") , but I don't hope that it works...

---

