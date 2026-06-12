---
title: "LTSP Kernel Panic problem"
date: 2010-07-18
forum: General Help
---

### Post by dmoore2607 on 2010-07-18
Complete noob so apologies if posting in wrong section
 
I've installed LTSP on 10.04. I can get a couple of (fairly new) laptops to boot from this so all appears to be fine. But my key goal is to get ASUS K8S-MX motherboard with sis 190 lan to boot so that I can set up a computer lab.
 
All seems to go well on boot but
 
When loading essential drivers, nothing seems to load and I get a done.
Then running /scripts/init-premount I get no interfaces found 
 
Then mounting root file system It starts Running /scripts/nfs-top
 
and drops into kernel panic
 
 
I've searched and searched on google and come up with nothing.
 
Any ideas

---

### Post by alexlittle on 2010-09-11
Hi,

I had the same problem trying to use my Asus eeepc 1008ha as a thin client. I followed the instructions here: [http://www.nubae.com/making-asus-eeepc-work-for-ubuntu-ltsp]("http://www.nubae.com/making-asus-eeepc-work-for-ubuntu-ltsp") with a couple of minor amendments and then it started working.

The changes I made were to use atl1c as the module name (not atl2) and then instead of:
cp /opt/ltsp/i386/boot/<kernel-version-number> /var/lib/tftpboot/ltsp/i386/

I used:
cp /opt/ltsp/i386/boot/initrd.img-<kernel-version-number> /var/lib/tftpboot/ltsp/i386/

Hope that's useful.
Alex

---

### Post by RicardoCapurro on 2011-01-16
Hi, I had the same problem and in my case worked using modules atl1c, atl2 and sis190

Thanks for the info

---

