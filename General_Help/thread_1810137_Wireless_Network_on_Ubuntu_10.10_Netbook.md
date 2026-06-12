---
title: "Wireless Network on Ubuntu 10.10 Netbook"
date: 2011-07-22
forum: General Help
---

### Post by meganjonez on 2011-07-22
Hi, I've just installed the netbook remix 10.04 on my Zoostorm XL netbook and all is working except for the WiFi.

I've searched google and the forums and came across a few possible answers all of which don't seem to work. I was just wondering if anyone could help me?

thanks.

---

### Post by seawolf167 on 2011-07-22
If you plug you laptop in to your router via an ethernet cable, then open the Hardware Drivers (System -> Administration -> Hardware Drivers) do you have any available drivers for your wireless device?

---

### Post by meganjonez on 2011-07-22
just checked and it just says 'no proprietary drivers are in use on this system'

---

### Post by gandaran on 2011-07-22
> **meganjonez said:**
> just checked and it just says 'no proprietary drivers are in use on this system'
post the output of 
```
lspci
```
(type in terminal) this is to identify the wireless chipset and find appropriate drivers.

---

### Post by meganjonez on 2011-07-22
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
megan@megan-laptop:~$

---

### Post by gandaran on 2011-07-22
> 02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
if you use the forum search box for **RaLink RT3090** especially in the networking and wireless forum section you can find many posts and possibly the answer on how to get the RT3090 chip working.

---

### Post by meganjonez on 2011-07-22
I've just realised I have:
megan@megan-laptop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"
megan@megan-laptop:~$ 

Would this make any difference? I have found the Ralink driver before and when tried to install have been told to insert the Lucid 10.04 disk into the CD ROM which I obviously don't have, as I have a netbook with no CD drive.

---

### Post by gandaran on 2011-07-22
here is a thread about ubuntu 10.04 and RaLink RT3090 that should help you
[http://ubuntuforums.org/showthread.php?t=1490123&highlight=RaLink+RT3090](http://ubuntuforums.org/showthread.php?t=1490123&highlight=RaLink+RT3090)

---

### Post by seawolf167 on 2011-07-22
Here is a how-to for the RaLink RT3090 driver for 10.04 LTS (should be the same for 10.10)
[URL="http://www.halibutdepot.org/how_to_build_rt3090_for_ubuntu_lucid/"]
http://www.halibutdepot.org/how_to_build_rt3090_for_ubuntu_lucid/[/URL]

---

### Post by Phil Binner on 2011-07-24
Sorry if I'm butting in, but I just had a problem connecting 2 Ubuntu machines to a network where Windows connects fine. My problem was for wireless and wired.

We pinned the down to a problem with the router which Windows is not sensitive to but Ubuntu, I-phone and Android are. It was solved by assigning static IP addresses in Ubuntu.

---

