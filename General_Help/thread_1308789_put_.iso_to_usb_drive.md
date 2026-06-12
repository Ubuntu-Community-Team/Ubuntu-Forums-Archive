---
title: "put .iso to usb drive"
date: 2009-10-31
forum: General Help
---

### Post by MathUHenry on 2009-10-31
I want to be able to generically put an .iso image to a bootable usb. There is the option in Ubuntu to "USB Startup Disk Creator", but it won't work with any .iso except for Ubuntu live cd images.

Also, there is Acetoneiso which will extract an .iso to a file, and Image Writer which will put an .img onto the usb. But I can't find a way to consolidate the extracted files into an .img (or to directly convert from .iso to .img). Could someone help me fill in the gap somewhere. Thank you.

---

### Post by darco on 2009-10-31
Which OS are you trying to move to a usb drive?
Typically w/Windows, you would make the drive bootable, then mount the .iso in your current OS, then extract the files to the usb drive...then you should be able to boot from the usb drive.

darco

---

### Post by MathUHenry on 2009-11-05
I'm trying to do it generically. How do you make the flash drive bootable? I can extract the files to it, but I don't know how to make it boot.

---

### Post by bodhi.zazen on 2009-11-05
IMO the easiest way is to use unetbootin

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

It is in the ubuntu repositories, you can install it in windows as well.

---

### Post by flipper9 on 2009-11-05
> **bodhi.zazen said:**
> IMO the easiest way is to use unetbootin

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

It is in the ubuntu repositories, you can install it in windows as well.

Seconded.  

Sometimes, depending on your linux distribution and setup, the windows version of unetbootin works better running under wine with linux than the native linux version.  Sounds crazy, but I've found that to be the case a couple of times because the linux version had all kinds of weird dependencies I couldn't resolve.

---

### Post by loomsen on 2009-11-05
Hello.

Unetbootin doesnt work properly.

Easier to mount the iso, copy the files over to the stick you want to use, and finally use syslinux to make it bootable.

You should see a folder calles isolinux inside your ISO.
theres also a isolinux.cfg. this can simply be copied and renamed to syslinux.cfg.

Note, that your stick should contain a partition /dev/sdb4 (which is seen as drive C: by DOS based loaders, which applies to syslinux)

OK, so, quick ref:
Your stick contains a folder isolinux. Copy all the files to your usb devices root folder, and rename isolinux.cfg to syslinux.cfg.
Then run
```
syslinux /dev/sdb4
```

reboot and you should be able to run the live iso from your stick :)

---

### Post by bodhi.zazen on 2009-11-06
> **loomsen said:**
> Unetbootin doesnt work properly.

What problems are you having with unetbootin ?

I have personally tried many techniques and many commands to make a bootable USB from an iso and they all have pitfalls. Of all the techniques, IMO, unetbootin is the easiest for new users (it has a nice gui) and , again IMO, most likely to result in a bootable USB.

---

### Post by loomsen on 2009-11-08
> **bodhi.zazen said:**
> What problems are you having with unetbootin ?

I have personally tried many techniques and many commands to make a bootable USB from an iso and they all have pitfalls. Of all the techniques, IMO, unetbootin is the easiest for new users (it has a nice gui) and , again IMO, most likely to result in a bootable USB.

It didnt work properly for some distributions i tried. Probably because there are different FS used for the LiveCDs (like squashfs, casper, isolinux...)
I found it doesn't work properly for LiveCDs with DOS based loaders like isolinux.

---

### Post by bodhi.zazen on 2009-11-08
Thank you for the clarification.

Unetbootin works fine with all supported distros (there is a long list) and you can sometimes fool it to recognize distros not listed as well.

See : [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch#Recognition%20as%20an%20Ubuntu%20Remix](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch#Recognition%20as%20an%20Ubuntu%20Remix)

Of course this necessitates you re master the iso ...

---

