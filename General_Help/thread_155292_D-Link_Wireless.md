---
title: "D-Link Wireless?"
date: 2006-04-04
forum: General Help
---

### Post by Spatulas on 2006-04-04
Hello all.  I haven't used linux before to any extent other than installing Redhat (bleh) at one time, so you'll have to forgive me for my relative noobyishness.

I have an IBM ThinkPAd R32 2658, specs are:
Celeron 1.5GHz, 256MB RAM, 20GB HDD, 14.1 XGA(1024x768) TFT LCD, 24x-10x CD-ROM, Modem(CDC), Ethernet(LOM), Li-Ion battery
PCMCIA Card: D-Link AirPlus DWL-650+

Now, I have installed without any problems, but now I would like to use my wireless.  I first got the wireless to work with no WEP or WPA, and that worked fine, but strangely I had to have both eth0 and wlan0 activated for the wireless to work (both are Wireless Connections, but it is odd because I only have the one card?).  Now, running a non-secure network is crazy talk, so I attempted to set up some form of Encryption, whether it be WEP or WPA.  My problem is that when I set that up, I could no longer connect to the router, despite having set up the key properly.  A quick lspci turned up:
> 0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #2) (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #3) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corp. 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801CAM IDE U100 (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801CA/CAM SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801CA/CAM AC'97 Audio Controller (rev 02)
0000:00:1f.6 Modem: Intel Corp. 82801CA/CAM AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
0000:02:07.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
0000:02:08.0 Ethernet controller: Intel Corp. 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
0000:02:09.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:03:00.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface

Does anyone have any ideas what I should try? Thanks.

---

### Post by funkydan2 on 2006-04-04
You won't get WPA support out of this card, since the ACX module only provides WEP support ([http://acx.sf.net)](http://acx.sf.net)).

You should be able to get WEP to work straight away.  If you set a HEX key on your Access Point, and put the same key into the network settings.  The ACX driver seems to be a little unstable when the SSID of the Access Point is not being broadcast.

The wireless card should be called wlan0, not eth0, so I'm not sure what's going on there.

My advice to you is to turn on your pc without any networking devices attached, once you've logged in, push your 650+ into the slot and wait for the power light to come on.  Then click the little networking icon in the system try and put in the settings for your wireless network.  That used to work for me (doesn't any more because I've updated to Dapper, and in Dapper the ACX support is currently broken, but hopefully will be working by June)!

Daniel

---

### Post by Spatulas on 2006-04-04
Well, now that you mention it, the power button nor the link light come on.... I noticed that the Link button didn't come on (forgot about the power one), but thought that was just a consequence of it all not working...  Any ideas on that front?

Thanks for all the info, I never would have found that tidbit on the WPA support myself :)

EDIT: I guess that is a seperate topic.  Posting a new thread.

---

### Post by Spatulas on 2006-04-05
Ok, it seems that the lights not turning on has nothign to do with it, because the device has power and everything...  Any other ideas as to what may be wrong?  I tested again with no encyption, the card works fine, so I am at a loss as to the cause...

---

### Post by Spatulas on 2006-04-05
Ok, sorry for the multiple posting and such.
I got it working, apprently this only works with WEP 64Bit HEX encryption, nothing above 64bit :P
Now, there is another network I would like to connect to and since it uses WPA I was wondering if there is anyway I can set it up to use WPA?  Thanks a lot.

EDIT: Read a bit on the ACX100 page... does wpasupplicant work in that regard?

---

