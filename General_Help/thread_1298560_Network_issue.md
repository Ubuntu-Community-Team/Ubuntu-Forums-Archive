---
title: "Network issue"
date: 2009-10-23
forum: General Help
---

### Post by KlinerDraken on 2009-10-23
After I changed the IP range on my router I can no longer get to the internet with Ubuntu 9.04. 

I get a valid IP address and I can ping the router but I can not ping google.com by URL or IP. My windows VM on my ubuntu host is what i am using to post this, so it works.

any ideas what i can try to get it working again?

:confused:


> ifconfig eth0 down
ifconfig eth0 up
dhclient eth0

did not work


---

### Post by KlinerDraken on 2009-10-23
ok not sure why this fixed it but i changed the ip range again form ###.###.0.0 to ###.###.1.1 and now its working again.

anyone know why that matters?

---

### Post by jbrown96 on 2009-10-23
Routers use ~0.0 for their own ip address. When you need to communicate with the actual router, you talk to that address. If the router is trying to give out that address then there may be a problem with ip address assignment, arp calls, and other low-level network communication. 

Ideally it shouldn't matter, but since every network uses that, many applications just assume that the router uses it. Ubuntu could just be making a poor assumption that it can request an ip from that address, and since you were using a non-standard config, Ubuntu didn't know where else to ask.

---

### Post by KlinerDraken on 2009-10-23
> **jbrown96 said:**
> Routers use ~0.0 for their own ip address. When you need to communicate with the actual router, you talk to that address. If the router is trying to give out that address then there may be a problem with ip address assignment, arp calls, and other low-level network communication. 

Ideally it shouldn't matter, but since every network uses that, many applications just assume that the router uses it. Ubuntu could just be making a poor assumption that it can request an ip from that address, and since you were using a non-standard config, Ubuntu didn't know where else to ask.

Ubuntu was getting IP ~0.100 the router had ~0.0 but I couldn't connect to the router web page or to any external sites when i changed the router back to ~1.1 it started working again.

---

