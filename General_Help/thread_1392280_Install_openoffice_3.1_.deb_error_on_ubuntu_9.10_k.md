---
title: "Install openoffice 3.1 .deb error on ubuntu 9.10 karmic"
date: 2010-01-27
forum: General Help
---

### Post by banhquy on 2010-01-27
I downloaded OOo_3.1.1_LinuxIntel_install_en-US_deb.tar.gz
extract and install by command
cd ....OOO310_m19_native_packed-1_en-US.9420/DEBS
dpkg -i *.deb
=> it's ok.
- And next step error ::D
error when i install *.deb in OOO310_m19_native_packed-1_en-US.9420/DEBS/desktop-integration
- Error below:
 
dpkg: regarding .../openoffice.org3.1-debian-menus_3.1-9420_all.deb containing openoffice.org-debian-menus:
 openoffice.org-common conflicts with openoffice.org-debian-menus
  openoffice.org-debian-menus (version 3.1-9420) is to be installed.
dpkg: error processing /home/users/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9420_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 /home/users/Desktop/OOO310_m19_native_packed-1_en-US.9420/DEBS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9420_all.deb


Help me

---

### Post by raktarok on 2010-01-28
Hi,

This is not advised normally, but you can try this:

```
sudo dpkg -i --force-conflicts *.deb
```

Proceed only if you are desperate, as this may break the package management system. why are you manually installing open-office though? Its available by default, and in the repositories...

---

### Post by banhquy on 2010-01-28
Hix,the default openoffice version in ubuntu 9.10 or update by ubuntu got problem with .doc file modified by microsoft office.i'll get a pic of that error.;)

---

### Post by Hagar Delest on 2010-01-30
See: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

