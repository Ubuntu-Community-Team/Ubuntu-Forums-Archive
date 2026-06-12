---
title: "dpkg hangs when setting locale.."
date: 2009-10-11
forum: General Help
---

### Post by wparsons on 2009-10-11
I've got something causing an error, not sure which package it is though.  It might be locales, but maybe not?

Anytime I try to run apt-get, it tells me that dpkg was interrupted, and to run dpkg --configure -a.  When I do that, it hangs on Setting up locales(2.7.9-4), specifically on the line with 'en_US.UTF-8', which comes right after 'Generating locales'.

If I try to run dpkg-reconfigure locales, it tells me the package is broken or not fully installed.

Anyone have suggestions on how to fix that?  Normally if a package isn't fully installed, I'd reinstall through apt-get, so I'm stuck in a bit of an infinite loop here.

I'm running ubuntu server, I think its 8.04 but I'm not positive.

---

### Post by wparsons on 2009-10-12
I'm thinking I might have to do a re-install, or atleast see if I can repair it booting with the live CD.  Good excuse to move it over to newer hardware anyway(its just a dev server, currently its a PIII 500, moving to a celeron 2ghz).

---

