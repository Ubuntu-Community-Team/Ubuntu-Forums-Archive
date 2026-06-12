---
title: "Graphical Corruption in Fresh Ubuntu dapper install (opengl)"
date: 2006-06-12
forum: General Help
---

### Post by siriusnova on 2006-06-12
Im running a Ubuntu 6.06 Thinkpad T30 with a Radeon 7500 video card using the "radeon" driver.

for some reason i get really bad corruption in any opengl app? What could be the reason a bad CD? Im wondering this because prior to this i was tracking Ubuntu Dapper Flights via apt-get dist-upgrade and everything was fine including the final release. I just did a blank fresh install and now im having corruption in all my opengl apps..

Google Earth app is a very good indicator of this, it was working fine prior to me doing a fresh install

[http://web.umr.edu/~taknnc/Screenshot.png](http://web.umr.edu/~taknnc/Screenshot.png)

Anyone? Should i just do a net install is that option available if the CDs are corrupted?

---

### Post by rcarring on 2006-06-12
Opengl has not been right since before the official release. A good example is the way the progress bar does not appear on the OOo splash, but this seems to be a gnome issue, as under XFCE, the progress bar appears normally.

maybe Opengl is broken under Gnome?

---

### Post by siriusnova on 2006-06-12
I really doubt it..

I tested a theory that maybe accelerated opengl was buggy or something so i disabled opengl and ure enough software opengl worked great.

Maybe the radeon kernel module is corrupted?

it worked in Dapper Beta upgrading all the way to Dapper LTS why wouldnt it work in Dapper LTS after a fresh install?

---

