---
title: "Scan button on HP psc 1350"
date: 2010-07-01
forum: General Help
---

### Post by jmickela on 2010-07-01
I'm able to scan using both xsane and the HPLIP utility however I can't figure out how to respond to a Scan button press on the device itself. 

In the HP Device Manager there's a section about responding to button presses on the device, but it's disabled and I haven't seen any way to enable it.

I found info about scanbuttond but it looks very out of date and I haven't been able to find anything recent that does the same thing. Is this just something that isn't supported?

---

### Post by Leppie on 2010-07-01
a lot of functions aren't available in linux.

---

### Post by jmickela on 2010-07-01
Yes, but it wouldn't be all that hard to kick off a scan command when the scan button press event comes on the usb connection. It seems like someone must have gotten this working.

---

### Post by Leppie on 2010-07-02
i actually use my scanners over the network with xsane, which gives me a scan preview as well :)
if you're on lucid and want to share your scanner over the network, follow this guide: [http://ubuntuforums.org/showthread.php?t=1519201&highlight=howto+scanner+network](http://ubuntuforums.org/showthread.php?t=1519201&highlight=howto+scanner+network)

but yes, it shouldn't be too hard to implement this. another function they left out is joining wifi printers to the network, but this isn't much of a problem since most wifi routers are now equipped with wps.

---

### Post by jmickela on 2010-07-02
Thanks, this is basically 90% of what I need. Not quite as simple as just having a network share that the image is written to when Scan is pressed, but it will still let users use the scanner without having to mess with the server it's connected to.

---

### Post by fuzzyworbles on 2010-11-11
if anybody out there has any suggestions on getting a scanner not listed in the supported list of scanbuttond to work, please comment. the documentation suggests adding scanimage -n or sane-find-scanner to the initscanner.sh script, but this doesn't seem to have any effect (in my case), other than causing the scanner to turn on.

---

