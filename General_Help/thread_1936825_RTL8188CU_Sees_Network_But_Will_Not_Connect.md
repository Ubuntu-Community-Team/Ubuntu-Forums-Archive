---
title: "RTL8188CU Sees Network But Will Not Connect"
date: 2012-03-06
forum: General Help
---

### Post by fleamour on 2012-03-06
Followed this guide to install driver for a micro USB Wireless Realtek, RTL8188CU based chip:

[http://www.solwiseforum.co.uk/showthread.php?9849-NET-WL-UMD-606N-and-Linux&p=46859#post46859](http://www.solwiseforum.co.uk/showthread.php?9849-NET-WL-UMD-606N-and-Linux&p=46859#post46859)

Although Ubuntu 11.10 will see wireless network/s it wont, actually connect.  It works fine with Windows 7.  I switched WNICs as previous Edimax card worked with Ubuntu but not 7.  (Edimax card is listed as 7 compatible, but I do not think it likes my router.)  Swapping out WNICs for Realtek should've proved to be the easiest/cheapest option, or so I thought.

Frustrating I'm sure you can appreciate!  So much for dual boot.

:confused: :( :confused:

---

### Post by fleamour on 2012-03-06
OK.  So it works after a reboot, but the internet connectivity runs like treacle, so slow as to be unusable.  

If I flick the wireless switch to off, then on, the internet connection looses the will to live!  It'll only connect on boot.

I get one compilation error, as follows:

```
ERROR:  Module 8192CU does not exist in /proc/modules
```

:(

---

### Post by fleamour on 2012-03-06
This worked!:

[http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/](http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/)

Phew, mammoth effort!

:D :mrgreen: :D

---

### Post by kurt18947 on 2012-03-06
> **fleamour said:**
> This worked!:

[http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/](http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/)

Phew, mammoth effort!

:D :mrgreen: :D

I haven't had much luck with this adapter in Mint 12 based on Ubuntu 11.10.  I may try this.  The good news is that with 12.04 (so far at least) the driver from Realtek and its associated install script works perfectly.

[SIZE=3]EDIT:[/SIZE]: installing Realtek's 8188Cus driver via the install script then doing  in  /etc/modprobe.d/blacklist.conf
```
blacklist rtl8192cu
```works with Linux Mint 12 as well.  Good job fleamour!  I find this adapter noticeably faster than the integral Intel iwl3945.

---

