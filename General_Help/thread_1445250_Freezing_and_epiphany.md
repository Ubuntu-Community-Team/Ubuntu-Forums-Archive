---
title: "Freezing and epiphany"
date: 2010-04-02
forum: General Help
---

### Post by dianemeeks on 2010-04-02
9.10 has been freezing.  The caps lock light flashes and the only thing that works is to reboot.  I believe this has something to do with an installation of epiphany that didn't quite work.  When I attempt to uninstall, here's what the terminal gives me.

sudo  dpkg -P epiphany-browser-data
(Reading database ... 324498 files and directories currently installed.)
Removing epiphany-browser-data ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing epiphany-browser-data (--purge):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 epiphany-browser-data

Synaptic gives me a shorter version of the same thing.  I need help....bad.

---

