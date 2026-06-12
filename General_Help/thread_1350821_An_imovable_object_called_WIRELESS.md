---
title: "An imovable object called WIRELESS"
date: 2009-12-09
forum: General Help
---

### Post by bristolbadger23 on 2009-12-09
Using a bewildering array of help pages and tools I have some how got the wireless card recognised, and able to see networks.

[INDENT]
00:06.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

          Cell 03 - Address: 00:1B:2F:F1:8D:CC
                    ESSID:"dad"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:46/100  Signal level:-66 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

[/INDENT]

So now, i open any of the 4 or so (apparent) network managers, and none are able to get me on-line for one reason or another. It's to do with WPA I think, but I'm not sure.

**Network manager** seems the most competent, until you realise it only asks for WEP keys, ignoring the 8 or so the forms of authentication, including the one i have setup, WPA-PSK...

**Wifi-radar** is a bizarre little tool that gives no cluse, makes no sense and I have no clue what to enter under "Use WPA - Driver"... and some others...

**IW** Didn't work...

**ndiswrapper** Looked the part, but reported driver not present, then verified that it was and essentially was unrelaiable and throught that there was nodrive so wasn'tr vb;cjfhb cvcvvcvb bored.. and fed up now... [ejects toys from pram]

And there were another two but i have forgotten what they were.

In short, this appalling support for such a basic, and widespread requirement has eaten over 8hours of my time and all i have to show for it is a headache.

I'm Running: Jaunty and my network card is a Netgear WG311v3. A seemingly unheard of combination that i must be mad trying to make work together...

---

### Post by coffeecat on 2009-12-09
Your problem is:

> **bristolbadger23 said:**
> Marvell Technology Group Ltd.

Of all the chipset manufacturers to have the bad luck to come across, that could very well be the worst. Please don't blame Linux or Ubuntu for your woes. There are some hardware manufacturers that can't/won't co-operate with the Linux kernel devs. One could ask, if Intel can work with the Linux community, why can't other HW manufacturers? But I don't know the answer.

Anyway, to save yourself any further headaches, I have one piece of well-meant advice. You are in the UK. Go to...

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

... and spend a mere £23 on a wireless card guaranteed to work in Ubuntu.

---

