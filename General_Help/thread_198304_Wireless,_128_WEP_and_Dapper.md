---
title: "Wireless, 128 WEP and Dapper"
date: 2006-06-17
forum: General Help
---

### Post by blue_thunder on 2006-06-17
I've recently made the switch to dapper, and while under my ethernet connection at school everything worked well. Now I'm home, and trying to connect to my network, something I did through "System-Networking" in Breezy pretty easily, but now cannot figure out.

ndiswrapper -l yields "bcmwl5   driver present, hardward present"
ndiswrapper -m yields "modprobe config already contains alias directive"

What should I type, if anything, for Network name (ESSID)? MY WEP key is 128bit, so should the code be 13 digit pairs (26 digits), and how exactly would I enter that? Should I leave it in Hexidecimal or Plain, in the Network settings?

I'm sorry if I sound awfully noobish. Thanks so much for any help.

---

### Post by x64Jimbo on 2006-06-17
iwconfig has all the options you need. For more info, type man iwconfig

---

### Post by blue_thunder on 2006-06-17
Thanks Jimbo, I'll give it a try.

---

### Post by blue_thunder on 2006-06-17
OK. I'm still totally lost. After trying to configure somethings with iwconfig, I still can't get the wireless to activate. There has gotta be something easier here that I'm just missing out on. On Breezy I could enter all the info for a static IP, the password for WEP and it would all work out, but here I don't know what it is I'm doing wrong.
Please help.

I can give you guys any information you need to help me. Just let me know what I can do.

---

### Post by Glass Casket on 2006-06-17
He is what i did.

1. Load up the appropriate driver is ndiswrapper
2. '# iwconfig wlan0 essid PUTYOURESSIDHERE'
3. '# iwconfig wlan0 key PUTYOUR26CHARACTER KEY HERE'
3. '# dhcpcd wlan0'

And that should work given you gave the right passkey. :)

---

### Post by blue_thunder on 2006-06-18
Everything is set. I've gone to System-Admin.-Networking, put in my ssid, my wep key, and set it for dhcp, but it says it's unable to activate it, and I just don't understand why.

Any help greatly appreciated.

---

### Post by blue_thunder on 2006-06-18
Also, the driver is detected, so everything should work out fine?

---

### Post by blue_thunder on 2006-06-18
Wi-Fi Radar isn't detecting it either. This whole thing is driving me mad.

---

