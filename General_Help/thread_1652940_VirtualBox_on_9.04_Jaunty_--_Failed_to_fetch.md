---
title: "VirtualBox on 9.04 Jaunty -- Failed to fetch"
date: 2010-12-25
forum: General Help
---

### Post by fermulator on 2010-12-25
Has anyone tried to install virtualbox on 9.04 Jaunty recently?

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

The links for vbox Jaunty are dead, and the apt-sources entry is apparently malformed...

> $ cat virtualbox.list 
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty contrib

During an "apt-get update":
> Hit [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release.gpg
Ign [http://download.virtualbox.org](http://download.virtualbox.org) jaunty/contrib Translation-en_CA
Hit [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release
W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/jaunty/Release](http://download.virtualbox.org/virtualbox/debian/dists/jaunty/Release)  Unable to find expected entry  contrib/binary-i386/Packages in Meta-index file (malformed Release file?)

---

### Post by dcstar on 2010-12-27
> **fermulator said:**
> Has anyone tried to install virtualbox on 9.04 Jaunty recently?

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

The links for vbox Jaunty are dead, and the apt-sources entry is apparently malformed...


Have **you** contacted that website and told them?

---

