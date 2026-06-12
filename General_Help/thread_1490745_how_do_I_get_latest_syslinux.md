---
title: "how do I get latest syslinux?"
date: 2010-05-22
forum: General Help
---

### Post by pizza-is-good on 2010-05-22
I have tried to get a parted magic usb working. After trying and failing with unetbootin several times, I found [this page]("http://partedmagic.com/documentation/130-creating-the-liveusb.html") that says that the syslinux in ubuntu is way outdated, and that it won't work withou the latest one.
So I went to synaptic, and found that I'm running syslinux 2:3.63+dfsg-2ubuntu3, and it says that it is the latest version.
I then went [here]("http://syslinux.zytor.com/wiki/index.php/The_Syslinux_Project"), the official syslinux project site, and found out that the latest syslinux is 3.86.

How do I install the latest syslinux on my ubuntu machine?
I'm running 10.04 64-bit.

Thanks,

~pizza

---

### Post by C.S.Cameron on 2010-05-22
The grub2 method described on this page worked for me.

[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

see also

[http://ubuntuforums.org/showthread.php?t=1451184&highlight=unetbootin&page=2](http://ubuntuforums.org/showthread.php?t=1451184&highlight=unetbootin&page=2)

---

### Post by pizza-is-good on 2010-05-22
Thanks.

I gave unetbootin another try. This time I did not select the latest parted magic, and now it worked.

The thread isn't really solved, I still don't have the latest syslinux, but at least I got what I wanted working to work.
If anyone knows how to upgrade syslinux, I'm still interested, so I can use the latest parted magic.

~pizza

---

### Post by motsteve on 2010-08-18
Try: [http://www.kernel.org/pub/linux/utils/boot/syslinux/](http://www.kernel.org/pub/linux/utils/boot/syslinux/)

---

