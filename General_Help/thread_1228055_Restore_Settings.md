---
title: "Restore Settings?"
date: 2009-07-31
forum: General Help
---

### Post by shadow9821 on 2009-07-31
I've messed up my network settings, and now the manager only detects wired connections. I was following a tutorial on making a TP Link wireless adapter work, but i gave up halfway and bought a lynksis. It was working fine, but now it doesnt connect. Is there a way to restore the software without losing any files? Or, if that is not possible, how do i un-blacklist the drivers for the adapters?

---

### Post by gettinoriginal on 2009-07-31
Attribute this solution to epihonygirl:
open up terminal and type in
```
sudo gedit /etc/modprobe.d/blacklist
```
This should open a window with a list of drivers that are blacklisted, now all that you need to do is look for the driver that you blacklisted and delete the entry for it.

i.e.
if it is listed as
"blacklist ath_pci"
then just delete it so that it is no longer there then save the file and restart.

---

