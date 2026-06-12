---
title: "ethernet problem on hp nx6100 notebook"
date: 2006-04-26
forum: General Help
---

### Post by Hurin on 2006-04-26
I just can't get my eth0 interface to work. I configure it same as I configured my other desktop computer, so the problem isn't in configuration.

I tired to locate the problem and cam upt with this:

$ dmesg | grep eth0
[4294705.624000] b44: eth0: Link is up at 100 Mbps, full duplex.
[4294705.624000] b44: eth0: Flow control is off for TX and off for RX.

The problem is in last line. It shoudn't be there. I think that's why the LAN doesn't work.

Doeas anyone know a possible solution for this problem? I'd be more than grateful!

THanks.

---

