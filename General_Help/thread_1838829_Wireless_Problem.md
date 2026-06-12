---
title: "Wireless Problem"
date: 2011-09-04
forum: General Help
---

### Post by dipendra2966 on 2011-09-04
With high hopes, i installed Ubuntu.. I'm completely new to ubuntu.. I'm running ubuntu on DELL Latitude D630. My wireless gets disconnected very frequently.I'm not able to use Ubuntu properly.. please help ..

otherwise i guess i'll have to go back to windows again

---

### Post by brucehohl on 2011-09-04
Start here:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

And, search this forum for "Latitude D630 wireless".

---

### Post by gandaran on 2011-09-04
> **dipendra2966 said:**
> With high hopes, i installed Ubuntu.. I'm completely new to ubuntu.. I'm running ubuntu on DELL Latitude D630. My wireless gets disconnected very frequently.I'm not able to use Ubuntu properly.. please help ..

otherwise i guess i'll have to go back to windows again
what is the wireless chipset brand? you may find the solution on the forum searching for threads with the same wireless chipset.
type in terminal and paste the output
```
lspci
```

---

### Post by dipendra2966 on 2011-09-04
> **gandaran said:**
> what is the wireless chipset brand? you may find the solution on the forum searching for threads with the same wireless chipset.
type in terminal and paste the output
```
lspci
```
dipendra@dipendra-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

---

### Post by gandaran on 2011-09-04
> 0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
there are some threads about the Intel wireless 3945ABG chipset issues you should check out in the network and wireless section.
what wireless security does the router setup have? wep, wpa or wpa2?
[http://ubuntuforums.org/showthread.php?t=1784698&highlight=Intel+Corporation+PRO%2FWireless+3945ABG&page=3](http://ubuntuforums.org/showthread.php?t=1784698&highlight=Intel+Corporation+PRO%2FWireless+3945ABG&page=3)

---

### Post by dipendra2966 on 2011-09-04
> **gandaran said:**
> there are some threads about the Intel wireless 3945ABG chipset issues you should check out in the network and wireless section.
what wireless security does the router setup have? wep, wpa or wpa2?
[http://ubuntuforums.org/showthread.php?t=1784698&highlight=Intel+Corporation+PRO%2FWireless+3945ABG&page=3](http://ubuntuforums.org/showthread.php?t=1784698&highlight=Intel+Corporation+PRO%2FWireless+3945ABG&page=3)

I was in the WPA..now it has started working once i changed it to WEP....thnx buddy !!

---

