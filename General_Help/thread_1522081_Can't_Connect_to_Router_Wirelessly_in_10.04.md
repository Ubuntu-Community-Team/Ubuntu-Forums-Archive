---
title: "Can't Connect to Router Wirelessly in 10.04"
date: 2010-07-01
forum: General Help
---

### Post by snowmanman on 2010-07-01
I am not able to get wireless internet working on Ubuntu 10.04. I have a Wireless PCI card, Netgear WG311v2.

I can't connect to the router, even though I downloaded the Windows drivers using Ndiswrapper.

Thanks in advance for any ideas you might have.

---

### Post by bobcollard on 2010-07-01
Left click on the Network icon in the Panel and see if it is listed, if so click on that and enter your WEP or other password and it should start.  Alternately if you right click the icon you will get a menu which includes "Edit Connections"  Use that to add a wireless address to your system.  One other posibility, in System/Hardware Drivers see if there are proprietary drivers recommended.
I am using Netgear WG111v3 with a Cisco Router and have no problems with Xubuntu 10.04.  My original Broadband got burnt and I had it removed then added the Netgear.

---

### Post by snowmanman on 2010-07-05
I went to edit connections and I added my information, though I'm not sure what my bssid is, if i have a 128-bit wep passphrase or 40/128-bit wep key, or what i should do with ipv4/6 settings.

I don't appear to need proprietary drivers.

It says I have never used the connection and I have it set to connect automatically.

---

### Post by snowmanman on 2010-07-05
iwconfig brings up lo and eth0 and neither have wireless extensions. ndiswrapper still says that the driver is installed and the device is present. It's like Ubuntu doesn't see it.

---

### Post by bobcollard on 2010-07-05
> **snowmanman said:**
> I went to edit connections and I added my information, though I'm not sure what my bssid is, if i have a 128-bit wep passphrase or 40/128-bit wep key, or what i should do with ipv4/6 settings.

I don't appear to need proprietary drivers.

It says I have never used the connection and I have it set to connect automatically.
For the above information call your ISP (Internet Service Provider)

---

