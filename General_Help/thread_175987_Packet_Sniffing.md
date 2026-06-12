---
title: "Packet Sniffing"
date: 2006-05-14
forum: General Help
---

### Post by skippy81 on 2006-05-14
Sorry to make another ethereal thread, but there is something that is confusing me.

Is it possible for me to use a PC with 2 lan cards in it to packet sniff a network without being assigned an IP - ie tap into the network without being part of it?  Traffic would pass right through the two lan cards and I would just sniff it as it went through.

---

### Post by steve.horsley on 2006-05-14
That's called bridging. I'm sure Linux can do it, but I don't know how to configure it. A google search for **linux bridging** should turn up some details.

---

### Post by cgjones on 2006-05-14
**bridge-utils** is the package you'll need. **brctl** is the command. Snort or maybe **tcpdump** can be used to actually log the packets.

---

### Post by skippy81 on 2006-05-14
Thankyou guys, i got some great tutorials on bridging now :D

---

