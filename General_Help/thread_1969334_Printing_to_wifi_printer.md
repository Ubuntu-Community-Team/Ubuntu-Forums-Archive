---
title: "Printing to wifi printer"
date: 2012-04-29
forum: General Help
---

### Post by crutch145 on 2012-04-29
I have a wifi Brother MFC-J425W printer that has a 192.168.x.x address.  I can successfully print to it when connected from a Windows PC.  When I am using Ubuntu 12.04, it found the printer via the Network Printer search.  It also installed the J425W CUPS driver.  However, when clicking on Print, it doesn't show anything in the Print Queue, but nothing ever prints... it just goes into limbo.  

Where can I start my troubleshooting?  

Thanks,

Justin

---

### Post by Lemuriano on 2012-04-29
Hi,

Did it work while connected through usb using Ubuntu?

Regards.

---

### Post by CharlesA on 2012-04-29
> **Lemuriano said:**
> Hi,

Did it work while connected through usb using Ubuntu?

Regards.
I would try this first.

I've been printing to an HP officejet over wifi from by 10.04 box with no problems. The CUPS driver should work fine.

Does the same thing happen if you hook up the printer via wired instead of wireless?

---

### Post by crutch145 on 2012-04-30
Thanks for the suggestion to try wired.  Strangely enough, it still does not work via USB connection.  So I guess troubleshooting wifi connection is moot.  Perhaps because this is the newest version of Ubuntu, maybe it is just not compatible with Brother's CUPS driver?

---

### Post by CharlesA on 2012-04-30
It should support it if it had the drivers available.

---

### Post by kurt18947 on 2012-04-30
I think you'll find that if you have *just* the CUPS driver installed, the printer will not work.  I think you'll need both the lpr and CUPS drivers installed.  Lpr needs to be installed first, then CUPS.  If you're using a 64 bit O.S. you need to installed a couple other things first, all Brother printer drivers are 32 bit.  Here is Brother Linux drivers page and installation instructions.
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

Installing the scanner is another task.  There are a couple items in the FAQ section on scanner install.

---

