---
title: "Network adapter driver installation problems"
date: 2012-04-26
forum: General Help
---

### Post by iPwnd26 on 2012-04-26
Hi,

Firstly, sorry if this is in the wrong place!

I'm new to Ubuntu, and have recently obtained a network adapter so I can connect my PC that I built to the internet. However, I am having difficulty installing it. When I try to insert the driver, I receive the following error message:

```
insmod: error inserting '8192cu.ko': -1 Device or resource busy
```

I'm not sure how to go about resolving this. Could anybody help me?
Thanks!!

---

### Post by kc1di on 2012-04-26
> **iPwnd26 said:**
> Hi,

Firstly, sorry if this is in the wrong place!

I'm new to Ubuntu, and have recently obtained a network adapter so I can connect my PC that I built to the internet. However, I am having difficulty installing it. When I try to insert the driver, I receive the following error message:

```
insmod: error inserting '8192cu.ko': -1 Device or resource busy
```

I'm not sure how to go about resolving this. Could anybody help me?
Thanks!!
first of all give us some more information to help you with.
what is make and model of the network adapter your trying to install?  if you don't know go to a terminal and type the following code:
```
lspci
``` 
and post the printout of that command.
is this a wireless adapter or wired?
most wired adapters are recognized during install and setup automatically.  Wireless driver such as Broadcom require additional driver which may be available through the Additional Drivers tool found in the system settings menu.

---

### Post by iPwnd26 on 2012-04-26
Thanks for your quick reply.

The network adapter is a Realtek RTL8192CU, and it's wireless. I think it has recognised it to some extent, because whenever I log on it scans for wireless networks. It finds my network, but when I enter the password it spends a while trying to connect, and then asks for the password again; I presumed this was to do with the drivers, as I had not installed them.
And if it helps, I'm running Ubuntu 12.04 beta.

Thanks again!

---

### Post by kc1di on 2012-04-26
Realtek is a real pain to get going according to several reports.

but here's a page and another thread which may be of help to you.

In IMHO i'd get a different wireless card. 

but may be someone else has it running. 

[http://ubuntuforums.org/showthread.php?t=1902039]("http://ubuntuforums.org/showthread.php?t=1902039")

[http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/]("http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/")

Good Luck 
D :)

---

### Post by iPwnd26 on 2012-04-27
Hi kc1di,
Thanks for your response!

I followed the steps on the website you offered, but still ran into my problem...

```
Authentication requested [root] for remove driver:
ERROR: Module 8192cu does not exist in /proc/modules
Authentication requested [root] for insert driver:
insmod: error inserting '8192cu.ko': -1 Device or resource busy
```

It's still saying the device is busy. Do you know of any way I can get around this?
Thanks again!

---

### Post by techsupport on 2012-04-27
> **iPwnd26 said:**
> Hi kc1di,
Thanks for your response!

I followed the steps on the website you offered, but still ran into my problem...

```
Authentication requested [root] for remove driver:
ERROR: Module 8192cu does not exist in /proc/modules
Authentication requested [root] for insert driver:
insmod: error inserting '8192cu.ko': -1 Device or resource busy
```It's still saying the device is busy. Do you know of any way I can get around this?
Thanks again!

That is a semi-old used wifi adapter. When was the last time it worked properly?

---

### Post by iPwnd26 on 2012-04-27
Well I plugged it into a Windows machine, and it installed and was working fine, so it cannot be defective.
The device can find networks on my Ubuntu machine, it just can't connect to them.

---

### Post by iPwnd26 on 2012-04-28
Well, something must have worked, because it's now working!! Thanks everyone who helped me; not sure what it was that fixed it but I'm glad I can finally use the internet on it.

---

