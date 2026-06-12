---
title: "xubuntu and Belkin F1DA108T"
date: 2009-08-06
forum: General Help
---

### Post by LinuxGold on 2009-08-06
I am running ubuntu-server 9.04 with xubuntu-desktop installed.

I am also using [Belkin F1DA108T KVM]("http://www.belkin.com/support/product/?lid=en&pid=F1DA108T&scid=1114") to administer my 4 servers (3 Windows servers).

Since my ubuntu server use only ONE usb port, I had to switch from USB to PS2 for both keyboard and mouse on ubuntu server ONLY, all 3 other servers use USB ports.  I need that USB port for other device (APC backup).

Now, after the switch, the keyboard works great but not mouse.  When I slightly move it, it went overboard, hitting the edge so hard that it breaks out of monitor.  I tried to reconfigure the xorg using the command:

```

sudo dpkg-reconfigure xserver-xorg

```

It didn't get my mouse fixed.  How do I get around to it?

Many thanks,


Scott

---

