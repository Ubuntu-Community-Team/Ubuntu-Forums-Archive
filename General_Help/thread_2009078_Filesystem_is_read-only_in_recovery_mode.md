---
title: "Filesystem is read-only in recovery mode?"
date: 2012-06-23
forum: General Help
---

### Post by asuastrophysics on 2012-06-23
Hi guys,

I just installed a fresh copy of Ubuntu 11.10, and when I went to install the latest proprietary NVIDIA drivers (295.59), all of my graphics stopped working. 

So, I booted into the recovery mode, trying to edit the blacklist.conf file. This can be found at /etc/modprobe.d/blacklist.conf

However, when I try to make any changes to the file at all, I get "Cannot write to file: Read-only Filesystem". Furthermore, I cannot write to any file at all, and thus cannot repair anything unless I boot into a livecd and chroot into the partition. 

Can someone explain why Ubuntu has a recovery mode if everything is read-only? Is my filesystem corrupt or is this how Recovery Mode is supposed to work?

---

### Post by steeldriver on 2012-06-23
just remount the root filesystem read-write - iirc there is a menu option to do that if you exit from the root shell, or you can type

```
mount -o remount,rw /
```at the console

---

### Post by Xero Xenith on 2012-07-18
Thanks, this worked. Why on earth would you want a read-only filesystem in recovery mode? It's ridiculous.

Any explanation as to why the recovery mode does not allow you to fix anything would be much appreciated.

---

