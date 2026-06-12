---
title: "How To Disable Modem-Manager?"
date: 2009-12-15
forum: General Help
---

### Post by crokett on 2009-12-15
I have Ubuntu v9.1 and it hangs at boot while starting modem-manager and loading various modem drivers.  This is a desktop with no modem installed. I want to disable it. I can't boot the machine to either regular or rescue mode, it hangs either way.  I am currently booted to a 9.04 install CD with my Linux partition mounted.  I looked through /etc/ini.d but don't see anything there.  Google turned up a few hits on unistalling the package but I can't boot the machine to remove the package.

---

### Post by philinux on 2009-12-15
> **crokett said:**
> I have Ubuntu v9.1 and it hangs at boot while starting modem-manager and loading various modem drivers.  This is a desktop with no modem installed. I want to disable it. I can't boot the machine to either regular or rescue mode, it hangs either way.  I am currently booted to a 9.04 install CD with my Linux partition mounted.  I looked through /etc/ini.d but don't see anything there.  Google turned up a few hits on unistalling the package but I can't boot the machine to remove the package.

It for mobile broadband. However.

You'll have to chroot in from the livecd and remove modemmanger that way.

```
apt-get purge modemmanager 
```

Once you got chrooted in.

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

This link shows how to establish a chroot.

---

### Post by crokett on 2009-12-15
Ok, that sort of worked.  Now it doesn't load modem manager but it still hangs.  It says
 ```

fsck from util-linux-ng 2.16
init: procps main process (355) terminated with status 255
/dev/sdb5 clean, 197434 files, 366782 blocks 

```

I did some searching and booted to the live cd and tried fsck from there.  It came back clean. Any more ideas?

---

