---
title: "Ubuntu isn't available"
date: 2011-11-21
forum: General Help
---

### Post by Cavid on 2011-11-21
Hello everyone. I was playing SuperTux cart race, and suddenly game got frozen!! System was working OK, but I couldn't exit the game( I clicked X button couple of times)!! So I decided to turn of my notebook and turn it on again!! This time there was only Ubuntu 2D available, there is no Normal Ubuntu!! Anyone who can help, pls answer!!

---

### Post by ikt on 2011-11-21
Are you able to confirm which drivers are installed? also which graphics card do you use?

---

### Post by Cavid on 2011-11-21
I am using Toshiba L300 satellite, so the graphics card is standard (provided by manufacturer) its memory is 384 mb or so. I can log in to my notebook using Ubuntu 2D, if there is anyway to get drivers' list tell me!!

---

### Post by ubudog on 2011-11-21
Could you please post the output of:
```
lspci
```
(run that in a terminal)

Which will tell us some of your system specs.

Also, look at Restricted Drivers to see if there's anything there to install.

(Search for "drivers" using the Dash)

---

### Post by Cavid on 2011-11-22
Ok, here is the output:


```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

And The program Additional Drivers didn't found anything to be installed
Thanks, for reply

---

