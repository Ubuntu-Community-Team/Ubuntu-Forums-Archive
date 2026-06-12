---
title: "Kernel log litterer with re-mount attempts"
date: 2011-12-17
forum: General Help
---

### Post by soulcheck on 2011-12-17
My boot times became a bit too much so i decided to take a look ad kernel log to see what might be causing the problem..

There i noticed repeating:

```


12/17/11 02:25:28 PM	EXT4-fs (sda6)	re-mounted. Opts: data=writeback,errors=remount-ro,commit=60,commit=600
12/17/11 02:25:29 PM	EXT4-fs (sda7)	re-mounted. Opts: data=writeback,errors=remount-ro,commit=60,commit=600
12/17/11 02:25:29 PM	EXT4-fs (sda2)	re-mounted. Opts: data=writeback,errors=remount-ro,commit=60,commit=600

```

and 

```


12/17/11 02:25:28 PM	EXT4-fs (sda6)	re-mounted. Opts: data=writeback,errors=remount-ro,commit=60,commit=0
12/17/11 02:25:29 PM	EXT4-fs (sda7)	re-mounted. Opts: data=writeback,errors=remount-ro,commit=60,commit=0
12/17/11 02:25:29 PM	EXT4-fs (sda2)	re-mounted. Opts: data=writeback,errors=remount-ro,commit=60,commit=0

```


New messages of this kind continue to appear after the system is up and running, which is strange as i got all the filesystems mounted. 

How to stop the remount attempts?

Some info.

My fstab:
```

#sda6
UUID=20fee089-ad39-4264-91f0-39aad7c84809 /               ext4    defaults,data=writeback,errors=remount-ro,commit=60,noatime 0       1
#sda7
UUID=b58528df-37fd-46c8-8160-d7dc0efc78cd /home           ext4    defaults,data=writeback,errors=remount-ro,commit=60,noatime 0       1
#sda2
UUID=ee463441-e841-40ab-b255-f14db4077b61 /media/stuff    ext4    defaults,data=writeback,errors=remount-ro,commit=60,noatime 0       1 

```

I'm on kubuntu oneiric, Linux 3.1.4-030104-generic x86_64 kernel.

Any help would be appreciated.

---

### Post by soulcheck on 2011-12-17
ok it looks like it's remounting when my laptop goes to battery power (found out [here]("http://askubuntu.com/questions/32960/ext34-commit-option-and-filesystem-integrity")). How do i disable this functionality?

---

