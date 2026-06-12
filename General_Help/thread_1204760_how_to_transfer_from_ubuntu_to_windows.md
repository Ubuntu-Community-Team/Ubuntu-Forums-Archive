---
title: "how to transfer from ubuntu to windows"
date: 2009-07-05
forum: General Help
---

### Post by rajanm1 on 2009-07-05
i want to transfer files from ubuntu to my vista pc but don't want to use a usb or 3rd party devise cos that takes to long. is there a way that i could directly connect my ubuntu netbook to my pc and transfer large files this way?

thanks

---

### Post by diablo75 on 2009-07-05
Well you'd have to do it via a network connection for starts (or that would be the best way) and how you go about setting the network depends on whether or not you have a router or switch available.  And if neither of those are available, then you'll have to use a "cross-over" Ethernet networking cable instead of the standard Ethernet cable.

You could then setup a shared folder on your Vista machine and allow Ubuntu access to it, then copy the files out of that share into your Ubuntu system.

Another way you might consider is to physically remove the hard drive from the Vista machine, set it to be a slave, boot Ubuntu up and copy the files out that way.  (Just read your post again....) Since you're using a netbook... I guess that counts this option out unless you had a USB adapter that would allow you to treat a normally internal HD as an External.

---

### Post by ivanvajar on 2009-07-05
Just connect them directly 

> "***cross-over***" Ethernet networking ***cable*** instead of the standard Ethernet cable.

This is VERY important.

---

### Post by rajanm1 on 2009-07-05
> **diablo75 said:**
> Well you'd have to do it via a network connection for starts (or that would be the best way) and how you go about setting the network depends on whether or not you have a router or switch available.  And if neither of those are available, then you'll have to use a "cross-over" Ethernet networking cable instead of the standard Ethernet cable.

You could then setup a shared folder on your Vista machine and allow Ubuntu access to it, then copy the files out of that share into your Ubuntu system.

Another way you might consider is to physically remove the hard drive from the Vista machine, set it to be a slave, boot Ubuntu up and copy the files out that way.  (Just read your post again....) Since you're using a netbook... I guess that counts this option out unless you had a USB adapter that would allow you to treat a normally internal HD as an External.
how can i tell the difference with a normal and a cross over cable?
could i just setup a shared folder over wi-fi on my vista pc? how can i do that?

---

### Post by 3rdalbum on 2009-07-05
> **rajanm1 said:**
> how can i tell the difference with a normal and a cross over cable?

It says "cross over" on the box, and maybe on the cable. I'm not joking - to my knowledge that's the only way you can tell. Some Ethernet cards can communicate directly without the need for crossover cables, too (often known as "Automatic MDI/MDI-X", "Auto uplink and trade", "Universal Cable Recognition" or "Auto Sensing").

> could i just setup a shared folder over wi-fi on my vista pc? how can i do that?

Setting up a shared folder over Wifi is likely to be slower than using a USB flash drive - wireless G only goes at 54mbps in peak conditions. With an Ethernet cable, you can get 100mbps or better.

Right-click on a folder that you want to share on your Ubuntu machine and choose Properties. Then click the Share tab. If you don't have Samba installed, you should be asked if you want to install it. Once it's installed, you can click "Share this folder". Give the share a short name and click "Create This Share".

When you connect your Windows PC to the Ubuntu machine and go to Network (or Network Neighbourhood or whatever it's called on Windows), you will be able to see the Ubuntu machine and its share. You will need to provide your Ubuntu login details in order to log into the Samba share, and then you can copy files to and from that folder.

---

### Post by alphacrucis2 on 2009-07-05
> **rajanm1 said:**
> how can i tell the difference with a normal and a cross over cable?
could i just setup a shared folder over wi-fi on my vista pc? how can i do that?

Yes you can use wifi but it isn't as fast as cable. If both machines have gigabit ethernet cards and you hook em up with a cat 5+ or cat 6 cables (you may or may not need a crossover as auto MDI is a feature of many gigabit cards). If you do need a crossover then go to a shop and buy one. They will specify which are crossovers and which are straight through. In any case with gig ethernet ports you are looking at a raw TX speed of 1000 mb/sec versus 56 mb/sec for wifi. Of course you won't actually achieve those as real throughput in either case but even 100mb ethernet will beat wifi. If comes down to convenience versus speed.

---

### Post by 7raTEYdCql on 2009-07-05
If you are using an ext2 fs then check this out. [www.fs-driver.org](www.fs-driver.org).

---

### Post by alphacrucis2 on 2009-07-05
> **3rdalbum said:**
> It says "cross over" on the box, and maybe on the cable. I'm not joking - to my knowledge that's the only way you can tell.



If the connector plug is clear plastic then you can tell, as you will be able to see the colour ordering of the individual wires. If the connector is opaque then you are out of luck without a cable tester. Sometimes the connector boots are colour coded to help, such as a red boot signifies a crossover.

---

