---
title: "Software RAID1 drive and automatic mount issue"
date: 2010-12-18
forum: General Help
---

### Post by piotrpakos on 2010-12-18
Hi,

I have just setup a software RAID1 and it works OK but I am having a lot of trouble with getting it automatically mounted during boot. I've noticed that sometimes it's automatically mounted and sometimes it's not - it sits there asking me to press s to skip the mount process.

Any ideas why this happens?

This is my /etc/fstab file contents:

```
# <file system>                                 <mount point>   <type>  <options>               <dump>  <pass>
proc                                            /proc           proc    nodev,noexec,nosuid     0       0
UUID=cb00c785-3633-43c5-bebc-309d5447e139       /               ext4    errors=remount-ro       0       1
# swap was on /dev/sda5 during installation
UUID=363a8ea1-c3f4-4b38-9b73-a85963e5003c       none            swap    sw     0
        0
/dev/md0                                        /samba          ext4    defaults        0       2

```

and /etc/mdadm/mdadm.conf ends with:

```
ARRAY /dev/md0 level=raid1 num-devices=2 devices=/dev/sdb1,/dev/sdc1
```

Any advice greatly appreciated.

---

### Post by piotrpakos on 2010-12-20
I've noticed that if I replace "defaults" with "rw,auto,noexec,nouser,nobootwait" it boots fine and /dev/md0 is automatically mounted every time.

I'm wondering why.

---

