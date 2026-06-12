---
title: "Printing question before installing Ubuntu on a client's PC."
date: 2012-06-06
forum: General Help
---

### Post by Colo2 on 2012-06-06
Hi.

I have a client who wants Ubuntu, but I need to make sure that their printer: Epson Stylus SX405 will work..

Looking at OpenPrinting:
[http://www.openprinting.org/printer/Epson/Epson-Stylus_SX400](http://www.openprinting.org/printer/Epson/Epson-Stylus_SX400)

The SX400 works perfectly, but theres no SX405 on that list at all.

Does this mean it's going to work, or not?

Thanks

Tom.

---

### Post by TheFu on 2012-06-06
> **Colo2 said:**
> The SX400 works perfectly, but theres no SX405 on that list at all.

Does this mean it's going to work, or not?

I don't know. Epson is the manufacturer, do they make Linux drivers? 
Are they well known for supporting Linux?
[http://esupport.epson-europe.com/ProductHome.aspx?lng=en-GB&data=YZnBT5wk60YA+Sz90uy8vFYplWSfOZ7z&tc=6](http://esupport.epson-europe.com/ProductHome.aspx?lng=en-GB&data=YZnBT5wk60YA+Sz90uy8vFYplWSfOZ7z&tc=6) seems to say **Windows only.**  It doesn't hurt to ask them directly, Epson.

I thought Epson was known for good Linux support. Perhaps I was confused?

A Google for "*SX405 linux driver*" found this: [https://www.openprinting.org/printer/Epson/Epson-Stylus_SX405](https://www.openprinting.org/printer/Epson/Epson-Stylus_SX405) - which seems to say it should work but nobody can be 100% certain until you try it on the exact system.

---

### Post by Swagman on 2012-06-06
You/they could spend a few bob and buy TurboPrint

[http://www.turboprint.info/](http://www.turboprint.info/)

---

### Post by Mark Phelps on 2012-06-06
My own experience is that Epson does NOT provide Linux support -- which makes is no different from the other printer vendors.

To get my Epson printer working, I installed the CUPS driver.

To get ink monitoring, I had to install and get mtink working.

NONE of these came from Epson.

---

### Post by apollothethird on 2012-06-06
> **Colo2 said:**
> Hi.

I have a client who wants Ubuntu, but I need to make sure that their printer: Epson Stylus SX405 will work..

Looking at OpenPrinting:
[http://www.openprinting.org/printer/Epson/Epson-Stylus_SX400](http://www.openprinting.org/printer/Epson/Epson-Stylus_SX400)

The SX400 works perfectly, but theres no SX405 on that list at all.

Does this mean it's going to work, or not?

Thanks

Tom.

Let us know how you make out.  I haven't tried the Epson printer with Ubuntu, but I have used several HP printers and never had a problem from either.

When you consider the money saved by using Ubuntu over Windows (no more annual or biannual upgrade fees for the OS (about $200.00) and Office (another $200.00) and you've more than paid for the printer.  The last time I upgraded a client to Ubuntu I recommended an HP printer as part of the upgrade to avoid problems.

By the way, he had a Lexmark which as far as I know is nothing but paperweight on a Linux machine.

I'll be glad to watch how you make out with the Epson.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Mark Phelps on 2012-06-06
> **apollothethird said:**
> ... I have used several HP printers and never had a problem from either.

I have HP printers and they have all installed without problems, as well.

However, while I personally haven't used HPLIP, others have, and it supposedly works wonders with installing HP printers.

AFAIK, there is no HPLIP equivalent for Epson.

---

### Post by philinux on 2012-06-06
Epson provides a linux driver via avasys.

Should be a .deb file available. [http://avasys.jp/eng/linux_driver/download/](http://avasys.jp/eng/linux_driver/download/)

---

### Post by sammiev on 2012-06-06
I have an Espon Artisan 730 works right out of the box. Prints both side and scans with no issues. Also have an Epson 280 that also works right out of the box. If you have a laptop, test it there first or another unit running Ubuntu. :)

---

### Post by Colo2 on 2012-06-06
Thanks guys, I installed ubuntu on his laptop, and will go to his house tomorrow to try and get the printer working.

Will post back with results.

Tom

---

### Post by Skara Brae on 2012-06-06
> **apollothethird said:**
> By the way, he had a Lexmark which as far as I know is nothing but paperweight on a Linux machine.
At work, we run SLED10 (KDE 3.5) and we have several Lexmark (laser) printers/models and they work fine. They use CUPS, I can see.

I have an Epson Stylus R200 here at home - but it is attached to my iMac, for which Epson provides a driver (and standing in another room).
The Epson site only shows Epson Stylus R200 drivers for Windos and OS X.

> **philinux said:**
> Epson provides a linux driver via avasys.

Should be a .deb file available. [http://avasys.jp/eng/linux_driver/download/](http://avasys.jp/eng/linux_driver/download/)
Hey, indeed they do!

---

### Post by Colo2 on 2012-06-07
Hello

Im back.

Plugged the printer in, the gnome display bubble appeared at top right saying it automatically installed the printer, and I proceeded to print photos without any issue. No installation/tweeking/headaches involved. 

Windows is way more of a pain in the ***! :P

Tom

---

### Post by sammiev on 2012-06-07
> **Colo2 said:**
> Hello

Im back.

Plugged the printer in, the gnome display bubble appeared at top right saying it automatically installed the printer, and I proceeded to print photos without any issue. No installation/tweeking/headaches involved. 

Windows is way more of a pain in the ***! :P

Tom

I thought it was going to be plug and play. Maybe mark this thread as solved for the next folks who do a search. :)

---

### Post by Colo2 on 2012-06-07
> **sammiev said:**
> I thought it was going to be plug and play. Maybe mark this thread as solved for the next folks who do a search. :)

Good plan :)

---

