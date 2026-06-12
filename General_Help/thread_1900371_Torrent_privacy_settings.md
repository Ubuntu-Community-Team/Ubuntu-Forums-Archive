---
title: "Torrent privacy settings"
date: 2011-12-26
forum: General Help
---

### Post by Condor Cluster on 2011-12-26
Just had a look at [http://www.youhavedownloaded.com/](http://www.youhavedownloaded.com/), was a bit unnerved that it picked up one of my downloads from a while back.

What are the best setting to have in Transmission to maintain privacy? I have a blocklist added to Transmission ([http://www.bluetack.co.uk/config/level1.gz](http://www.bluetack.co.uk/config/level1.gz)), along with my current settings:

[I]Encryption mode: Prefer Encryption
Use PEX to find more peers
Use DHT to find more peers
Use Local Peer Discovery to find more peers
Use UPnP or NAT-PMP Port Forwarding for my Router
Enable uTP for peer communication[/I]

Thanks

[]("http://www.youhavedownloaded.com/")

---

### Post by Boondoklife on 2012-01-23
Well if you are going for security, I would disable: PEX, DHT, LPD, UPNP, and uTP

on top of that you should "Require" encryption.

You may wanna look into merging multiple blocklists from that site, and others, into a master list with an app like blocklist manager. It can compress the ranges by getting rid of overlapping/duplicate ranges.

---

