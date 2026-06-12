---
title: "Not booting"
date: 2010-10-20
forum: General Help
---

### Post by Colo2 on 2010-10-20
Hello everyone

I turned my server on today and, the bios screen loads as usual, and when it goes to boot from the hd, it just hangs, it's as if it doesn't know what to boot from. I booted from a livecd, and managed to browse the hard drive with thunar. (file manager)

What do I need to do to make this hd bootable again?

Thanks


Tom

---

### Post by Colo2 on 2010-10-20
Please :(

I need a solution, there's about 300 GB worth of data on the drive, so I can't really format. Any way that I can repair it? maybe the MBR has a problem?

---

### Post by alexan on 2010-10-20
Try unplug everything but keyboard, mouse and monitor as hardware of your server (usb adaptors, printer etc)
While it "hangs", are you still able to [ctrl]+[alt]+[f1]?

---

### Post by Colo2 on 2010-10-20
> **alexan said:**
> Try unplug everything but keyboard, mouse and monitor as hardware of your server (usb adaptors, printer etc)
While it "hangs", are you still able to [ctrl]+[alt]+[f1]?


Hello

Thank you for your response

I tried that, and no, there was no command prompt which came up..

Just for some extra info. I have tried another drive, and it works fine, so I can rule out mobo/hardware problem

I've tried resetting the CMOS/BIOS with the pins on the mobo, and I've made sure in the BIOS that that hard drive (which is detected fine) is the one it's supposed to boot from..

Here is the hang:

[img]http://i55.tinypic.com/53v97s.jpg[/img]

The unreadable bit at the bottom says: 

> Verifying DMI pool data ......................

Thanks

---

### Post by cariboo on 2010-10-20
Boot from a Live Cd and see if you can access your data. Once you have backuped up your data, you should run the HDD manufactures diagnostic software on the drive to determine if what the problem is.

---

### Post by Colo2 on 2010-10-20
> **cariboo907 said:**
> Boot from a Live Cd and see if you can access your data. Once you have backuped up your data, you should run the HDD manufactures diagnostic software on the drive to determine if what the problem is.

Could this be a filesystem problem?

---

### Post by Colo2 on 2010-10-20
Hey

Just thought I'd post that I've fixed it.

Was a grub problem. Put in the ubuntu livecd, installed ubuntu along side the current one, and grub loaded on next boot, and was able to access the whole partition

Thanks guys

---

