---
title: "Wireless problems"
date: 2006-05-24
forum: General Help
---

### Post by werthog on 2006-05-24
I've been wanting to get some experience working with Linux, so I installed Ubuntu 5.10 on a three-year-old IBM Thinkpad T40. So far, I've been doing all right, but I'm having some trouble getting connected to the Internet. I've spent the last few evenings trying to work this out on my own, and I'm finally down to my last resort: asking for help ;)
My network setup at home is a bit... *unique*, to say the least, which exacerbates my problem a bit. Due to our location, we can only get online by dialup. We connect through an old Apple Airport base station with a built-in modem. No security or any other special settings; nobody lives close enough to get a signal anyway :p . The other laptops we use, a few iBooks and an HP, all work fine without any setup.
The Thinkpad I've installed Ubuntu onto uses a built-in wireless card with an Atheros chip, which is supported by the MadWifi drivers that come with Ubuntu from what I've read [here]("http://madwifi.org/wiki/UserDocs/Distro/Ubuntu") and [here]("https://wiki.ubuntu.com/WifiDocs/Driver/Madwifi?highlight=%28madwifi%29#head-d0c9537f2f0e28b3497fa4872c6bb76bce9755c9"). My experiences seem to corroborate this, as not only does Ubuntu recognize the wireless card, but it even seems to connect to my wireless network; In the Network administration window, my network appears in the appropriate drop-down box, and the output from iwconfig and ifconfig appear (at least to my untrained eye) to confirm that I'm connected to the network. However, no programs can connect to the Internet; I can't even ping google.com. I've also experienced the same exact issue with a NetGear PC card, which also uses the MadWifi drivers.
What could possibly be causing this problem? I have very little experience with networking, but I can tell you that I've set my Thinkpad to configure by DHCP, and the Airport Admin Utility on my iBook tells me that the Airport station is set to "Share a single IP address (using DHCP and NAT)" and also provides the alternative option to "Share a range of IP addresses (using only DHCP)" with a customizable range. This is about the limit of the Airport station's network settings.

Sorry if I've given too much information, I just thought I'd provide as much as possible to save time later :) I'd really appreciate any help you can provide, as this is probably my best option for getting online with this computer; I don't have a way of connecting by ethernet (yet), and from what I've read, the modem is a lot tougher to get working than the wireless card. Thanks for any help, but don't sweat it if you can't figure it out. I'm mainly doing this for the experience, and I won't be heartbroken if I can't get this working :p Either way, I've already learned a lot.

---

### Post by werthog on 2006-05-25
Just realized that there's a forum for network issues. I'll take this there.

---

