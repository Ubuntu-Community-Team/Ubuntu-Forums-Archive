---
title: "Dual boot guide question"
date: 2010-12-16
forum: General Help
---

### Post by COKEDUDE on 2010-12-16
Is the picture in step 6 wrong? I thought there was a option to install side by side. 

[IMG]http://apcmag.com/images/howto/dualboot_ubuntu_vista_vista_first/ubuntu_install_05.png[/IMG]

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3)

---

### Post by pellgarlic on 2010-12-17
hi. that looks fine - the "use the largest continuous _free_ space" option is selected, so according to the disk space usage at the top of the screenshot, it will use the 36% free space left of the hard drive (the other 63% being used by vista).

the "100%" in the bottom bar graph just means that ubuntu will install everything it needs into one large partition within that free space. 

it is possible, using the "specify partitions manually" option, to split the free space into further multiple partitions, so you can have your "home" directory (like windows "my documents") on its own partition, as well as other directories, like "/boot", or a separate "data" partition if you want.

the easiest way is to start with one big partition, then as you learn more about linux, you'll develop your own preferences about what to put in different partitions or not. discussions about partition layouts for linux can get long and complicated... =P personally, i like a 3-partition layout - "/" ("root" - where the actual OS lives), "/home" and "/data". makes it easier to reinstall or change things later.

---

### Post by pellgarlic on 2010-12-17
sorry, i just noticed you have a few hundred "beans"... i guess you probably didn't need the "this is how linux works" lecture =P 

i'll leave it in place in case it helps anyone else searching for help with this though.

---

