---
title: "Fixing Package Database"
date: 2011-08-18
forum: General Help
---

### Post by crokett on 2011-08-18
I was having a problem with a fresh 11.04 install and the VPN software I use for work.  I found the fix was to upgrade the software, so I downloaded an RPM, converted it to .deb and installed it via dpkg.  The install worked and the VPN software now works, but Package Manager says I have a broken package and wants to 'upgrade' to the older broken one.  How can I fix this without breaking my VPN SW again?

---

### Post by crokett on 2011-08-18
Fixed.  I did some rummaging and found this:

```

dpkg --purge --force-depends <packagename>

```

This forced removal of the dependencies.

---

