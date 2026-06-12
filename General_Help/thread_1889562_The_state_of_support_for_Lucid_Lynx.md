---
title: "The state of support for Lucid Lynx"
date: 2011-12-01
forum: General Help
---

### Post by Linux_junkie on 2011-12-01
I have Lucid on a laptop and have noticed for sometime now that certain applications have not been updated for sometime, namely OpenOffice.  Now I know development of OpenOffice has stopped but Canonical are still claiming that they are supporting this application until 2013.  With no updates since Oracle abandoned OpenOffice how can Canonical continue to say that its supported until 2013?

Come on Canonical, update your repos and remove applications that are no longer supported.

---

### Post by Penguinnerd on 2011-12-01
The idea of an LTS release is just the opposite of that, though.

Unless there are security issues, everything is supposed to stay the same. If you want a newer version, you can do a few things.


1. Install manually by downloading the new version somewhere. (Libreoffice, I suppose)

2. I've heard you can use backports or somthing to do this, but never tried it. This might be the most practical option for most people who need newer stuff.

3. Use a newer version if you must. LTS is supposed to be old and predictable. I use LTS because I don't want my system to change very frequently. If you are peeved about not having the latest versions, reconsider your decision to use LTS.

However, do note: If there were a major flaw in the version of openoffice present in 10.04 with regard to security or something, I am confident that Canonical would patch/fix it. (Even though the original developer won't anymore)

---

### Post by LowSky on 2011-12-01
All you get are Security Updates. If you want actual new version of the software you will need to grab a PPA, the better option of to grab LibreOffice since it is more widely supported.

For LibreOffice:
```
sudo add-apt-repository ppa:libreoffice/ppa
```

If you still want OO.o
```
sudo add-apt-repository ppa:openoffice-pkgs/ppa
```

---

### Post by philinux on 2011-12-01
> **Linux_junkie said:**
> I have Lucid on a laptop and have noticed for sometime now that certain applications have not been updated for sometime, namely OpenOffice.  Now I know development of OpenOffice has stopped but Canonical are still claiming that they are supporting this application until 2013.  With no updates since Oracle abandoned OpenOffice how can Canonical continue to say that its supported until 2013?

Come on Canonical, update your repos and remove applications that are no longer supported.

Have you enabled backports in software sources.

 [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Moved to general help.

---

