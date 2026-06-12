---
title: "Unnecessary Unity updates"
date: 2012-01-09
forum: General Help
---

### Post by ully-mick on 2012-01-09
Ubuntu 11.10 Classic. 
I don't use Unity, so I completely removed Unity to stop unnecessary updates. same with Banshee, I use Audacious.
But even though they are both removed from my system, they still try to update every time. is there anyway to stop this but still update the rest of my system? as it is now I'm having to scroll through the updates and untick all the unuty/banshee stuff.

thanks.

Mick.

---

### Post by Double.J on 2012-01-09
> **ully-mick said:**
> Ubuntu 11.10 Classic. 
I don't use Unity, so I completely removed Unity to stop unnecessary updates. same with Banshee, I use Audacious.
But even though they are both removed from my system, they still try to update every time. is there anyway to stop this but still update the rest of my system? as it is now I'm having to scroll through the updates and untick all the unuty/banshee stuff.

thanks.

Mick.

how did you remove them? if update is finding them, it seems likely something of the packages is left on your sysem?

---

### Post by ully-mick on 2012-01-09
ah, right. not sure, it was October/November time when I did it. I think banshee was removed through the software centre or synaptic, and unity from instructions on here or somewhere else on the web.
I've just done "sudo apt-get remove --purge banshee" and "sudo apt-get remove --purge unity" see if that sorts it. should've done that before posting, sorry :oops:

thanks.

Mick.

---

### Post by bluexrider on 2012-01-09
sudo apt-get autoremove "***package***"

removes the package, and all it's dependencies.

---

