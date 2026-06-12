---
title: "NVIDIA GeForce 6150 card"
date: 2010-03-16
forum: General Help
---

### Post by pinenut on 2010-03-16
I have been using Fedora for many years, but I thought I would try Ubuntu. So, I installed Ubuntu 9.10 in a computer with Asus M2NPV-VM with an on-board nVidia GeForce 6150 graphic card. 

The installation was easy, but as soon as I tried to install the nVidia graphic card driver, I ran into trouble. I initially installed nVidia accelerated graphic driver (version 185) (recommended by Ubuntu). I could not type anything with Terminal or FireFox. I uninstalled it and installed version 96. With this driver, I was able to configure the nVidia x-server setting. But now I open Terminal and I can type anything. Neither can I with FireFox. My keyborad is no longer recognized. I am using Microsoft USB wireless receiver and wireless keyboard and mouse. 

Do you think it is too much trouble getting Ubuntu 9.10 to work with this nVidia graphic card?

---

### Post by dcstar on 2010-03-16
> **pinenut said:**
> I have been using Fedora for many years, but I thought I would try Ubuntu. So, I installed Ubuntu 9.10 in a computer with Asus M2NPV-VM with an on-board nVidia GeForce 6150 graphic card. 

The installation was easy, but as soon as I tried to install the nVidia graphic card driver, I ran into trouble. I initially installed nVidia accelerated graphic driver (version 185) (recommended by Ubuntu). I could not type anything with Terminal or FireFox. I uninstalled it and installed version 96. With this driver, I was able to configure the nVidia x-server setting. But now I open Terminal and I can type anything. Neither can I with FireFox. My keyborad is no longer recognized. I am using Microsoft USB wireless receiver and wireless keyboard and mouse. 

Do you think it is too much trouble getting Ubuntu 9.10 to work with this nVidia graphic card?

Exactly how did you install the driver?

---

### Post by bhencetotozo on 2010-03-16
Try this, I wish u luck. I hope it works for you too.

[http://www.nvnews.net/vbulletin/showthread.php?p=2209577]("http://www.nvnews.net/vbulletin/showthread.php?p=2209577")


1) download that beta driver (I use it on my Gforce 7950 gx2)
2) press ALT+CONTROL+F1,
3) sudo su
4) password
5) /etc/init.d/gdm stop
6) sh NVIDADRIVERFILE.run

IF step 6 fails, type ./  instead of sh

---

### Post by fragos on 2010-03-17
Try System-> Administration-> Hardware Drivers to install and select Nvidia drivers or any other proprietary drivers for that matter. Works every time for me.

---

### Post by pinenut on 2010-03-17
> **fragos said:**
> Try System-> Administration-> Hardware Drivers to install and select Nvidia drivers or any other proprietary drivers for that matter. Works every time for me.
Thank you for your input, but I had done the exactly the same thing as you suggested. But it didn't work for me.

---

### Post by pinenut on 2010-03-17
> **bhencetotozo said:**
> Try this, I wish u luck. I hope it works for you too.

[http://www.nvnews.net/vbulletin/showthread.php?p=2209577](http://www.nvnews.net/vbulletin/showthread.php?p=2209577)


1) download that beta driver (I use it on my Gforce 7950 gx2)
2) press ALT+CONTROL+F1,
3) sudo su
4) password
5) /etc/init.d/gdm stop
6) sh NVIDADRIVERFILE.run

IF step 6 fails, type ./  instead of sh

Thank you for your help. I found the newest driver from the nVidia web site, which is version 190.53. I ran into a problem installing it because '/etc/init.d/gdm stop' command failed to stop the x-server. I got another way of stopping it and will try it later.

Another method required me to start Ubuntu to the recovery mode and drop to a root prompt. I also had to issue 'telinit 3' command to go to the level 3 environment. 

I was finally able to install the driver, version 190.53. Having set the dual displays to the TwinView, everything is working fine. 

Looking back now, my problem may not have been the version of the driver itself. It is probably the way that I configured the driver. I could not properly configure the NVIDIA x server settings while running the NVIDIA driver.  I had to log on with the native x sever and then configure the nVidia settings. I wish that I had known this simple step which would saved me all the trouble installing and unintalling different versions of the display driver.

---

### Post by fragos on 2010-03-17
Does the resulting /etc/X11/xorg.conf call out "nvidia" as follows:

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
EndSection

---

