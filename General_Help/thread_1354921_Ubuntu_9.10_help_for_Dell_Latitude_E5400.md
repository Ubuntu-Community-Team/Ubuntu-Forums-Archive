---
title: "Ubuntu 9.10 help for Dell Latitude E5400"
date: 2009-12-14
forum: General Help
---

### Post by paragkalra on 2009-12-14
Hello All,

Previously I was using Ubuntu 8.10 on Inspiron 1525 and everything was working on it - right from Wifi to MP3 to Movies

I just installed Ubuntu 9.10 on Dell Latitude E5400 and would like to do the same for it as well.

Could some please point me to an appropriate thread or steps required to enable drivers for Wifi and installation of all the codecs for MP3 and all kind of Movie formats.

---

### Post by snowpine on 2009-12-14
You can install all necessary codecs as follows:

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

I can't help with the wireless, because I don't know what kind of wireless card you have. Have you tried System->Administration->Hardware?

---

### Post by paragkalra on 2009-12-14
parag@nglap093:~/Downloads$ lspci | tail -3
> 02:01.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5761e Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)


'System->Administration->Hardware' Drivers show nothing.

---

### Post by snowpine on 2009-12-14
Broadcom 4312 is problematic; bunch of threads on it for example including these recent ones:

[http://ubuntuforums.org/showthread.php?t=1309760](http://ubuntuforums.org/showthread.php?t=1309760)
[http://ubuntuforums.org/showthread.php?t=1311938](http://ubuntuforums.org/showthread.php?t=1311938)

Not having the Ubuntu/4312 combination myself, I do not have a definitive solution for you. :) I do know that Broadcom makes their Linux driver freely available, so I'm sure it is possible to fix it.

---

### Post by paragkalra on 2009-12-15
Ok installed the driver 'compat-wireless-2.6.32.tar.bz2' from here -
[http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)

Rebooted the machine.

Under 'System->Administration->Hardware Drivers' 2 wireless drivers now became visible.

Enabled & Activated Broadcom STA Wireless Driver

Again rebooted the machine.

 Now it shows Driver is activated but not in use.

How to use this driver 

 Or do I need to upgrade the Kernel. My current Kernel is 2.6.31-14-generic

---

