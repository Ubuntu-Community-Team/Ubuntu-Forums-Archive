---
title: "Intel i810 module not loading on upgrade to 2.6.31-17-generic-pae"
date: 2010-01-31
forum: General Help
---

### Post by randomas on 2010-01-31
I'm running ubuntu 9.10 on an asus ul30vt notebook. 
After my last boot, desktop effects were turned off. After some digging around it turns out the system couldn't load the i810 driver and reverted to vesa. When I tried to load it manually it gave me an unrecognized symbols error. dmesg log also gave allot of errors to i915 and i810.  

For the time being I solved the problem by booting into 2.6.31-16-generic-pae.

Anyone esle have this happen? Know what it's about or how to fix it?

I wanted to report a bug in launchpad, but I don't know which project to file it under xserver, kernel, ubuntu? And which logs to post. 

TIA

---

