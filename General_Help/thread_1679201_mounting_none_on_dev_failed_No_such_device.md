---
title: "mounting none on /dev failed: No such device"
date: 2011-01-31
forum: General Help
---

### Post by mathiaho on 2011-01-31
Hi

I'm running Lucid with the 2.6.32-28-generic and 2.6.31-11-rt(abogani's ppa) kernels, on a fairly new laptop.

When I boot the rt-kernel, right after grub I get a message:

```
mount: mounting none on /dev failed: no such device
W: devtmpfs not available, falling back to tmpfs for /dev
```Then after a few seconds, I see a lot of fast moving text and then Ubuntu starts just fine.

when booting the generic kernel, I don't see any text at all, but it uses just as long time as the rt-kernel, so I guess the problem affects both.

Any ideas what this is about?

Thanks

---

### Post by matt_symes on 2011-01-31
Hi

Open a terminal and type

```
cat /etc/fstab
```

Post the result back here

Kind regards

---

### Post by mathiaho on 2011-02-03
Hey, sorry for my late answer.

> 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=65725cf4-1171-475d-909a-563c93c229ab /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=704f6f2b-d003-421c-bce2-11c54f11e675 none            swap    sw              0       0

Thanks

---

### Post by mathiaho on 2011-02-06
Any ideas?

---

### Post by matt_symes on 2011-02-06
Hi

Your fstab looks fine. Have a read of this.

[http://ubuntuforums.org/showthread.php?t=1435968](http://ubuntuforums.org/showthread.php?t=1435968)

Kind regards

---

### Post by mathiaho on 2011-02-07
Thank you! Strangely I didn't find that thread when searching the forum before posting this one...

---

