---
title: "Broken Package - Cannot Install Other Packages!"
date: 2011-01-14
forum: General Help
---

### Post by DaftPyramid on 2011-01-14
A recent update resulted in this error message:

```
E: /var/cache/apt/archives/pidgin-data_1%3a2.7.9-1ubuntu0+pidgin1.10.04_all.deb: trying to overwrite '/usr/share/pixmaps/pidgin/protocols/48/facebook.png', which is also in package pidgin-facebookchat 0
```

Snyaptic tells me that the libc6-i686 and pidgin-data packages are broken. When I attempt to "fix" them, I just get that message again. Every time I try to install a package, I get that message, and the package does not install.

Any help would be greatly appreciated, thanks in advance.

---

### Post by ridetheteapot on 2011-01-14
sudo dpkg -i --force-overwrite /var/cache/apt/archives/pidgin-data_1%3a2.7.9-1ubuntu0+pidgin1.10.04_all.deb
?

---

### Post by DaftPyramid on 2011-01-14
Wow, that worked. Thank you so much.

---

