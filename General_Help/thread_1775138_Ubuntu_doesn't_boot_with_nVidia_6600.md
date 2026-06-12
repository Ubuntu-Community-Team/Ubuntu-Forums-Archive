---
title: "Ubuntu doesn't boot with nVidia 6600"
date: 2011-06-04
forum: General Help
---

### Post by frankplummer on 2011-06-04
Good afternoon all!

I have a little dilemma.

Yesterday evening I decided to get Photoshop CS5 working with WINE on my Ubuntu 11.04 install, which resulted in great success. Somehow in the process however, I managed to screw up my GLXDock - it wasn't rendering correctly. Despite numerous reboots along the way it still remained a mess, but I digress, that isn't the issue (just some background info if that helps!)

My motherboard has an integrated Intel graphics chipset. Now, since yesterday evening, I haven't been able to boot into Ubuntu using my nVidia 6600 - which I have been able to do for months previous now. Whether it was something I had changed, or an update that killed it I do not know. Booting normally, it will hang on the plain purple splash screen (not even getting to the "Ubuntu" splash) Even when I boot into recovery mode, the system comes out with a "Bad EIP Value" and hangs but ONLY when I have my nVidia card installed. If I take the card out and boot with integrated Intel, it boots to the desktop by the normal means fine and boots to recovery.

I've exhausted all my ideas guys (I'm used to Ubuntu Server - no graphics at all!!) and I'd really appreciate some help.. :(

Thanks in advance!
-Frank

---

### Post by frankplummer on 2011-06-04
If it helps, this is the result I get with the nVidia card installed upon booting to recovery mode. It hangs hereafter.

[IMG]http://i52.tinypic.com/24e86k9.jpg[/IMG]

---

### Post by frankplummer on 2011-06-04
Problem solved!!

The issue I found was that since a recent update, the nouveleau drivers in Ubuntu weren't working with my nVidia 6600 (this was probably thanks to me deciding to uninstall at the nVidia drivers when I panicked about my Dock). Why this was an issue in recovery mode I don't know - maybe a bug to look at Ubuntu devs - but upon attaching "nomodeset" to my bootline I could boot into Ubuntu, blacklist the nouveleau drivers and install the nVidia drivers from their website via the *.run script.

Thanks to all those that may have looked, but it's sorted now. :)

---

