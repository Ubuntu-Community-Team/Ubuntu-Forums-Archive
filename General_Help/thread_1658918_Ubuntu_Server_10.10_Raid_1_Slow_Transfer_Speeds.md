---
title: "Ubuntu Server 10.10 Raid 1 Slow Transfer Speeds"
date: 2011-01-03
forum: General Help
---

### Post by harveyd on 2011-01-03
I have just built my first Ubuntu Server based NAS and I am getting slow transfer speeds.

The Server consists of the motherboard 
NC9C-550-LF 1.5GHz Dual Core ATOM N550
with 2GB RAM.

The server has three drives
#1 Single 2.5" 5400rpm Drive with Ubuntu 10.10 server

2x Samsung 1.5TB 5900rpm 3.5" Drives in Raid 1 using linux software raid for Data.

All devices in the network are connected through gigabit Ethernet and have confirmed that each device indeed recognizes that it is connected at Gigabit speed.

The problem I have is that when copying across the network I am averaging 10-11MB/s. I am using SCP to do the copying.

I am trying to work out where the problem is. The SCP speeds are pretty much the same if I copy to the OS drive (sda) or the raid (md0). I have also used hdparm (hdparm -tT /dev/md0 and hdparm -tT /dev/sda) and the speeds look ok, see the results below:-

/dev/md0:
 Timing cached reads:   1560 MB in  2.00 seconds = 780.31 MB/sec
 Timing buffered disk reads:  310 MB in  3.00 seconds = 103.19 MB/sec

/dev/sda:
 Timing cached reads:   1564 MB in  2.00 seconds = 781.75 MB/sec
 Timing buffered disk reads:  194 MB in  3.03 seconds =  64.10 MB/sec

This leads me to think it's network related. The logic board has 2x Gigabit  Realtek RTL8111E PCI-E ports.

Can anyone point me in the write direction to get the transfer speeds up.

---

