---
title: "Kernel Panic unable to mount root"
date: 2010-05-03
forum: General Help
---

### Post by desertboy on 2010-05-03
Fresh install on an acer touchscreen

[http://us.acer.com/acer/productv.do?LanguageISOCtxParam=en&kcond61e.c2att101=68796&sp=page16e&ctx2.c2att1=25&link=ln438e&CountryISOCtxParam=US&ctx1g.c2att92=450&ctx1.att21k=1&CRC=3691807100](http://us.acer.com/acer/productv.do?LanguageISOCtxParam=en&kcond61e.c2att101=68796&sp=page16e&ctx2.c2att1=25&link=ln438e&CountryISOCtxParam=US&ctx1g.c2att92=450&ctx1.att21k=1&CRC=3691807100)

boots livecd fine selected to replace entire disk now presented with vfs error after install and reboot. This is a full replace install taking all the disk not a wubi install. Please help I don't want to have to reinstall windows 7 (PC has worked sweet as for 4 weeks with windows 7 just need to get back to ubuntu again.)

Posting from said computer from the livecd as we speak.

---

### Post by gzarkadas on 2010-05-03
Does the disk utility (or gparted, if you prefer) shows your partition ok?

What is the error message presented by the kernel? You can also check your /var/log/kern.log to see where the kernel stopped and what was doing just before it panicked.

Also is your /etc/fstab correct? Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1446383"), it may be of help.

---

