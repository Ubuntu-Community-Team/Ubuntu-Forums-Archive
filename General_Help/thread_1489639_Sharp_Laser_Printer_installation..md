---
title: "Sharp Laser Printer installation."
date: 2010-05-21
forum: General Help
---

### Post by Quiane on 2010-05-21
The laser printer in question is a sharp am-900.  It will not auto detect, and i'm running a virtual machine (with USB passthrough) and cannot see the usb connection on the virtual winxp installation i'm running.

So, i'm wondering if anyone can give me any tips on using fstab to find the mount point of the printer to install a generic driver, or if anyone has a .ppd file for that printer it would be GREATLY appreciated.

Failing that if anyone has any tips at all (including "it wont work dude" but in a way more technical way) it would still be appreciated!

Thanks!

---

### Post by Objekt on 2010-05-21
What virtualization software are you using?  I only know Virtualbox, but I'm sure someone here can help you if it's something else.

I don't see an AM-900 on the Sharp page at openprinting.org ([http://www.openprinting.org/printers/manufacturer/Sharp]("http://www.openprinting.org/printers/manufacturer/Sharp")).  I also don't find it on Sharp printers support page ([http://www.sharpusa.com/CustomerSupport/ProductDownloads.aspx?downloadtype=drivers](http://www.sharpusa.com/CustomerSupport/ProductDownloads.aspx?downloadtype=drivers)).  Is the AM-900 a very old model?  I know it exists, and even found a few places to buy one.  Perhaps it's so old that Sharp no longer supports it.

I did find the Windows drivers for the AM-900 at cnet.com: [http://download.cnet.com/SHARP-AM-900/3000-2116_4-79565.html]("http://download.cnet.com/SHARP-AM-900/3000-2116_4-79565.html").

Maybe you can at least use those to make your AM-900 work on the virtual XP machine.

---

### Post by Quiane on 2010-05-21
yeah, i'm using virtualbox for the xp virtualization.  I did have the am-900 drivers for xp, installed it, but there was no passthrough for the usb (couldn't select it, so xp couldn't "See" it).

The am-900 is new enough to have usb support, but i'm sure it's not a brand new model (i bought it on kijiji)...

Thanks for the reply! :)

Mark

---

### Post by Objekt on 2010-05-21
What version of Virtualbox are you using?  I'd guess you're using the one in the Ubuntu Software Center, which is the "Open Source Edition," or OSE.  Virtualbox OSE does not support USB devices.  You need the Personal Use and Evaluation License (PUEL) version, available here: [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

There used to be a slightly funky procedure required to get USB passthrough working on Virtualbox.  Not sure whether that still applies.  There's tons of threads on this in the Virtualization forum, so you can probably find further help there ([http://ubuntuforums.org/forumdisplay.php?f=308]("http://ubuntuforums.org/forumdisplay.php?f=308")).

---

### Post by Quiane on 2010-05-21
Oh, i have the virtualbox passthrough working, i routinely load my iphone and have even used an epson scanner through usb passthrough on my VB (same machine, same installation).  I'm using the .deb from virtualbox.org, i think my version is 3.1 :)

---

