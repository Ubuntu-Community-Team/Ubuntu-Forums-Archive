---
title: "Udev mount USB drive via script"
date: 2009-07-06
forum: General Help
---

### Post by DeanLearner on 2009-07-06
Ubuntu 9.04 Desktop

I have a udev script that runs when a certain USB script (by checking the vendor and product id) is inserted. I have turned off the automatic gnome mounting facility via gconf-editor so it doesn't get in the way.

The /etc/udev/rules.d/55-woop.rules file
```
ACTION=="add", SUBSYSTEM=="usb", SYSFS{idVendor}=="0781", SYSFS{idProduct}=="5151", RUN+="/usr/local/bin/usb-backup %s{serial}"

```

As another check I send the usb drive serial number to the usb-backup script as well.

I know the script is being run when the usb drive is inserted but the sections relating to mounting the drive do not work. If I run the script as root/sudo it runs fine (if I run as a normal user, it complains that I have to be root).

The /usr/local/bin/usb-backup file (simplified version)
```

#! /bin/sh

mkdir /media/test
mount /dev/sdf /media/test


```

Now I've done some searching around and as far as I can tell udev runs its commands as root so that can't be the problem.... right?

Sorry I'm waffling... does anyone have any idea why the the above isn't mounting the drive? Or, where can I look for clues as to why it isnt working? (seen nothing in /var/log/messages and /var/log/syslog)

Ta! :)
-Chris

---

