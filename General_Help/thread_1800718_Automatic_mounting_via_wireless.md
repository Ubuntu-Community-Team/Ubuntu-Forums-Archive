---
title: "Automatic mounting via wireless"
date: 2011-07-09
forum: General Help
---

### Post by ElToro on 2011-07-09
I have a problem mounting a NFS server share at startup (fstab) from a laptop that connects to my LAN via a WLAN USB stick.

It's an old HP-laptop, running Ubuntu 11.04, that I use for music only (It has a couple of good Harman Kardon speakers integrated). It connects to the LAN via a D-Link DMA140 (WLAN USB-stick). 

To get the stick to work, I had to include the following in rc.local (so that it runs on every start-up):

```
sudo modprobe rt2870sta
```

I also want to mount a network share (on my music server) on start-up, using NFS. The normal thing would be to add the mount-command in the fstab, but the laptop is not connected until rc.local runs. I have tried to put the mount in rc.local after the code above, but it times out before the laptop is connected to the LAN.

I guess I could (1) put the modprobe-code somewhere else, that runs before rc.local, or (2) run some kind of check that the laptop is connected to the LAN before trying mount, but I am not sure how to achieve this.

Any advice would be greatly appreciated. :)

---

