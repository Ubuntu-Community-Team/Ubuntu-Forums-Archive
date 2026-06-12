---
title: "Need help, extremely urgent"
date: 2010-12-03
forum: General Help
---

### Post by alababi on 2010-12-03
I just used Gparted to resize a NTFS partition to install Natty Narwhal but a problem happened. Something weird appear and then I cannot boot ubuntu again. This is the screenshot when I used the boot CD
[IMG]http://img600.imageshack.us/img600/7619/screenshot1lj.png[/IMG]

Luckily, I'm still able to boot Windows 7 but Windows 7 didnt recognize this partition, here is the screenshot
[IMG]http://img256.imageshack.us/img256/8992/help0.png[/IMG]

So how can get everything back, or at least, be able to access to the partition to backup the data and do a clean install?

---

### Post by nolag on 2010-12-03
You won't likely be able to access the data on that partition.  It is odd that you can't boot to ubuntu, does grub2 load or did you restore to boot to windows?  If grub does not load, reinstall it.  If it does try to reformat that partition then boot to ubuntu.  If you want to backup the ubuntu drive you can google ext3 on windows and you will see free software for that.

---

