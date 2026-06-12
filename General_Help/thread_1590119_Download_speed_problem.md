---
title: "Download speed problem"
date: 2010-10-07
forum: General Help
---

### Post by Magnificence on 2010-10-07
Hi all,

I just installed Ubuntu 10.04 Desktop edition on my laptop.
My download speed is now very slow, it isn't that slow when I run Windows 7 on the same laptop. It looks like it stops every second and then let some through for a little moment. When I download packages or update, my overall download speed is about 100kb/s or less. And I know that it usually becomes about 1Mb/s.

It this an issue I someone can fix or could this be something else, like a driver error?

Thank you.

---

### Post by lrgmmc on 2010-10-07
what is your network hardware?is it wireless?

---

### Post by TBABill on 2010-10-07
Same speed wired and wireless?

---

### Post by lrgmmc on 2010-10-07
are you using wireless or wired? and yes, if you do use both is the speed the same?

---

### Post by Magnificence on 2010-10-07
It is wireless, if I use wired on the laptop there is no problem at all, but wireless only acts weird when I have ubuntu running.

---

### Post by coffeecat on 2010-10-07
> **Magnificence said:**
> It is wireless,

And the hardware? What make and model laptop? What is the wireless card? Open a terminal, run the command:

```
lspci
```

and post the line of the output that describes the wireless card.

---

### Post by Magnificence on 2010-10-07
The command outputs:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
09:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
```

And the model of the laptop itself is called Dell Vostro V13.

---

### Post by coffeecat on 2010-10-07
> **Magnificence said:**
> The command outputs:
```
09:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
```

Well, that's very strange. I was expecting a "difficult" chipset, but that's the wireless chipset I have on my Sony laptop and it works just fine - as well as in Windows and no diminution of speed.

Perhaps someone else may have something to offer.

---

### Post by Magnificence on 2010-10-07
Ok, maybe I should reinstall Ubuntu, I forgot to plug in the power on my laptop while the installation process was resizing my partition, I know, that's stupid. xD After that I tried to let Windows restore that, and I installed Ubuntu again. Maybe that has caused some difficulties? I noticed that my laptop just shut off a few minutes ago for no reason too.

But thank you anyway!

---

### Post by coffeecat on 2010-10-07
> **Magnificence said:**
> Ok, maybe I should reinstall Ubuntu, I forgot to plug in the power on my laptop while the installation process was resizing my partition, I know, that's stupid. xD After that I tried to let Windows restore that, and I installed Ubuntu again. Maybe that has caused some difficulties? I noticed that my laptop just shut off a few minutes ago for no reason too.

I doubt whether a re-installation would make any difference, unless you are getting other problems.

Before you install, try the wireless in the live CD session. If you get good speeds then at least you know you can get good speeds with Ubuntu with that laptop. If you don't, then you need to consider other factors. I do remember a thread where a poster - albeit with a different make of laptop and different wireless device -  was experiencing wireless driver problems where that driver and wireless worked just fine for other people. If I remember correctly the conclusion was that there was a conflict between the wireless driver and the particular implementation of ACPI. Your machine is a Dell - mine a Sony. Perhaps a problem in the BIOS firmware - I don't know.

---

