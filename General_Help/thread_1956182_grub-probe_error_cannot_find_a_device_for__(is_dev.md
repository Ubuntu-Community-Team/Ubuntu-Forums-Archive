---
title: "grub-probe: error: cannot find a device for / (is /dev mounted?) Help please"
date: 2012-04-10
forum: General Help
---

### Post by Budisha on 2012-04-10
Hello, everyone.
Shortly, i have errors and im trying to install a package and i get an error:
(I used make folowing make install)
```

cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
Will now run update-grub to ensure grub will find the new initramfs ...
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
make: *** [install-modules] Error 1

```

After that i tried the following to confirm that grub-probe produces the error:
```

root@ubuntu:/home/ubuntu/compat-wireless-3.4-rc1-2# grub-probe /
grub-probe: error: cannot find a device for / (is /dev mounted?).

```

I have been messing with this the whole day. Tried reinstalling and everything.
What is strange is that when im booting from the USB i dont even get to grub. I get a blue window with the options Try Ubuntu, Install, Advanced settings, etc... I'm a ubuntu n00b, but im pretty sure that is called syslinux.
I thinki should also mention that when i'm tryng to openthe usb in the explorer, i get an error saying "Could not find "/cow"". I dont know if this is relevant but i thought i should mention it.

---

### Post by Budisha on 2012-04-11
Anyone please?

---

### Post by Budisha on 2012-04-14
Last bump.

---

### Post by gordintoronto on 2012-04-14
Are you running from USB or from the hard drive? What version of Ubuntu? What package are you trying to install? Where did you get it from?

If it's cryptsetup, why don't you install it from Software Center?

---

