---
title: "Brother HL-2170W - 9.10 UNR"
date: 2010-04-02
forum: General Help
---

### Post by RamboGT on 2010-04-02
Greetings,

I recently went full UNR from Win7, and loved it.

I'm having only one real issue...my brother HL-2170W printer won't install properly.  I followed the two line install for 9.04 listed here:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#002](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#002)
for pre-install, then installed the cupswrapper driver (deb) listed here:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2170W](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2170W)

What else do I need to do....it will print a test-page upon install, but nothing from either Google Chrome or from a PDF, but will in OpenOffice and Gmail.

Any clues?

Thanks.

RamboGT

---

### Post by RamboGT on 2010-04-14
57 views...no help, thx.

---

### Post by plucky on 2010-04-15
> **RamboGT said:**
> Greetings,

I recently went full UNR from Win7, and loved it.

I'm having only one real issue...my brother HL-2170W printer won't install properly.  I followed the two line install for 9.04 listed here:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#002](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#002)
for pre-install, then installed the cupswrapper driver (deb) listed here:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2170W](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2170W)

What else do I need to do....it will print a test-page upon install, but nothing from either Google Chrome or from a PDF, but will in OpenOffice and Gmail.

Any clues?

Thanks.

RamboGT


Install the LPR driver as well.

The install instructions are also on the [Brother Website](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2170W)

I would recommend you connect the printer with USB cable to make sure it works before trying to get it working with the wireless connection.

After both drivers are installed,connect and power on the printer and then go to **System > Administration > Printing** and select **New Printer**.
Answer the questions and select the correct driver and hopefully it will now work.

Good Luck

---

### Post by RamboGT on 2010-04-15
Install everything per Brother's website, and the LPR and CUPS drivers...no joy.

When I go to Add New Printer, it searchs and finds nothing.  Also I'm installing this via the Cat5e cable, not wireless.

How do flash the machine, as I do not remember how it was orginally setup wirelessly.  I do not have a windows machine to go through to setup wireless.

Thanks.

---

### Post by garvinrick4 on 2010-04-15
It does not have a USB to cable with? The driver is installed already in ubuntu
for wired. If you have a router for Wifi you can set-up a network and will print
from laptop no problem. Takes a few minutes to follow instructions Ubuntu
gives you. Ubuntu has just a ton of drivers for Brother printers. Windows workgroup
with windows and Samba for Ubuntu.

---

