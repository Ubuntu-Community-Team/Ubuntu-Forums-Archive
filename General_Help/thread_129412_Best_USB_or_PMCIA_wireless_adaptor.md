---
title: "Best USB or PMCIA wireless adaptor?"
date: 2006-02-13
forum: General Help
---

### Post by FlakJacket on 2006-02-13
I would like to know what the best supported USB or PCMCIA card WLAN adaptor is for Linux.  Preferably compatible with both wireless b and g.

Thanks,
Flak

---

### Post by dresnu on 2006-02-14
I have a Netgear WG511T pcmcia card which is an 802.11g standard compatible card. It was perfectly recognised in ubuntu 5.10 and works flawlessly. The only thing that I had to do was apt-getting the restricted modules for my kernel version from the repositories. I recomend it without any thoughts.

This page might also be usefull to you: [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

---

### Post by nomasteryoda on 2006-02-14
Howdy,

I use several Wifi PCMCIA cards all based on the Atheros chipset. All are 802.11g, which means they support 802.11b as well and the last 2 support 802.11a as well.

~$20 US - CompUSA:
[B]AT&T Plug&Share 54Mbps Wireless Notebook Adapter
Model No: 6700G
FCC ID: 07J-GL245401-1A1[/B]

dmesg shows:
ath0: Atheros 5212: mem=0x84000000, irq=11
ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
ath0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
ath0: H/W encryption support: WEP AES AES_CCM TKIP
ath0: mac 5.9 phy 4.3 radio 4.6

++++++++++++++++++++++++
~$35 US - Tigerdirect:
[B]SMC EZ-Stream Universal 2.4/5GHz Wireless Cardbus Adapter
Model No: SMC2336W-AG
FCC ID: RAZWN6301BARC
IC: 4711A-WN6301BA[/B]

dmesg shows:
ath0: Atheros 5212: mem=0x84000000, irq=11
Debugging version (IEEE80211)
ath0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
ath0: turboA rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
ath0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
ath0: H/W encryption support: WEP AES AES_CCM TKIP
ath0: mac 5.6 phy 4.1 radio 3.6

++++++++++++++++++++++++++++++++++++
$45 US - Office Depot:
[B]D-Link AirPlus XtremeG
Model No: DWL-G650
P/N: BWLG650NA.B5
FCC ID: KA2DWLG650B5[/B]

dmesg shows:
ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
ath0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
ath0: H/W encryption support: WEP AES AES_CCM TKIP
ath0: mac 7.9 phy 4.5 radio 5.6
++++++++++++++++++++++++++++

I like all 3 cards, but the nicest is the D-link. None have external antenna ports. You can purchase models from Orinoco that have external ports - good for your cantenna or roof-mount antenna (can be purchased cheap for ~$20).


Enjoy,
nomasteryoda

---

### Post by FlakJacket on 2006-02-14
thanks guys.  I think I may go with an orinoco just for experimenting with cantennae and such.  Are orinoco's supported just as well as the others you mentioned does anyone know?

Thanks,
Flak

EDIT: How do I know if I have a Cardbus slot on my laptop?

---

### Post by dresnu on 2006-02-15
Cardbus is the pcmcia slot. If you have it, you 'll see a slot(there might be 2) which is flat as if you had to insert a credit card. It's probably situated on the side of your laptop.

---

### Post by FlakJacket on 2006-02-15
OK that's what I thought but I just wanted to make sure.  I think I will get a ORiNOCO 11a/b/g ComboCard.  Is a PC card the same as pcmcia?

Thanks,
Flak

---

### Post by dresnu on 2006-02-15
yep, 
"The term "PC Card" referes to the credit card-size peripherals that add memory, mass storage, and I/O capabilities to computers in a rugged, compact form factor. The term "PCMCIA" (Personal Computer Memory Card International Association) refers to the non-profit trade association and standards body that promotes PC Card and ExpressCard technology by defining technical standards and educating the market. In the past, cards were known as "PCMCIA Cards", but the industry now refers to products based on the technology as "PC Cards," "PC Card Hosts" and "PC Card Software," and refers only to the association as PCMCIA."

---

