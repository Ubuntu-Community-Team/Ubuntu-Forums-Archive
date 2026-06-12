---
title: "Any Gnome GUI's for vpnc?"
date: 2006-03-16
forum: General Help
---

### Post by nuzzy on 2006-03-16
Are there any Gnome graphical front end apps for vpnc?  I know KDE has kvpnc...

---

### Post by aysiu on 2006-03-16
You can use kvpnc... even in Gnome.

---

### Post by DukeTech on 2007-03-24
I had Kvpnc 8.7 working in Dapper/Gnome. It worked great except it timed out every 60 seconds on my setup for Cisco.

They said they fixed the Cisco timeout problem with 8.7 so I installed it. Now it does not work at all. I now get the following error:

error: The required helper program (pkcs11-tool) isn't available, connect will be disabled.

Too bad, they were so close.

---

### Post by balique on 2007-04-01
The pkcs11-tool is in the "opensc" package.

---

### Post by EdLesMann on 2007-09-12
Thanks Balique!
I was getting the same error, but only it would let me connect so I never bothered fixing it. Then I did an update and it stopped letting me connect. I found your post and installed opensc and now it works with my cisco vpn!

Thanks again!

---

