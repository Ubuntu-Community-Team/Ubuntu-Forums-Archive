---
title: "problems with WIFI on Lenovo S12 in Ubuntu 10.04 LTS"
date: 2011-12-15
forum: General Help
---

### Post by strnad on 2011-12-15
Good Morning,

I have a problem to turn on my WiFi on Lenovo S12 in Ubuntu 10.04 LTS.

When I look at the network manager I can only see that Wireless Network is disabled. All of my drivers are up to date. Of course, hw switches are on.

WiFi already worked but when I upgraded to 10.04 it suddenly stopped.

Can you please help?

Thanks

Peter

---

### Post by lechien73 on 2011-12-15
Are you using the proprietary drivers?

I did remember something about the WMI module of the Lenovo S12 being mis-identified as an Acer. You could try opening a terminal window and typing:

```
sudo rmmod acer_wmi && echo "blacklist acer_wmi" >> /etc/modprobe.d/blacklist.conf

```

Then reboot. Hope that helps! You may have to connect it to the Internet with an ethernet cable, and download the proprietary drivers though, if they're not already installed.

---

### Post by strnad on 2011-12-15
Hello lechien,

thanks for the help but when I entered the code you suggested I have got this reply:

ERROR: Module acer_wmi does not exist in /proc/modules

So it must be something else.

Thanks

Peter

---

### Post by lechien73 on 2011-12-15
Ok...could you try going to **System -> Administration -> Hardware Drivers**, please. Does it mention anything about drivers for your Broadcom card there, and whether they're in use or not? If they're not in use, then you'll need to connect to the Internet with a wired connection to activate them.

---

### Post by strnad on 2011-12-16
Hi Matt,

that is what confuses me the most. I have installed those proprietary drivers as a first thing.

When I do what you told me to I have this drivers turned on:

Broadcom STA Wireless driver
These package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware.

The wifi worked well without any problems. I had 10.10 and I could connect to anything.

Then I rolled back to 10.04 LTS and it stopped working.

I tried to run 10.10. from my USB to see whether it could help. But when I tried to install drivers it failed.
Thanks

Peter

---

### Post by strnad on 2011-12-16
Hi Matt,

I don't know what happened. I turned on my PC and suddenly it works. Maybe the code you have reccomended somehow blocked those bad things that didn't allow my WiFi to work properly.

But it's true that I have updated Ubuntu yesterday, so that might also have helped.

Nevertheless, all seems to work fine and I would like to thank you for your help.

Peter

---

### Post by lechien73 on 2011-12-16
You're very welcome...I'm glad it's working, these issues can be frustrating and time-consuming.

Please could you mark the issue as [SOLVED] using the **Thread Tools** menu if you get chance?

Thanks

---

