---
title: "Virtual Box install"
date: 2010-03-16
forum: General Help
---

### Post by frankiethepill on 2010-03-16
Recently installed Ubuntu on a netbook- no DVD rom so installed from a pendrive. Then tried to install VirtualBox - half way through the install process it asks for the Ubuntu install disk in CDROM - problem as there isn't one. Tried the install pendrive- no joy. Tried adding a USB DVD rom drive with a Ubuntu install CD, the drive is recognised by the system but the install process doesn't see it, so stops. 
Any way around this?

---

### Post by dudumomo on 2010-03-16
Hi,
With VirtualBox, on the setting of yout Virtual Machine, you can add an iso as a CDROM. Then you will be able to boot on this.

---

### Post by frankiethepill on 2010-03-16
> **dudumomo said:**
> Hi,
With VirtualBox, on the setting of yout Virtual Machine, you can add an iso as a CDROM. Then you will be able to boot on this.

I'm not that far ahead- I'm still trying to get Virtual Box installed on the machine- during the install process it seems to want some files from the Ubuntu install disk. Why it couldn't put them in on Ubuntu installation I don't know.

---

### Post by El Zoido on 2010-03-16
Strange, I've never been asked for the install cd by virtual box.
Try this:
Go to System -> Administration -> Software Sources

and there, check if the Ubuntu-cd is enabled at the bottom. If it is, try disabling it and see if Ubuntu will now try to download whatever it is missing from the net.

Alternatively, if you have not done so, you could try adding the official Virtualbox repository from [www.virtualbox.org]("http://www.virtualbox.org") and try installing from there. 
This will also give you the most recent non-ose version.

---

### Post by frankiethepill on 2010-03-16
> **El Zoido said:**
> Strange, I've never been asked for the install cd by virtual box.
Try this:
Go to System -> Administration -> Software Sources

and there, check if the Ubuntu-cd is enabled at the bottom. If it is, try disabling it and see if Ubuntu will now try to download whatever it is missing from the net.

Alternatively, if you have not done so, you could try adding the official Virtualbox repository from [www.virtualbox.org]("http://www.virtualbox.org") and try installing from there. 
This will also give you the most recent non-ose version.

Perfect. Works like a charm. I did try VMWare once before, and this is so much easier to install! VMWare was a bit convoluted!
Linux seems to be getting its act together- I have tried older versions before and little things like program installations drove me to drink, but it all seems to be so much better in this generation. Annoyingly I only want Windows access for one program I use for my accounts. Otherwise I can nearly totally go for Linux for all my computer uses. We're getting there!

---

### Post by Jeff Anthony on 2010-03-16
I had absolutely no problems running VirtualBox, installed just as easily as anything ever was. Sounds more like you had a problem with the Ubuntu install where it came from the USB or something. Don't blame VirtualBox!

---

