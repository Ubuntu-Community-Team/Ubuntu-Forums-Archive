---
title: "Drivers for a really old computer"
date: 2010-05-28
forum: General Help
---

### Post by Arcaian on 2010-05-28
I have just installed Ubuntu on my old ThinkPad i Series 1600 2662. It's a really old computer, and I don't know where to find drivers for it. I have checked on the sites of IBM who made it when I bought it, and the newer compant that makes it now. Just wondering if anyone knew where I could get some drivers ?
 
Thanks in advance
 
Arcaian

---

### Post by jerenept on 2010-05-28
Drivers for what component exactly?

---

### Post by Arcaian on 2010-05-29
Sorry, that sounded like a nooby question. When I formatted I forgot to backup the drivers, so, everything. Thanks !

---

### Post by jocko on 2010-05-29
> **Arcaian said:**
> Sorry, that sounded like a nooby question. When I formatted I forgot to backup the drivers, so, everything. Thanks !
Exactly what part of the computer does not work?

---

### Post by Arcaian on 2010-05-29
Well, at this point in time I haven't done anything on it, so I don't know. I just presumed there would be no drivers.

---

### Post by jocko on 2010-05-29
> **Arcaian said:**
> Well, at this point in time I haven't done anything on it, so I don't know. I just presumed there would be no drivers.

Does the computer boot at all? Then you already have the correct drivers for most parts of the motherboard (ata/sata controllers, pci bus, etc...). 
Do you have network access? Then you already have the correct drivers for your network adapter.
Do you hear sound? Then you already have the correct sound card driver.
Do you get your monitor's native resolution? Then you probably already have the best available graphics driver.

Remember that in linux, most drivers are built in to the kernel, and the older the hardware is, the MORE likely it is that there is a driver for it already.

---

### Post by Arcaian on 2010-05-29
Cool ! Well everything except the network drivers are working the, but the problem is that I have a CD from Netgear to install the drivers, but I've been told even wth PlayOnLinux and Wine, installers don't work. Does this mean I'll have to be plugged in via a cable just to get the internet ?

---

