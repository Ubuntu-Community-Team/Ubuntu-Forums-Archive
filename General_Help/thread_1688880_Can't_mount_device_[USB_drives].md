---
title: "Can't mount device [USB drives]"
date: 2011-02-15
forum: General Help
---

### Post by MiguelLuna on 2011-02-15
Hello to everyone! ):P

Two days ago, my HDD died  ](*,) (actually, I killed it), and I decided to use Ubuntu as my primary OS, installed on a USB Drive. It's not a Live USB. Even that I know Ubuntu since 7.10, I'm still a newbbie. Anyways, today, when I tried to connect a new USB Drive, apart from the one where the OS is, it didn't show up on the Desktop nor the Computer window. I tried to mount it by using the disk utility, but it gives the following error:

Error mounting: mount exited with exit code 1: helper failed with:
> mount: according to mtab, /dev/sda1 is already mounted on /
mount failedThen I tried in Terminal, by changing to root:
> sudo -sand then with:

>  mount -w /dev/sda1 /media/usbit says /media/usb is not a mountig device or something like that, I tried again but without the>  /usb part, and it mounted to the Media folder.

If I get it out and in again, and try to mount it with Disk Utility, it gives the error
> Can't mount, not enought space on deviceThe device is empty.

Thanks in advance to everyone.

Miguel

---

### Post by MiguelLuna on 2011-02-15
> I just discovered that my CD Drive doesn't work too! It's a matshita uj-850s. :S Everything worked fine when it was a Live USB =/

It does work, just a faulty CD

---

