---
title: "Cannot boot. partition problem? raid problem?"
date: 2009-10-12
forum: General Help
---

### Post by kktm on 2009-10-12
Hello,

I cannot boot. After grub it sais 
```
mount: mounting /dev/disk/by-uuid/[...] on /root failed: Invalid argument
```

I'm on a pretty fresh installed Karmic Koala (but it's probably not related to beta, I had similar problems on debian etch and lenny before)

My partition scheme is as follows:
```
sda: 300 Gb
sda1: 49 Gb (root partition)
sda2: 250 Gb (/dev/md0)
sda3: swap

sdb: 500 Gb
sdb1: 250 Gb (/dev/md0)
sdb2: 250 Gb (/home)

```

My problem is probably related to raid, because to mount /dev/sda1 in busybox I have to first "mdadm --stop /dev/md1" the funny thing is: I know nothing about an md1. But it shows me this device in /etc/mdadm.conf, it detects it when booting into a rescue system from the installation cd and shows it in /etc/mdadm.conf in the busybox after grub...

Furthermore, I have to reread the partitiontable (sfdisk -R) before I see the partitions on /dev/sda when booting to a rescue system.

Before reassembling the md-array, I could this system. So for the moment I would be very happy to know at least how to prevent grub from starting that device...

---

### Post by kktm on 2009-10-12
Okay, managed to get a running system again.

I had to stop md1, mount and chroot my root partition and edit /etc/mdadm/mdadm.conf to not contain the inexistent md1 any more and recreate my initrd.

```

$ mdadm --stop /dev/md1
$ mount /dev/sda1 /root
$ mount -o bind /dev /root/dev
$ mount -t proc none /root/proc
$ chroot /root /bin/bash
$ vim /etc/mdadm/mdadm.conf
[...]
$ dpkg-reconfigure linux-image-`uname -r`

```

Now the system is booting again, but still, the md-array needs to be recreated manually (or let's call it semi-automatic :) ), but another raid shows up:

```

$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d0 : inactive sdb1[1](S)
      243224000 blocks

```

to get the system like I want it I have to:
```

$ mdadm --stop /dev/md_d0
$ mdadm --auto-detect

```

after that my raid shows up as I want it:
```

$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[1] sda2[0]
      243224000 blocks [2/2] [UU]

```

I'm confused. Can anybody explain me what's going on here???

---

