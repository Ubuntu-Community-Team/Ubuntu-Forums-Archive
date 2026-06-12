---
title: "Unable to install Miro"
date: 2009-06-28
forum: General Help
---

### Post by sefs on 2009-06-28
Hi all I am unable to install miro.

I get this error:
```
Depends: libtorrent-rasterbar2 but it is not going to be installed
```

---

### Post by oldos2er on 2009-06-28
Which version of Ubuntu are you running? Do you have all repositories enabled?

---

### Post by lovinglinux on 2009-06-28
If you have the PPA repository for Deluge enabled, then it probably replaced *libtorrent-rasterbar2* with *libtorrent-rasterbar4*. If this is the case, then you might want to downgrade Deluge to install Miro.

---

### Post by sefs on 2009-07-09
I removed the deluge from the ppa installed the latest version from getdeb.net which still uses raster2 and then installed the latest version of miro from their ppa.

That seemed to have worked.

---

