---
title: "Needs help to configure wireless networking"
date: 2006-02-28
forum: General Help
---

### Post by cantaresg on 2006-02-28
Hi,
I'm new to Linux and had just installed Ubuntu 5.10 just yesterday. Today I added a D-Link DWL-G630 PC card but I am at a lost trying to get a connected to a wireless network. Please help. Thanks a million.

---

### Post by ESM on 2006-02-28
Did you try it in system - administration -networking?

---

### Post by Sendervictorius on 2006-02-28
First, just see if it is going, out of the box. Go to Network Manager:  System>Administration>Networking, and see what you get. If it is ok, you should just be able to disable your ethernet connection, set up parameters in the wireless connection, and go.

Network cards are sometimes hard to get up and going, depending on what chipset the your card has. Sometimes diferent revisions of the same models of cards will have different chipsets. So you may have to troubleshoot.

If you have some problems with your card, and need to troubleshoot, I can recommend this guide:
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

Just doing a search on the forums may also show what others with your card have gone through.

The good news is that nearly always you can get it going.

---

### Post by DaMasta on 2006-02-28
You need to use ndiswrapper.
[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)

---

### Post by Sendervictorius on 2006-02-28
You may not need ndiswrapper with this card. It depends on which revision of the card you have. DWL-G630 rev. C uses madwifi drivers out of the box, for instance.

---

