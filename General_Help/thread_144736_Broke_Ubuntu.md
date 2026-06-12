---
title: "Broke Ubuntu"
date: 2006-03-14
forum: General Help
---

### Post by kinghajj on 2006-03-14
I followed the instructions here [[http://www.tectonic.co.za/view.php?id=916]](http://www.tectonic.co.za/view.php?id=916]) in order to try to get Xgl/Compiz to work. Step one took forever but completed. When I tried step two, "compiz" couldn't be found, so I just installed xgl. Then I tried installing compiz, but if wanted to uninstall the linux kernel for some reason.... It said I was trying to get rid of the kernel I was using. I noticed that during step one a new kernel was installed, so I decided to reboot into that kernel. But for some reason it won't boot. When GRUB comes up and boots the kernel, all I get is a blank screen.

Help, please! Thanks.

---

### Post by kinghajj on 2006-03-15
help?

---

### Post by Ivan Matveich on 2006-03-16
...and try choosing one of the other kernels in the list that appears.

---

### Post by kinghajj on 2006-03-21
When I try booting either kernel 2.6.12-10-3 or 2.6.15-18-3, I get the message like "/dev/hdb1 does not exist! Dropping into shell." After this I get the BusyBox shell.

I tried running "sudo dpkg-reconfigure linux-image-2.6.15-18-3-368", which was suggested in a post I found online, but that has not helped.

---

### Post by TristanMike on 2006-03-21
If you are using Breezy, XGL does NOT work on it. It only works on Dapper, the next release of Ubuntu.

EDIT: oh, and fyi, the wiki for Dapper setup is [here](http://wiki.ubuntu.com/XglHowto)

---

### Post by kinghajj on 2006-03-21
[QUOTE=TristanMike]If you are using Breezy, XGL does NOT work on it. It only works on Dapper, the next release of Ubuntu.
[here](http://wiki.ubuntu.com/XglHowto)[/QUOTE]

That doesn't help me alot :( 

The page I went to gave instructions on upgrading Breezy to Dapper, so Xgl *should* work if I ever get it to boot again. I guess I could wait til June and upgrade from Dapper-alpha to Dapper-final... but I don't want to wait 3 months without linux!

---

