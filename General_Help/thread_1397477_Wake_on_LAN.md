---
title: "Wake on LAN"
date: 2010-02-03
forum: General Help
---

### Post by Black-Nobody on 2010-02-03
Dunno how many threads about this exists but this is the next one and I hope this is the right forum to post this :p

Well, a friend of mine has an old ubuntu server (can't tell you the ubuntu version but it have to be one of the newest one 'cause he just installed it 3 or 4 month ago) pc at home.
He activated wake-on-lan so i can start it myself.

Now our problem: 

I use the WOL Tool for Win7, I've added IP, MAC and subnetmask but the pc doesn't react on my magic packets and it can't display its status (it says the whole time that our server is offline even when its on).
Even my friend can't start it from the same network the server is in.

We tried a lot and think that the pc doesn't have a static IP when the power is off.
The only way to it is to broadcast the wakeonlan command to his whole network (send it via 192.168.1.255).

So my question:
What could be the reason for this non-static IP (I tried it with ifconfig eth0 192.168.1.210 but doesn't work).
The router is configured for this mac address, too.
It should guide the packets to the desired MAC address.

Is the subnet 255.0.0.0 the right one for WAN ?

What does SecureOn Password mean?
Sounds like a BIOS option for wol.

PS: Sorry, but my english is terrible.
My last basic english lesson was ~3years ago ;)

---

### Post by t4thfavor on 2010-02-03
I had some PC's that wouldn't wake if the bios had an option for low power mode. I think they were Dell brand. I just use my router, send it the MAC address and the PC wakes up. They do however have to support Wake on LAN, via the bios. 

That is the first place I would check.

I use the ubuntu package wakeonlan MA:CA:DD:RE:SS:00 to wake them up, and it works flawlessly. 

Good luck.

---

