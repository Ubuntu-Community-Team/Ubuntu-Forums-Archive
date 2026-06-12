---
title: "Broadcom driver support"
date: 2012-07-16
forum: General Help
---

### Post by hunter.allen on 2012-07-16
Hello all, 

I am having trouble installing a broadcom wireless driver... I see [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") that it is supposedly supported. Here is some helpful output: 


```
allenh1@roboard:~$ lspci
00:00.0 Host bridge: RDC Semiconductor, Inc. R6021 Host Bridge (rev 02)
00:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
00:07.0 ISA bridge: RDC Semiconductor, Inc. R6031 ISA Bridge (rev 02)
00:08.0 Ethernet controller: RDC Semiconductor, Inc. R6040 MAC Controller
00:0a.0 USB Controller: RDC Semiconductor, Inc. R6060 USB 1.1 Controller (rev 12)
00:0a.1 USB Controller: RDC Semiconductor, Inc. R6061 USB 2.0 Controller (rev 03)
00:0b.0 USB Controller: RDC Semiconductor, Inc. R6060 USB 1.1 Controller (rev 12)
00:0b.1 USB Controller: RDC Semiconductor, Inc. R6061 USB 2.0 Controller (rev 03)
00:0c.0 IDE interface: RDC Semiconductor, Inc. Device 1011 (rev 01)
```

```
allenh1@roboard:~$ modprobe b43
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module b43 not found.
```

```
allenh1@roboard:/etc/modprobe.d$ ls
alsa-base.conf          blacklist-firewire.conf     blacklist-watchdog.conf
blacklist-ath_pci.conf  blacklist-framebuffer.conf  broadcom-sta-common.conf
blacklist-bcm43.conf    blacklist-modem.conf        libpisock9.conf
blacklist.conf          blacklist-oss.conf          ndiswrapper


```


```
allenh1@roboard:~$ lspci -n | grep '14e4:43'
00:03.0 0280: 14e4:4324 (rev 03)
```

```
allenh1@roboard:~$ lsb_release -d
Description:	Ubuntu 10.04.4 LTS
```


```
allenh1@roboard:~$ uname -mr
2.6.34.10-vortex86-sg i586
```

Any help? I am comfortable using ndiswrapper if needed.

---

### Post by mike555 on 2012-07-16
in 12.04 the package manager has "b43-fwcutter ", that should help if yours has it.

---

### Post by hunter.allen on 2012-07-16
I have installed that package; however, no dice...

---

### Post by kurt18947 on 2012-07-16
> **hunter.allen said:**
> I have installed that package; however, no dice...

Have you checked in 'additional drivers'?  Some Broadcom adapters come to life once the additional driver is installed/activated.  Others don't.

---

### Post by hunter.allen on 2012-07-16
How should I do this?

---

### Post by kurt18947 on 2012-07-18
> **hunter.allen said:**
> How should I do this?

It depends on what *buntu version you're running.  For Unity or Gnome-shell, press the windows/super key then type "add".  Additional Drivers should be one of the choices.  I don't have an Xubuntu or Lubuntu desktop handy to check those.

---

