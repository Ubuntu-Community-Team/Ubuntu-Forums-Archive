---
title: "Installation of an old friend: 10.04 LTS"
date: 2012-05-10
forum: General Help
---

### Post by OllieGab on 2012-05-10
After problems with installing Ubuntu 12.04 - blank screens at boot up etc (which I believe is due to that the screen/monitor parameters are now loaded from 'inside' the kernel...or something like that) I installed an old friend. Ubuntu 10.04 and everything is working just fine.
I did the 'apt-get update' post installation.
If I now do the 'apt-get upgrade', does that mean that it will upgrade to a later distro? Ie, 10.11. Or will it 'jump' directly to the latest Ubuntu? Or perhaps 'upgrade' actually means something completely different?

Cheers!

---

### Post by kc1di on 2012-05-10
> **OllieGab said:**
> After problems with installing Ubuntu 12.04 - blank screens at boot up etc (which I believe is due to that the screen/monitor parameters are now loaded from 'inside' the kernel...or something like that) I installed an old friend. Ubuntu 10.04 and everything is working just fine.
I did the 'apt-get update' post installation.
If I now do the 'apt-get upgrade', does that mean that it will upgrade to a later distro? Ie, 10.11. Or will it 'jump' directly to the latest Ubuntu? Or perhaps 'upgrade' actually means something completely different?

Cheers!

No ```
apt-get upgrade 
```only moves the installed packages to their newest available versions. 

in order to do a distribution upgrade you would have to enter 
```
apt-get dist-upgrade
``` while having the correct repositories available on your machine.

---

### Post by OllieGab on 2012-05-11
Thanks for that!
Now, I upgraded to 10.11 - which is now unsupported - and then again to 11.04. This is where it gets 'exciting'.
This is where Unity comes in and where my screen goes blank. I can boot up using a previous kernel (2.6.32-42) but obviously I'd like it to work 'as it should'.
If I add 'nomodeset' i etc/default/grub it does start up but in the classical style, also saying "You hardware does not seem to work with Unity".
This is not true as I've had it working with Unity using the previous kernel.
Any ideas where I can go from here? This blank screen thingy seems to be quite a common thing now as the same happens with Mint and some other OSs.

Cheers

---

### Post by wilee-nilee on 2012-05-11
Blank screen generally means you need a graphics driver. In what ever version your running on now update the OS and look in the additional drivers app to see if a driver is waiting.

You can also run this and identify the graphic card as well, post the card if needed.

```
lspci
```

---

### Post by kc1di on 2012-05-11
> **OllieGab said:**
> Thanks for that!
Now, I upgraded to 10.11 - which is now unsupported - and then again to 11.04. This is where it gets 'exciting'.
This is where Unity comes in and where my screen goes blank. I can boot up using a previous kernel (2.6.32-42) but obviously I'd like it to work 'as it should'.
If I add 'nomodeset' i etc/default/grub it does start up but in the classical style, also saying "You hardware does not seem to work with Unity".
This is not true as I've had it working with Unity using the previous kernel.
Any ideas where I can go from here? This blank screen thingy seems to be quite a common thing now as the same happens with Mint and some other OSs.

Cheers

Follow wilee-nilee  command and let us know what video card your using , there have been some problems in 12.04 with some cards and we may be able to help further.

---

### Post by OllieGab on 2012-05-11
lspci gives me the following:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)

The thing is, the kernel 2.6.35 works fine (with Unity) but the default for 12.04 (2.6.38) doesn't. Would they really remove something that works in a newer version of the kernel?

---

### Post by OllieGab on 2012-05-11
Further to my reply. Don't know how the smiley ended up there...should say. 2.6.38!

---

