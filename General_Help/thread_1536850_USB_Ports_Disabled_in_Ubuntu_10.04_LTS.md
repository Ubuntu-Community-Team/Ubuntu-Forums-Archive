---
title: "USB Ports Disabled in Ubuntu 10.04 LTS"
date: 2010-07-22
forum: General Help
---

### Post by haydenh on 2010-07-22
I have Ubuntu Server 10.04 LTS installed. For some reason none of my USB ports work. My PS2 ports work however. Is there a bug in 10.04 that disable these ports? Is there a way to fix this issue?

Also, I've checked BIOS and they are enabled. Thanks in advance!

---

### Post by cariboo on 2010-07-23
What's the output of the following command when you plug in a usb device:

```
dmesg | tail -n10
```

Type the above command in a terminal and paste the output in your next post.

---

### Post by haydenh on 2010-07-25
> **cariboo907 said:**
> What's the output of the following command when you plug in a usb device:

```
dmesg | tail -n10
```Type the above command in a terminal and paste the output in your next post.

```

[    7.953786] type=1505 audit(1279839084.945:10):  operation="profile_load" pid=600 name="/usr/sbin/tcpdump"
[    8.898055] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[    8.898212] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   19.868023] eth0: no IPv6 routers present
[160424.517290] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[160424.523821] SGI XFS Quota Management subsystem
[160424.575539] JFS: nTxBlock = 8192, nTxLock = 65536
[160424.653317] NTFS driver 2.1.29 [Flags: R/O MODULE].
[160424.716489] QNX4 filesystem 0.2.3 registered.
[160424.831597] Btrfs loaded
```

---

### Post by ThomasHC on 2010-07-25
Are you sure they don't work, or maybe you have just forgotten to mount or configure the USB device?

---

### Post by haydenh on 2010-07-25
> **ThomasHC said:**
> Are you sure they don't work, or maybe you have just forgotten to mount or configure the USB device?

I am positive they don't work. I've tried a USB keyboard as well as a USB phone charger. Neither of which work.

---

### Post by punkerbruin on 2010-07-27
I have the same problem but I have ubuntu 10.04 installed for 2 months. The usb ports doesn't work since today(I have updated my pc today)

---

