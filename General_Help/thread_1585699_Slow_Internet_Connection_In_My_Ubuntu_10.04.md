---
title: "Slow Internet Connection In My Ubuntu 10.04"
date: 2010-09-30
forum: General Help
---

### Post by pankaj.sea on 2010-09-30
Hi!
I have dual boot OS and I'm using Ubuntu with Win 7. Previously I was using Fedora but I thought to change the flavor! So I installed Ubuntu, but now I'm truly facing problem with my Internet connection! Its too slow in Ubuntu, the both surfing and downloading speed!
Usually in windows I get 200-400 kbps download speed when downloading a file and if I download the same file in Ubuntu using flashget I'm getting only 60-70 kbps speed!
:( Also the surfing is too slow!
My broadband's bandwidth is 2.1 Mbps!
Any suggestion? :confused:

---

### Post by ioannisb on 2011-08-22
I have the same problem. Did you find a solution?

---

### Post by Mark Phelps on 2011-08-22
> **ioannisb said:**
> I have the same problem. Did you find a solution?

The difference in download speeds between the different OS's is probably entirely due to the different network drivers in place for each OS.

I enountered exactly the same problem with an older release of Ubuntu.  But fortunately, I was using a Marvell network chipset at the time, and the Marvell website had downloadable Linux device drivers.

All you can really do is check the network chipset provider's website for Linux driver versions.  If they don't have any, you're stuck using the drivers installed with Ubuntu -- and there's really nothing you can do to increase the networking speed.

---

