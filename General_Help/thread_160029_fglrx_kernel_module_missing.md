---
title: "fglrx kernel module missing?"
date: 2006-04-14
forum: General Help
---

### Post by Grey on 2006-04-14
Okay, I have no idea what's up.  fglrx is working fine on my own computer, but my girlfriend's computer just WILL NOT load the fglrx module.  I've even upgraded to Dapper, and it still just gives me the mesa glx drivers.

When I try to modprobe fglrx, I just get this:

FATAL: Module fglrx not found.

Which I don't think is right, given that it works just fine on my PC, which does have working 3D acceleration.

And for the record, I have xorg-driver-fglrx and restricted modules installed.  It is just unable to find the kernel module.  I have no idea what's up, and any help would be appreciated.  If it helps, the first install on that computer was 5.04, and was dist-upgraded to breezy.

---

### Post by Numeri on 2006-04-14
Some ppl suggested that when installing the fglrx drivers one should shut down gdm:
$ sudo /etc/init.d/gdm stop

and then [reinstall] or [remove + install] the restricted modules and the fglrx driver. 

Maybe that helps. Yours... Numeri

if not, what does your /var/log/Xorg.0.log look like?

---

### Post by Grey on 2006-04-14
Sorry, I resolved this problem, and forgot to post about it...  I SUSPECT that the problem all along was that I didn't actually have the restricted modules installed.  (I swear, I checked for them, but perhaps I was mistaken).

Anyways, what I did was I removed both the restricted modules and the fglrx driver, and then rebooted, with the vesa driver.  Then I reinstalled both of those, and switched to fglrx.  Another reboot fixed everything.

I was also messing with the kernel image though, and reinstalled that a few times.  That might also have had something to do with it.

At any rate, it's working fine right now.  Speedy as hell.

---

