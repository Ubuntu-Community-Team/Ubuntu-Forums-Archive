---
title: "Filesystem locked after using chmod command on Maverick, can't boot."
date: 2012-02-12
forum: General Help
---

### Post by Blake. on 2012-02-12
Hello everyone, I'm having a major problem and would really appreciate some assistance.

You see, I was trying to set up a usb controller on Ubuntu 10.10 using this guide: [http://linuxgamingtoday.wordpress.com/2008/01/24/install-and-use-usb-based-gamepads-in-ubuntu/](http://linuxgamingtoday.wordpress.com/2008/01/24/install-and-use-usb-based-gamepads-in-ubuntu/)

However, when I ran this command: 
```
sudo chmod 666 /dev/input/js0

```The entire computer started freaking out. It started throwing error messages about programs no longer funtioning, and all the icons went to the default GNOME theme and looked really pixelated. So at the moment, I simply rebooted my computer. However, it will no longer boot, and the filesystem will not mount in other OS'es. GParted says it can't mount the filesystem because it is locked.

I would like to be able to get the OS to boot again, but at the very least I need to be able to mount the filesystem in another OS so I can back up everything under my /home directory to an external hard drive. Any suggestions?

---

