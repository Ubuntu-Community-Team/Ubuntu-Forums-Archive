---
title: "HP laserjet 1100"
date: 2010-08-11
forum: General Help
---

### Post by backflip on 2010-08-11
Ubuntu 10.04.
My printer used to be automatically recognised but since installing 10.04 it isn't seen. I've tried ctrl + n in admin/printing but nothing happens.
Any ideas ?
Thanks.

---

### Post by TNT1 on 2010-08-11
hplip?

---

### Post by backflip on 2010-08-11
I've tried that, I removed hplip via synaptics and installed the latest version 3.10.6 but the printer is still not seen.

---

### Post by TNT1 on 2010-08-11
I had this recently on a deskjet all in one... turned out the usb printer cable was faulty... This after I re-installed hplip and cups...

---

### Post by backflip on 2010-08-11
Cable is OK, not a problem with Windows. Also 10.04 won't see my 2nd printer Epson stylus 830U. Both were instantly recognised in Ubuntu before I installed 10.04 :(

---

### Post by fragos on 2010-08-11
Just to be sure unplug and replug your USB cables. When I installed 10.04 my PSC 1410 there was no longer a PPD file for it the PPD for the 1100 is also missing. I located the PPD for my 1410 and placed it in /etc/cups/ppd. the file name was PSC-1400-series.ppd. The PPD you need is I believe is "HP-LaserJet_1100-hpijs.ppd".

---

### Post by darolu on 2010-08-11
I have the same printer and works just fine; unless you have a special model, I think all HP1100 use your parallel-port instead USB; which in my case, was the only problem I had, Ubuntu (linux kernel) wasn't configuring my parallel port card hence my printer being unable to operate. Maybe you are having a similar problem, to make sure your parallel port is configured run these commands:
```
lspci | grep Parallel
```
If it prints nothing run lspci without piping to grep and look for something that says parallel manually.

If you did find it, then run:
```
sudo grep parport /proc/ioports
```
Something like "cf00-cf01 : partport0" should be printed, if it prints nothing it means your parallel port modules ain't being loaded and that you need to configure it manually.

Hopefully is not your case, but I think it wouldn't hurt to check.

---

