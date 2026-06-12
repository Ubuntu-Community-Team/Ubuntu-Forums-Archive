---
title: "Setting up wireless internet"
date: 2010-01-31
forum: General Help
---

### Post by crazycoolzac on 2010-01-31
I am currently running 9.10 ubuntu and am trying to set up wireless internet. I am the administrator so I can acquire any information needed. I am asking how to use my Dynex Wireless G USB adapter (Model: DX-BUSB) to connect to a modem down the hall. I'm assuming I need some drivers of some sort but I am unfamiliar with linux so I am unsure of how to set this up. Please help.

---

### Post by blueshiftoverwatch on 2010-01-31
It might already be working right out of the box. There should be an icon for NetworkManager on your upper panel that will list all wireless points within working range and let you select the one you wish to use.

---

### Post by crazycoolzac on 2010-01-31
Nope, no wireless networks are listed.

---

### Post by Jotham on 2010-02-01
Do you have a wireless router set up?

---

### Post by crazycoolzac on 2010-02-01
yes, i'm duel booting with windows xp so I know the routers working fine.

---

### Post by kayaksmak on 2010-02-01
You might need to install restricted drivers.  I had to do that for my Broadcom wireless card.  Go to **System->Administration->Hardware Drivers**.

[edit] or you might need to add whatever network you're trying to connect to if it's a hidden network.  just right click on the Network Manager icon, click **Edit Connections**, and under the **Wireless** tab, click **Add...**

---

### Post by t4thfavor on 2010-02-01
OK, so you do have a wireless network, already in the building. 

You first need to figure out if your OS can use the wireless card you have by typing:

```

iwconfig

```

Then look for something like

```

wlan0     IEEE 802.11bg  ESSID:"123479876"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:18:84:19:BD:59   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=28/70  Signal level=-82 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

If you have any entries other than the ones that say "no wireless extensions" then you are almost there.

Next check the network manager at the top right of you screen to see if it has any networks listed.

If your ssid is not broadcast you will have to set that up manually using the "Connect to Hidden Wireless Network" option at the bottom of network manager's right click menu.

If you got no wireless cards back in the first command, you should post in the wireless section on how to get your card installed properly.

Perhaps a mod could move this thread there in that event.

---

### Post by Jotham on 2010-02-01
Okay, just making sure.

I don't know if you checked, but [this]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") is a pretty good resource.

Other than that, every time I have to set up wireless on a fresh installation of Ubuntu, I have to plug my computer into a wired connection while I do it. The drivers may also be on the install disc.

---

### Post by crazycoolzac on 2010-02-01
I'll have to check tommorow, my power being shut off in 4 minutes.

---

