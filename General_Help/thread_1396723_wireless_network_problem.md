---
title: "wireless network problem"
date: 2010-02-02
forum: General Help
---

### Post by amite on 2010-02-02
hi,
 
i hv a problem with my wireless network ,it work fine with windows7 (my 2nd os).
but in ubuntu wireless network are not shown,even in network manager.
help me, i m new user
thanks!

---

### Post by darshana on 2010-02-02
What is the wireless network card you have?

---

### Post by amite on 2010-02-03
dell wireless 1397 WLAN mini card

---

### Post by hawaiian1der on 2010-02-03
Grab a LiveCD if you font already have one: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Pop it in the CD drive.

Go to the Synaptic Package Manager: System > Administration > Synaptic Package Manager.

Click Settings > Repositories > Check the Installible CD-ROM/DVD and close.

Reload the SPM.

In the quick search box type: bcmwl-kernel-source. It should be the first one.

Click the box next to in and click Mark for installation.

Hit apply at the top and click Yes to everything.

Restart and your good to go :)

Hope this works for you.

---

