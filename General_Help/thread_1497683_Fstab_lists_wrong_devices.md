---
title: "Fstab lists wrong devices"
date: 2010-05-30
forum: General Help
---

### Post by JustinR on 2010-05-30
Hi,

I didn't know where to post this so I'll post it here.

When I installed Ubuntu 10.04 around a month ago everything went smooth but whenever I try to plug in something like an external hard drive a pop-up says something along the lines of "/etc/mtab shows /dev/sdc1 *(my external device)* already mounted as /". Well I checked disk utility and /dev/sdb1 is mounted as /, not sdc1. I figured out that I could still mount /dev/sdc1 manually which was odd. I checked /etc/fstab and it showed my / partition as /dev/sdc1, when /dev/sdb1 is shown in Disk Utility. Well today I edited /etc/fstab from /dev/sdc1 / to /dev/sdb1 /. Rebooted and everything ***still*** worked fine, and now /dev/sdc1 mounts normally.

So I guess I don't have a problem but has anyone else experienced this? Should I file a bug report? I checked Google and no body else seems to have had this quirk. 

Any information on this? Thanks.

---

### Post by garvinrick4 on 2010-05-30
When you start using USB drives they get a mbr on them as lets say sdb and then you have some other usb device plugged in and it is sdb at that time so the USB drive with mbr that it is sdb is plugged in it will not work. If you plug the external drive with mbr on it first  and restart so it gets to be sdb instead of sdc all will work out. All external drives with grub loaded on them keep a tab on what it is. First USB attached is sdb second sdc third sdd. Have a nice day hope this helped a bit. I imagine you can screw around with them with
updating grub here and there but I like to keep my devices with installs and mbr's on them in a order.

---

### Post by dcstar on 2010-05-31
> **JustinR said:**
> Hi,

I didn't know where to post this so I'll post it here.

When I installed Ubuntu 10.04 around a month ago everything went smooth but whenever I try to plug in something like an external hard drive a pop-up says something along the lines of "/etc/mtab shows /dev/sdc1 *(my external device)* already mounted as /". Well I checked disk utility and /dev/sdb1 is mounted as /, not sdc1. I figured out that I could still mount /dev/sdc1 manually which was odd. I checked /etc/fstab and it showed my / partition as /dev/sdc1, when /dev/sdb1 is shown in Disk Utility. Well today I edited /etc/fstab from /dev/sdc1 / to /dev/sdb1 /. Rebooted and everything ***still*** worked fine, and now /dev/sdc1 mounts normally.
.......

/etc/fstab should **not** have any /etc/sdn entries, all internal mounts should be using UUIDS for exactly this reason.

---

