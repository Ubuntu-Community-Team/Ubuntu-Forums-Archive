---
title: "Unetbootin installation: Incorrect fstab"
date: 2011-03-26
forum: General Help
---

### Post by del_diablo on 2011-03-26
I found this on the bugtracker: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/574009](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/574009)
It seems more or less identical to my problem.

I have a desktop, and a HD driver connected via external USB cables.
I used to run Debian, until grub2 decided gave me errors about placement. Fatal and easly fixable errors.
I downloaded unetbootin, and threw in a 16GB usb penn, and then threw over Ubuntu to the pen.
I then installed, and the installation went smoothly. Did manual partition setup.
I got a fatal IO error on shutdown related to what I assume was the USB pen, and then restarted.
On restart GRUB worked, partition select worked, BUT I was unable to mount the root partition, to what I assume was due incorrect UUIDS during installation.
I then got dropped into busybox, and the exit command did not work either.
Fixing this issue is trivial: Use the liveinstall on the usbpenn and run gedit over the fstab and set it up properly.
HOWEVER, that would be a workaround, a rather ugly one too.
So I ask: Can some of you people PLEASE submit "confirmed" to the bugtracker, so the issues get fixed?

---

### Post by del_diablo on 2011-03-26
Solved via adding rootdelay=90 to grub cmd options......
Apparently lack of sane defaults :(

---

