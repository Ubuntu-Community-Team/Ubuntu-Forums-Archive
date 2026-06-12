---
title: "Ubuntu 10.10 on old laptop"
date: 2011-08-18
forum: General Help
---

### Post by Advait on 2011-08-18
Hi All,

A few days ago I installed 10.10 on a friend's Dell Inspiron 600M laptop that has 1gb ram and Pentium M-725 1.6GHz (8GB partition for 10.10, dual boot with Windows XP SP3).

Ubuntu is running slow, especially when we try to navigate web pages (the web pages scroll very slowly). The bandwidth is fine so I'm pretty sure the slowness is not due to the internet connection. It's also slow in non internet apps like OpenOffice.

On the Windows side, the web pages scroll normally.

I'm presuming this laptop has plenty of horsepower to run 10.10. Let me know if not true.

Any ideas why it would be slow? Should I try to update the video drivers? I presume a video driver update has to be done within Windows? True?

Any ideas appreciated. Thanks!

Advait

---

### Post by mikewhatever on 2011-08-19
Can you post the output of **lspci** from Applications->Accessories->terminal in Ubuntu. The output should identify the video related hardware, which, so far, we know nothing about. If you have desktop effects enabled, turn them off.

'Updating drivers' is a phrase from the Windows world. With Linux, it's easier to upgrade the kernel or the whole distro then a driver.

---

### Post by sbraz on 2011-08-19
i think this is your problem:
**ATI Mobility RADEON 9000** AGP 4X video graphics at 32MB

more specs here:
[http://www.notebookreview.com/default.asp?newsID=2154](http://www.notebookreview.com/default.asp?newsID=2154)

---

### Post by sbraz on 2011-08-19
i've just read here:
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell)

```
Modem not tested. The wireless card has irq problems but can 
be fixed with pci=noacpi in grub or by disabling the parallel port 
in the Bios. -- 
https://bugzilla.ubuntu.com/show_bug.cgi?id=1254
```
[https://bugzilla.ubuntu.com/show_bug.cgi?id=1254](https://bugzilla.ubuntu.com/show_bug.cgi?id=1254)

---

### Post by Advait on 2011-08-25
It turns out the client's laptop also began running very slow on the Windows side (with the cpu pegged at 100%). I updated the video driver and problem solved. Yay! Soon I'll test the video on the Ubuntu side. Thanks!

> **sbraz said:**
> i think this is your problem:
**ATI Mobility RADEON 9000** AGP 4X video graphics at 32MB

more specs here:
[http://www.notebookreview.com/default.asp?newsID=2154](http://www.notebookreview.com/default.asp?newsID=2154)

---

