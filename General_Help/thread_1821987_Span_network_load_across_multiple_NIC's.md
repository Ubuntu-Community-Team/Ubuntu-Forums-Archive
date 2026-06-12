---
title: "Span network load across multiple NIC's"
date: 2011-08-09
forum: General Help
---

### Post by perceptus on 2011-08-09
I have a box currently setup to share files on my network and for the most part its great.  However when multiple people request files my 1gb speeds drop.  I have extra 1gb NIC's to use but have no clue on how to spread the load of transfering files between multiple nics.  Is this even possible? or does this happen automagically?

Thanks for input.

---

### Post by Synoc on 2011-08-09
near as I can figure, unless you set up the NICs to go to separate routers, they will all go through the one. high end routers can route traffic based on load, but the PC... I do not think so, but Linux rarely says no to anyone. the question is how far down this rabbit hole are you willing to go?  the IP address is tied to the PC name. not the NIC on the PC. Multiple NICs to the same PC name requires multiple networks and multiple routers and thus get multiple IP addresses.  

Also the other problem is the processor power required to move that much data to multiple PCs. it's another bottleneck to overcome

---

### Post by dcstar on 2011-08-10
> **perceptus said:**
> I have a box currently setup to share files on my network and for the most part its great.  However when multiple people request files my 1gb speeds drop.  I have extra 1gb NIC's to use but have no clue on how to spread the load of transfering files between multiple nics.  Is this even possible? or does this happen automagically?

Thanks for input.

Load balancing NICs usually require that capability in the NIC as well as complementary capability on the Ethernet switch side.

If the "speed" drops when multiple people use your server most likely the disk I/O will be the bottleneck, not the NIC. You can see this in the System Monitor, unless the NIC remains at around 100% utilisation then something else is slowing things down.

You can also use the **top** command to see the I/O wait percentage when the server is heavily loaded.

---

