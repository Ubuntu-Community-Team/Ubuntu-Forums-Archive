---
title: "Safe Mode only???"
date: 2010-11-08
forum: General Help
---

### Post by Nickjpost on 2010-11-08
Hello, all. I'm new to Ubuntu and just installed Ubuntu 10.10 on my Toshiba laptop after my winxp os crashed and became corrupt. When I installed Ubuntu, it gave me an option to install 3rd party drivers. I installed the modem driver. When I booted my computer this morning and logged onto the Desktop Environment, the GUI did not appear, but managed to have access in Safe mode. I wanted to test removing that driver but when I try to remove, it says I am not authorized. Should I use the Starup disk utulity to reinstall? Is there a way to remove it form the command line? Any suggestions welcome and appreciated...please note that I am fairly new with Linux OS.
 
Thank you for your support!
Nick

---

### Post by Hippytaff on 2010-11-08
Are you sure the driver is the problem? if you want to remove it you need to do it as root, which from the command line, means you put sudo infront of the command.
 
You might also find reading the modprobe manual page useful. Modprobe is the command for installing drivers. From the terminal type
```

man modprobe

```
If your having boot problems it might be worth running the script here - [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) and posting the output (which should appear on your desktop as Results.txt). people might be able to help you diagnose the problem.

---

### Post by Nickjpost on 2010-11-08
Thanks Hippytaff for your reply.
I'm not positive that it is the problem, but it is not a driver that Ubuntu supports, so I wanted to try to remove it and see what happens. When I try to remove that driver, I recieve an error stating that I am not authorised. I will, however, look into the man page for modprobe. Thanks again!

---

### Post by Hippytaff on 2010-11-08
Out of interest what driver is it for what device?

---

### Post by Nickjpost on 2010-11-08
It is labeled "Software modem", Smartlink modem daemon. I have created a bootable usb in safe mode, would I be able to reinstall the OS using that? I don't have anything I'm worried about loosing.

---

### Post by Hippytaff on 2010-11-08
If you can boot from the usb, you should be able to reinstall ubuntu from it if your happy to do that :-)

---

### Post by Nickjpost on 2010-11-08
Ok, I'm going to try that...I really appreciate your help! :)

---

