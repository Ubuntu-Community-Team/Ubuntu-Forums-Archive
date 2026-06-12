---
title: "Can't install packages - 10.10 Live CD/USB"
date: 2011-02-19
forum: General Help
---

### Post by nxsfan on 2011-02-19
I need to copy the filesystem off a damaged drive. It boots up grub, but stalls at the initramfs. I can't fsck (believes another user is accessing the drive), I tried replacing the superblock with a backup, but it won't let me.

I can boot the live disk and run dd but eventually it hits an i/o error.

I uncomment /etc/apt/sources.list so i can install gddrescue.

```
sudo apt-get update
sudo apt-get install gddrescue
```

It gets to: ```
Unpacking gddrescue (from....
``` and then stalls indefinitely. Same for dd_rescue

This happens with the 10.10 desktop and 10.10 Netbook editions, on both CDs and USBs, created using unetbootin and the Universal USB tool.

What am I doing wrong? Why does it stall.....

Thanks for any help.

---

