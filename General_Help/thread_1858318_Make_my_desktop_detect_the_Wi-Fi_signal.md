---
title: "Make my desktop detect the Wi-Fi signal"
date: 2011-10-12
forum: General Help
---

### Post by anur.bhargav on 2011-10-12
I would like to make my desktop detect my Wi-fi modem just like the laptops do. But I have a questions on what hardware should I buy to be able to do this.

What is the difference between a Wireless USB Adapter and a Wireless Desktop Network Card.

And which one of these should I buy or something like them which may be better. Please review them.

1. Wireless USB Adapter [http://www.flipkart.com/computers/network-components/usb-adaptors/itmdffytdzcyzq8e?pid=usbdffygdk7ddysq&_l=i0Gl7dmUSmlJSyQnzmuCBg--&_r=LgKiEBRXIZMCDZGrOCdxCQ--&ref=476ecaf9-ea63-4bb2-8c32-e98250fa367e](http://www.flipkart.com/computers/network-components/usb-adaptors/itmdffytdzcyzq8e?pid=usbdffygdk7ddysq&_l=i0Gl7dmUSmlJSyQnzmuCBg--&_r=LgKiEBRXIZMCDZGrOCdxCQ--&ref=476ecaf9-ea63-4bb2-8c32-e98250fa367e)

2. Wireless Desktop Network Card [http://www.flipkart.com/computers/network-components/network-nics/itmdffymxrhhxwx7?pid=nicdffyfxphhjgj6&_l=EHChRxVWtW1cPjuSVo2FOQ--&_r=Zwv_emduvrOPTvAOo8AQ5A--&ref=aaa614b1-7a11-424b-9ddc-6056a32f544d](http://www.flipkart.com/computers/network-components/network-nics/itmdffymxrhhxwx7?pid=nicdffyfxphhjgj6&_l=EHChRxVWtW1cPjuSVo2FOQ--&_r=Zwv_emduvrOPTvAOo8AQ5A--&ref=aaa614b1-7a11-424b-9ddc-6056a32f544d)

---

### Post by gandaran on 2011-10-12
> I would like to make my desktop detect my Wi-fi modem just like the laptops do
you already have a wifi card?
if correct then let us see if you need to install driver
type this command in terminal and paste the output
for internal devices
```
lspci
```
for usb devices
```
lsusb
```

without the chipset model and brand it's difficult to know if any of the two adapters you posted work out of the box on Ubuntu.

---

### Post by mikewhatever on 2011-10-12
The difference is pretty obvious, just look at the products pictures. More importantly, google the device you want to buy to make sure it works with Linux. If lots of people had problems with a particular device, you'd probably better skip it.

---

### Post by anur.bhargav on 2011-10-12
> **mikewhatever said:**
> The difference is pretty obvious, just look at the products pictures. More importantly, google the device you want to buy to make sure it works with Linux. If lots of people had problems with a particular device, you'd probably better skip it.

OK done :p... So most Important is look for Ubuntu Linux support... And u say both of those would detect WiFi signals ??
Could u by any chance know any device that is supported by Ubuntu ??

---

### Post by haqking on 2011-10-12
> **anur.bhargav said:**
> OK done :p... So most Important is look for Ubuntu Linux support... 
Could u by any chance know any device ??

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

[http://linuxhcl.com/](http://linuxhcl.com/)

---

### Post by anur.bhargav on 2011-10-12
> **gandaran said:**
> you already have a wifi card?
if correct then let us see if you need to install driver
type this command in terminal and paste the output
for internal devices
```
lspci
```for usb devices
```
lsusb
```without the chipset model and brand it's difficult to know if any of the two adapters you posted work out of the box on Ubuntu.


No I don't have a WiFi card in my desktop.. But have a Wireless Access Point (WiFi modem)..
Anyways Here's the output of the commands
```
 lspci 

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
``````
 lsusb 

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 0461:4d22 Primax Electronics, Ltd 
Bus 005 Device 002: ID 1c4f:0016 SiGma Micro 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0644:0200 TEAC Corp. All-In-One Multi-Card Reader CA200/B/S
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by sffvba[e0rt on 2011-10-12
***Threads merged.***

@OP - Please only start one thread on a topic.


Regards
404

---

### Post by anur.bhargav on 2011-10-12
> **not found said:**
> ***Threads merged.***

@OP - Please only start one thread on a topic.


Regards
404


I'm really sorry about that... I've hit it twice by mistake :(

---

### Post by prestone on 2011-10-12
I found that most cheap USB wifi cards work fine, alfa makes good wifi cards.

---

### Post by anur.bhargav on 2011-10-12
> **haqking said:**
> [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

[http://linuxhcl.com/](http://linuxhcl.com/)


Could I buy this..
[http://www.flipkart.com/computers/network-components/usb-adaptors/itmdffytfmtfyrhw?pid=usbdffyghugba8pn&_l=6+ctCdGX3gIXnmMGDpUTLA--&_r=01+vXbIZTTPedSOcih1tNA--&ref=c916dc2b-7183-47e1-9685-3b1d10f74425](http://www.flipkart.com/computers/network-components/usb-adaptors/itmdffytfmtfyrhw?pid=usbdffyghugba8pn&_l=6+ctCdGX3gIXnmMGDpUTLA--&_r=01+vXbIZTTPedSOcih1tNA--&ref=c916dc2b-7183-47e1-9685-3b1d10f74425)

Please Cross check once... Its Listed here, Last but one  [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB)
but not at LinuxHCL..

Would it work, can it detect my WiFi modem ??

---

### Post by haqking on 2011-10-12
> **anur.bhargav said:**
> Could I buy this..
[http://www.flipkart.com/computers/network-components/usb-adaptors/itmdffytfmtfyrhw?pid=usbdffyghugba8pn&_l=6+ctCdGX3gIXnmMGDpUTLA--&_r=01+vXbIZTTPedSOcih1tNA--&ref=c916dc2b-7183-47e1-9685-3b1d10f74425](http://www.flipkart.com/computers/network-components/usb-adaptors/itmdffytfmtfyrhw?pid=usbdffyghugba8pn&_l=6+ctCdGX3gIXnmMGDpUTLA--&_r=01+vXbIZTTPedSOcih1tNA--&ref=c916dc2b-7183-47e1-9685-3b1d10f74425)

Please Cross check once... Its Listed here, Last but one  [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB)
but not at LinuxHCL..

Would it work, can it detect my WiFi modem ??

yes you can buy it.

it shows it as supported.

i expect so.

---

### Post by anur.bhargav on 2011-10-12
> **haqking said:**
> yes you can buy it.

it shows it as supported.

i expect so.

Thank you very much:popcorn:.. Done Deal... I still haven't got one thing.. These are the the things that detect WiFi signals.. Right ??

---

### Post by haqking on 2011-10-12
> **anur.bhargav said:**
> Thank you very much:popcorn:.. Done Deal... I still haven't got one thing.. These are the the things that detect WiFi signals.. Right ??

?

a wireless adapter detects wireless signals.

what do you mean ? like a keyring wifi finder ? you can buy them at any online geek store including t-shirts which show you wifi signals

---

### Post by anur.bhargav on 2011-10-12
> **haqking said:**
> ?

a wireless adapter detects wireless signals.

what do you mean ? like a keyring wifi finder ? you can buy them at any online geek store including t-shirts which show you wifi signals

Hehe ;) .. Nah I don't want them... WiFi's not very famous here in India yet.. Its just confined to Homes..

Thanks A Ton... I'm ordering it..:popcorn:

---

### Post by haqking on 2011-10-12
> **anur.bhargav said:**
> Hehe ;) .. Nah I don't want them... WiFi's not very famous here in India yet.. Its just confined to Homes..

Thanks A Ton... I'm ordering it..:popcorn:

ok no worries, remember to mark the thread as solved using thread tools.

cheers

---

