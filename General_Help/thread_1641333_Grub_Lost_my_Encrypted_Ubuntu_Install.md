---
title: "Grub Lost my Encrypted Ubuntu Install"
date: 2010-12-08
forum: General Help
---

### Post by cyrxi on 2010-12-08
The background:
I have a multi-boot laptop that was working fine triple booting between an unencrypted install of Ubuntu 10.04, a "full-disk" encrypted version of Ubuntu 10.04, and Windows XP.  Everything was working beautifully until a recent set of updates on the unencrypted Ubuntu.  Now I can't log in to my encrypted install.

I have tried booting from the grub prompt, but can't seem to get anything to work.

I tried using the rescue operations on the alternative install CD to reinstall the GRUB boot loader, but it FAILED (exit code 1).

I have also used the rescue options to gain access to and execute a shell on my encrypted Ubuntu install.  I figured great, I'll just run update-grub but I get:
```
Generating grub.cfg ...
/usr/sbin/grub-probe: error: no mapping exists for 'encrypted-vg-root'.
```

So I tried 'grub-install /dev/sda':
```
/usr/sbin/grub-probe: error: no mapping exists for 'encrypted-vg-root'.
Auto-detection of a filesystem module failed.
Please specify the module with the option '--modules' explicitly
```

So I tried 'grub-install /dev/sda --modules=dm-crypt':
```
/usr/sbin/grub-probe: error: no mapping exists for 'encrypted-vg-root'.
/usr/sbin/grub-probe: error: no mapping exists for 'encrypted-vg-root'.
/usr/sbin/grub-probe: error: no mapping exists for 'encrypted-vg-root'.
You attempted a cross-disk install, but the filesystem containing /boot/grub does not suport UUIDs.
```

I've searched around and also tried a few other more creative things, but I am having zero luck.  I'm usually pretty good at troubleshooting my own issues, but I'm just stuck here.  Any help would be greatly appreciated.

---

