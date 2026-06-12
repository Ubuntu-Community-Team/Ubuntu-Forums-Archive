---
title: "hp deskjet 2050 xsane support?"
date: 2011-03-20
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-03-20
anyone know if the scanner is supported
lucid 10.04.2
it is downloading updates now
hp-setup does not work on it
Bus 003 Device 004: ID 03f0:8711 Hewlett-Packard 
scanimage -L did not find it

---

### Post by pqwoerituytrueiwoq on 2011-03-23
looks like it needs hplip 3.10.6 ([http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_2050_j510_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_2050_j510_series.html))
[https://launchpad.net/ubuntu/+source/hplip/](https://launchpad.net/ubuntu/+source/hplip/)
how do i add it as a source?
is there a deb package?
edit i think i found them
[https://launchpad.net/~ubuntu-security/+archive/ppa/+buildjob/2192428]("https://launchpad.net/%7Eubuntu-security/+archive/ppa/+buildjob/2192428")

EDIT:
This worked for me
[http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)
Edit:
even better 
[https://launchpad.net/~hplip-isv/+archive/ppa](https://launchpad.net/~hplip-isv/+archive/ppa)

---

