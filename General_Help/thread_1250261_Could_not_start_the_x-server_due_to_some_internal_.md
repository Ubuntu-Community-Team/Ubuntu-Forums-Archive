---
title: "Could not start the x-server due to some internal error"
date: 2009-08-26
forum: General Help
---

### Post by Capt2836 on 2009-08-26
Have a problem with Easy Peasy 1.1 that has just occured - suspect problem is a generic Ubuntu one, rather than EP specific.

Have been running off a SDHC card for 6 months as an alternative to the Xandros Linux on my Asus EeePC 1000 SSD 40 gb.

A few days ago (have been away onboard ship for 4 months), whilst using the EeePC away from the mains, I closed the lid – on reopening, instead of being greated by the usual « user password login » request, was black screen, white text – no flashing cursor – all locked up.

After forced shutdown, on reboot:

Get to Ubuntu splash, progress bar does its back and forth wiggle, then fully progresses from left to right.

Then get a (plain) blue screenwith the text:

Could not start the x-server due to some internal error........

Bottom of screen – command line:

Ubuntu 8.10 Ueee tty1
Ueee login:

Hangs there.


After pressing power off button to force close -get the usual Easy Peasy 1.1 shutdown splash screen – progress bar progresses left to right happily and netbook shuts down.

On trying to boot in recovery mode:

Get to recovery option screen:

Try fsck – get message « could not open /etc/fstab – Stale NFS handle »

Try xfix – get message « user/sbin/dpkg-reconfigure xserver-xorg is not installed »


One assumes xserver/graphics is the problem - but not the foggiest what to do next.

Any help much appreciated.

Cheers
Kim

---

### Post by winotree on 2009-08-28
Certainly not my area of expertise but I did come across this [http://www.sls.psi.ch/controls/help/howto/nfs_howto.html](http://www.sls.psi.ch/controls/help/howto/nfs_howto.html) during my afternoon's reading -- might it help??  ;)

---

### Post by Capt2836 on 2009-09-07
> **winotree said:**
> Certainly not my area of expertise but I did come across this [http://www.sls.psi.ch/controls/help/howto/nfs_howto.html](http://www.sls.psi.ch/controls/help/howto/nfs_howto.html) during my afternoon's reading -- might it help??  ;)

Sorry for the late reply - have been away from internet connections.  Will have a kook at the link - many thanks for your suggestion.

Kim

---

### Post by Capt2836 on 2009-09-07
> **winotree said:**
> Certainly not my area of expertise but I did come across this [http://www.sls.psi.ch/controls/help/howto/nfs_howto.html](http://www.sls.psi.ch/controls/help/howto/nfs_howto.html) during my afternoon's reading -- might it help??  ;)

Further to my previous post - 1) yes, this may well allow me to run the recovery programs and 2) it's just a shame i have just realised that the SD card with EP on it is in the Uk - and I am in France for the next month. Will try upon my return.  Many thanks again.

Kim

---

