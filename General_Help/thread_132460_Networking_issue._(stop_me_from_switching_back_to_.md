---
title: "Networking issue. (stop me from switching back to windows. please.)"
date: 2006-02-18
forum: General Help
---

### Post by Vilhelmo on 2006-02-18
I've got two problems. 
The first is that my wireless networking keeps freezing all the time, sometimes every five minutes sometimes every hour. Sometimes it just comes back after a while, sometimes i can fix it by deactivating the wireless network card and reactivate it again. That is my first problem. I use ndiswrapper with windows xp drivers for my Dlink g520+ card. It seems that the card loses the signal every now and then. Some info from iwconfig: ```
 Bit Rate:54 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3
          RTS thr:4096 B   Fragment thr:4096 B
          Power Management:off
          Link Quality:100/100  Signal level:-73 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

My second problem is that sometimes when i reactivate my network card the whole computer freezes, the music hangs, the mouse stops moving and I have to press the reboot button on the computer. This also happens when I leave the computer on for a week and then comes back to use it. 

I know wireless networking is a tricky issue but some suggestions would be great!

---

### Post by SVFUSiON on 2006-02-18
Well it sounds like the drivers are causing that, try using older/newer drivers for your wlan card, also just try hardwired, it could just be your networking in general.

---

### Post by Vilhelmo on 2006-02-18
I think I've figured out a problem. When i run iwlist scan the router that comes up is "Protocol:IEEE 802.11b" but with iwconfig my card seems to be set up to " IEEE 802.11g".  So how do I change the protocol the card uses? edit: my router is a 802.11g router. but with iwlist scan it show 802.11b, maybe it might work better with that protocol?

---

### Post by nalmeth on 2006-02-18
Your card may have support in the kernel, but if not at least you have ndiswrapper. I have heard that newer versions of ndiswrapper (not yet in repositories) solve a lot of problems, including network performance. If you haven't yet, read thru this, and maybe you'll find something out about your situation:

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

---

### Post by racyrefinedraj on 2006-02-18
Dude! the g-520 is an atheros chipset! have you tried the [Madwifi]("http://madwifi.org") drivers? If not, do so. Definitely easier than NDISwrapper. The website says that the g-520 is supported, but doesn't mention the g-520+ either way. 

Of course, if you've already tried that, then my apologies.

---

