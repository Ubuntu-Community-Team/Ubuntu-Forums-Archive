---
title: "ndiswrapper"
date: 2006-03-01
forum: General Help
---

### Post by BrejoSacor on 2006-03-01
Alright, here is the dilemma....
   I am reading the wiki guide for installing my WLAN card, and I needed to install Ndiswrapper, guide [here]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto").  I have run lspci and it returned. This along with all my other hardware:
```

0000:02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
```

Now the next step was to download the specific driver, which i did, however it was R90501.EXE.  I need to know how to get the specific .INF and .SYS file from that.  I can't really proceed with the driver install without those files, and the Wiki was no help with extracting it besides it saying 'unzip/cabextract/unshield"

Anyhelp would be great....

---

### Post by ivanhelguera on 2006-03-01
Hi, 
try googling for the 'driverers broadcomm', and you'll find probably the right files. 
I used broadcom ndiswrapper twice, and my advice is to try both bcwl5.inf (XP driver) and bcmwl5a.inf (W98 one) if the former fails to work. 
best , iH

---

