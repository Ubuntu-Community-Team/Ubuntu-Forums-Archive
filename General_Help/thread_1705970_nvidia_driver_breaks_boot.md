---
title: "nvidia driver breaks boot"
date: 2011-03-13
forum: General Help
---

### Post by RainerZA on 2011-03-13
I have recently installed ubuntu desktop i386 10.10 on my laptop (Saony vaio VPCF137HG) as a dual boot. When it first started it worked perfectly, but when I installed the nvidia driver (For a nvidia Geforce 425M GPU) it came to the purple screen ([Pic of screen]("http://s2.i1.picplzthumbs.com/upload/img/0b/93/93/0b9393c46ec6d0c4118ff0a8d8026b6006676b99_wmlg.jpg")) and no further. It doesn't respond to any commands and would not go any further, even after 40 mins! can anybody please help me?

---

### Post by Krytarik on 2011-03-13
First, boot into "recovery mode", if you don't see a boot menu normally, press SHIFT to make it appear, then choose "root shell promp".

Then, in either case, rename/remove "/etc/X11/xorg.conf". This should revert to the previously running driver. Reboot.

If you installed the driver manually with the installer from Nvidia's website, remove it by following its instructions.

I recommend installing the proprietary driver via "System -> Administration -> Additional Drivers".

If you have done so already, try upgrading to the driver provided by Ubuntu-X-Swat's PPA, they offer the most recent packaged version of the proprietary driver:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by RainerZA on 2011-03-13
How do I remove that file, when I'm in the prompt it doesn't allow me to use barrwords like xorg or conf so how am i to remove or rename the file? and the driver that's giving my trouble was a proprietary driver.
thanks

---

### Post by Krytarik on 2011-03-13
So, you did manage it in the meanwhile? (Since your thread is marked as "solved" now.)

---

