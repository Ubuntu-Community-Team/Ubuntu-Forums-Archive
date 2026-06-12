---
title: "Can no longer mount eSata external HDD"
date: 2010-12-02
forum: General Help
---

### Post by majoob on 2010-12-02
I have an external eSATA hard drive that has been working fine for months for backing up (I had been rsync'ing to it every night). For my configuration, see [http://ubuntuforums.org/showthread.php?t=1362201](http://ubuntuforums.org/showthread.php?t=1362201)

I can no longer mount the drive with eSATA (doesn't even recognize it). It was mounted on /dev/sdb1. The drive also has a USB ... I tried that and it mounts fine.

So, my data is ok, but I want to resume nightly backups (via eSATA).

Thoughts?

Here is some output:

fstab (2 lines below 'cause I swap HDD's between my dock and offsite storage):
```
proc            /proc           proc    defaults        0       0
UUID=228d6ffc-c50e-425d-a768-fcb9c22d8383 /               ext3    relatime,errors=remount-ro 0       1
UUID=aa75b03b-5037-4b0b-b73b-0c1f017c89dd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=f13cde43-eec0-40dc-8418-0f41fb549073 /media/backup ext3 user,relatime,noexec 0 2
UUID=511b4a1c-cb54-488d-a737-c41cc14087be /media/backup ext3 user,relatime,noexec 0 2
```

fdisk -l:
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000eb078

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      120378   966936253+  83  Linux
/dev/sda2          120379      121601     9823747+   5  Extended
/dev/sda5          120379      121601     9823716   82  Linux swap / Solaris

```

mount:
```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/matt/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=matt)

```

---

### Post by majoob on 2010-12-03
Anyone?

---

### Post by Mosabama on 2010-12-03
did you check dmesg ?

---

### Post by majoob on 2010-12-03
I'm not sure what to look for in dmesg. Should I post it's output?

---

### Post by Mosabama on 2010-12-03
yeah ... plug the esata, then dmesg and post the last 10 lines.

---

### Post by majoob on 2010-12-03
Here are the last few lines from dmesg after re-plugging in eSATA.

```
[   25.387398] CPU1 attaching NULL sched-domain.
[   25.400123] CPU0 attaching sched-domain:
[   25.400126]  domain 0: span 0-1 level MC
[   25.400129]   groups: 0 1
[   25.400134] CPU1 attaching sched-domain:
[   25.400136]  domain 0: span 0-1 level MC
[   25.400138]   groups: 1 0
[   25.872458] usb 8-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   31.068034] eth1: no IPv6 routers present
[49327.603812] lo: Disabled Privacy Extensions
[60900.240466] lo: Disabled Privacy Extensions
[65083.901295] usblp0: removed

```

---

### Post by Mosabama on 2010-12-03
There is nothing about eSATA here, its not detected at all!!
Have you tried changing the cable?
maybe its the eSATA cable or port not working any more.

but from this I can say that its not a driver issue.. I dont think there is anything wrong with linux handling it.

---

### Post by majoob on 2010-12-03
Ok. I'll look at the cable and ports. BTW, my eSATA card is nothing more than two ports on a plate, with short SATA cables connecting to two internal SATA ports on my Mobo.

---

### Post by dcstar on 2010-12-04
> **Mosabama said:**
> There is nothing about eSATA here, its not detected at all!!
Have you tried changing the cable?
maybe its the eSATA cable or port not working any more.

but from this I can say that its not a driver issue.. I dont think there is anything wrong with linux handling it.

eSATA is **not** a hotplug system that is detected the same as USB.

If you want to have eSATA resources available **after** you have booted a system then do the following after connecting the drive:

```
sudo partprobe
sudo mount /dev/whatever-the-eSATA-partition-is
```

---

### Post by majoob on 2010-12-04
Thanks dcstar.
Yeah, back when the drive was working I had to either reboot or use the mount command.

When I do this:
```
sudo partprobe
sudo mount /media/backup
```

I get:
```
mount: special device UUID=f13cde43-eec0-40dc-8418-0f41fb549073 does not exist
```

(I still need to check the cables and ports.)

---

### Post by dcstar on 2012-09-08
Ancient thread notes:

Hotplug only works with AHCI set in your BIOS. If you BIOS resets back to IDE emulation then no more hotplug.

Also eSATA automounting is currently broken in 12.04:

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/153768](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/153768)

---

### Post by wildmanne39 on 2012-09-09
Thanks for sharing. Thread Closed.

---

