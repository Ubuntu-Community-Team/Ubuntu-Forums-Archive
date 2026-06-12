---
title: "Ubuntu IP Stays on Network"
date: 2006-02-15
forum: General Help
---

### Post by kenobi25 on 2006-02-15
I'm working with an ubuntu machine in an office where we use static IP addresses and I am using one in my ubuntu machine to connect to the network/internet fine.  Occasionally I need to shut down my ubutnu machine and use its' IP in another computer (windows or linux) but despite unplugging the machine from power and the network, the IP still appears to be in use on the network.  Is there a way to force that IP free on the network when ubuntu is shutting down, or is this not a problem for anyone else and there is something strange about our network here?

---

### Post by steve.horsley on 2006-02-15
What makes you think the IP is still there? I think it is rather unlikely. Can you ping the address after unplugging your PC? 

It is possible (likely) that the unplugged PC's MAC address is still lingering in the ARP caches (IP address -> Ethernet address lookup tables) of other devices on the network. This will cause problems for a while, until the old entries are aged out and discarded, because that wquipment will be sending packets to the wrong (and now gone away) physical address. You may have to wait up to perhaps 30 minutes for the ARP cache entries to age out. Different kit has different timeouts. Some can have their caches cleared manually, but it's not easy to find out how.

---

