---
title: "Bittorrent blocks all other internet traffic"
date: 2010-05-06
forum: General Help
---

### Post by Totenglocke on 2010-05-06
When I use Transmission to download a torrent, it completely blocks all other internet traffic on my home network.  Even if the torrent isn't downloading or connected to more than a few peers, it blocks everything else.

Any ideas?

---

### Post by Flyers2391 on 2010-05-06
> **Totenglocke said:**
> When I use Transmission to download a torrent, it completely blocks all other internet traffic on my home network.  Even if the torrent isn't downloading or connected to more than a few peers, it blocks everything else.

Any ideas?

This used to happen to me when I tried to upload ubuntu images ... traffic wouldn't necessarily be blocked but web sites would be amazingly slow.  I chalked it up to Comcast seeing P2P traffic and, assuming it was illegal, rate shaping my connection to nearly nothing

---

### Post by Totenglocke on 2010-05-06
No, my ISP doesn't filter bittorrent and using Linux Mint with Transmission up until I switched to 10.04, I never had this issue.  It's not that pages are slow to load, it's that NOTHING outside of bittorrent will work, even if it's not downloading at all.  As long as there is a torrent that isn't paused, everything but bittorrent is blocked on my network.

It seems like it's opening too many tcp connections and overloading the router, but that doesn't make sense when it happens even if it's only connected to 6 peers.

---

### Post by Totenglocke on 2010-05-07
I solved the issue.  I turns out that by default the firewall in Ubuntu was blocking the port Transmission was using, yet it was still able to connect and due to the port being blocked, it kept opening up an ever increasing number of TCP connections. Opening up the port fixed the issue.

*EDIT*
Aaaand the next day it decided to stop working again.  Nothing was changed on the firewall, yet it decided to close the port and nothing I did would reopen it.  Fan-freaking-tastic.

---

### Post by reyquito on 2010-07-04
I'm having the same problem. However, I haven't been able to solve it. Have you? As long as I can see, my FW is not even running.

---

### Post by flight243 on 2011-04-18
Did you solve this? How?

I'm running 10.04 LTS on 3 computers and I'm having connection issues in all of them when I download a torrent, even if I set up a very low download speed and max connections in the torrent client.

In one of these 3 computers I also run Arch and everything works fine there so this is a problem i only have with Ubuntu :$. My firewall is not running in neither of them.

Thanks!

---

