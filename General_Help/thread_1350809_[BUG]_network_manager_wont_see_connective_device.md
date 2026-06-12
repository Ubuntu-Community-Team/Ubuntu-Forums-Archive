---
title: "[BUG] network manager wont see connective device"
date: 2009-12-09
forum: General Help
---

### Post by rvndrk3233 on 2009-12-09
ok, I've found that with 9.10 anyway, DUN and WWAN connections are not listed in the drop down menu.

LAN connections are the only thing shown and the configure script doesn't have common carriers setup.

I cant even configure the pantech verizon card without manually using wvdial and scripts(which I had to piece together to get a decent disconnect ability.....) The nTelos aircard is found ok, but never dials out.

The hardware is always busy.

anyone having WWAN issues should be aware of this.

you need the wvdial scripts to dial out/PRL update(yes, you can do it on linux....)

I have scripts if anyone wants them, but you might need a different AT&F init string for your USB WWAN card[modem].

---

