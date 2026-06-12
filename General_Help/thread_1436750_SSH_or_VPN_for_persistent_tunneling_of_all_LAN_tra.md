---
title: "SSH or VPN for persistent tunneling of all LAN traffic from router?"
date: 2010-03-23
forum: General Help
---

### Post by jm27 on 2010-03-23
I am currently setting up a old box to serve as a general, quality router/fileserver that should give me fine control over my network traffic. This router will serve as the bridge between several local users and the Internet, along with quite a few machines.
 
Traffic is expected to be heavy, in the sense of multiple powerusers using the Internet to the fullest, not from one machine doing anything insane like Torrenting. The connection profile will reflects lots of up and down, not necessarily a huge number of persistent connections.
 
Due to security concerns, the need to build an encrypted tunnel between a SoHo LAN and a dedicated server is unescapable. I'm trying to determine whether I can pull this off with a simple SSH tunnel on the box serving as the local router, or if a VPN (either PPTP or L2TP) is a more appropriate solution.
 
Proxying won't work, because not all apps can easily be socksified across the Windows, GNU/Linux, and OSX platforms that the users will need. For this reason, I have to pull this off strictly at the router level.
 
I'm not all that familiar with the specific details of each protocol's performance as far as their latency, efficiency, overhead, and fault-tolerance are concerned. I'm less concerned with a protocol taking up CPU as I am with useless bytes and latency it might be introducing to the link. I don't know the low-level nitty gritty of how each protocol encapsulates its traffic.
 
If there is an existing package for this, it would be great, but at this point I'm simply trying to figure out which protocol is more appropriate before I begin digging in the wrong direction. The biggest concern, of course, is that the chosen protocol aggressively re-establish sessions should the connection suddenly drop, which will be a concern given the SoHo line I'll have to work with. The actual outbound server is no concern, as it has four cores and a Gbps line.

---

### Post by jm27 on 2010-03-23
Oops, I meant to post this in the networking subforum. Can a mod help me out with a move?

---

