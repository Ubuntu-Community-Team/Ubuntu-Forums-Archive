---
title: "Downgrading Ubuntu 12.04 64-bit to 32-bit"
date: 2012-09-27
forum: General Help
---

### Post by mioimnida02 on 2012-09-27
Good Day! I installed Ubuntu 12.04 through WUBI by which installation's default was 64-bit. Is there any way to downgrade from 64-bit to 32-bit without re-installing?

Here are my reasons for downgrading:

1. I am using a single core CPU @1.60 Ghz. I am afraid that when the time 12.10 come out. I won't be able to upgrade.

2. Netbook only supports 2GB of RAM. 64-bit machines are memory as well as CPU hogs. 12.04 drains my RAM so fast.

3. Intel GMA 3600 was not supported in 64-bit machines but is supported in 32-bit machines.

Thanks for you help!

---

### Post by snotplop on 2012-09-27
Allo and welcome to the community!

While it is *theoretically* possible to change an installation from 64-bit libs and binaries to their 32-bit equivalents though some significant trials and tribulations, most of the time it's just not worth the hassle - and believe me, I have tried :)

It's usually a lot faster and easier to just reinstall the system from scratch.

Not sure how far you can get with Wubi's containers, but here's how I've always done it:

When you boot into the 32-bit live[cd|usb] simply mount your existing Ubuntu installation drive and remove everything in the drive *except* the home folder (eg, /etc/home/).

Unmount the drive and install Ubuntu as normal, paying special attention to maintain the exact same partitioning/mountpoint scheme and ensure you are not formatting the partition that contains your home directories.

When it comes back up, you'll be amazed how preserved your home environment is - even down to the tabs you still had open when Firefox crashed right before you nuked the old system :)

Hope this helps,
-Andy

---

### Post by JRV on 2012-09-27
Also Atom processors do not support the PAE kernel.
You will need to install from the netboot Non-PAE disk.

---

### Post by JRV on 2012-09-27
The Non-PAE netboot disk is located here:

[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/)

---

### Post by mioimnida02 on 2012-09-30
Thank you guys for replying :). I think I would just wait for 12.10 if my netbook can handle it before doing anything :).

---

