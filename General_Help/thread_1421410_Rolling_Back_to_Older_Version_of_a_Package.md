---
title: "Rolling Back to Older Version of a Package"
date: 2010-03-04
forum: General Help
---

### Post by lazerradial2003 on 2010-03-04
My most recent update in Jaunty led to a crashing problem I'd had before, I've tried booting with different Kernel versions from GRUB but same problems with all so doesn't seem to be that. 

I've got a list of packages which were installed in the update (below). 

Is there a simply way of going through them one by one to reinstall the old version to try and work out which package is causing the problem? 

Update Summary: 
bind9-host (1:9.5.1.dfsg.P2-1ubuntu0.3) to 1:9.5.1.dfsg.P2-1ubuntu0.4
dhcp3-client (3.1.1-5ubuntu8.1) to 3.1.1-5ubuntu8.2
dhcp3-common (3.1.1-5ubuntu8.1) to 3.1.1-5ubuntu8.2
dnsutils (1:9.5.1.dfsg.P2-1ubuntu0.3) to 1:9.5.1.dfsg.P2-1ubuntu0.4
firefox (3.0.15+nobinonly-0ubuntu0.9.04.1) to 3.0.17+nobinonly-0ubuntu0.9.04.1
firefox-3.0 (3.0.15+nobinonly-0ubuntu0.9.04.1) to 3.0.17+nobinonly-0ubuntu0.9.04.1
firefox-3.0-branding (3.0.15+nobinonly-0ubuntu0.9.04.1) to 3.0.17+nobinonly-0ubuntu0.9.04.1
firefox-3.0-gnome-support (3.0.15+nobinonly-0ubuntu0.9.04.1) to 3.0.17+nobinonly-0ubuntu0.9.04.1
firefox-3.5 (3.5.5+nobinonly-0ubuntu0.9.04.1) to 3.5.7+nobinonly-0ubuntu0.9.04.1
firefox-3.5-branding (3.5.5+nobinonly-0ubuntu0.9.04.1) to 3.5.7+nobinonly-0ubuntu0.9.04.1
firefox-gnome-support (3.0.15+nobinonly-0ubuntu0.9.04.1) to 3.0.17+nobinonly-0ubuntu0.9.04.1
fuse-utils (2.7.4-1.1ubuntu4) to 2.7.4-1.1ubuntu4.0.9.04.1
gimp (2.6.6-0ubuntu1) to 2.6.6-0ubuntu1.1
gimp-data (2.6.6-0ubuntu1) to 2.6.6-0ubuntu1.1
gzip (1.3.12-6ubuntu2) to 1.3.12-6ubuntu2.9.04.1
libbind9-40 (1:9.5.1.dfsg.P2-1ubuntu0.3) to 1:9.5.1.dfsg.P2-1ubuntu0.4
libdns45 (1:9.5.1.dfsg.P2-1ubuntu0.3) to 1:9.5.1.dfsg.P2-1ubuntu0.4
libdns46 (1:9.5.1.dfsg.P2-1ubuntu0.3) to 1:9.5.1.dfsg.P2-1ubuntu0.4
libexpat1 (2.0.1-4) to 2.0.1-4ubuntu0.9.04.1
libfuse2 (2.7.4-1.1ubuntu4) to 2.7.4-1.1ubuntu4.0.9.04.1
libgimp2.0 (2.6.6-0ubuntu1) to 2.6.6-0ubuntu1.1
libisc45 (1:9.5.1.dfsg.P2-1ubuntu0.3) to 1:9.5.1.dfsg.P2-1ubuntu0.4
libisccc40 (1:9.5.1.dfsg.P2-1ubuntu0.3) to 1:9.5.1.dfsg.P2-1ubuntu0.4
libisccfg40 (1:9.5.1.dfsg.P2-1ubuntu0.3) to 1:9.5.1.dfsg.P2-1ubuntu0.4
libkrb53 (1.6.dfsg.4~beta1-5ubuntu2) to 1.6.dfsg.4~beta1-5ubuntu2.2
liblwres40 (1:9.5.1.dfsg.P2-1ubuntu0.3) to 1:9.5.1.dfsg.P2-1ubuntu0.4
libmysqlclient15off (5.1.30really5.0.75-0ubuntu10.2) to 5.1.30really5.0.75-0ubuntu10.3
libpurple-bin (1:2.5.5-1ubuntu8.4) to 1:2.5.5-1ubuntu8.5
libpurple0 (1:2.5.5-1ubuntu8.4) to 1:2.5.5-1ubuntu8.5
libsmbclient (2:3.3.2-1ubuntu3.2) to 2:3.3.2-1ubuntu3.3
libssl0.9.8 (0.9.8g-15ubuntu3.3) to 0.9.8g-15ubuntu3.4
libthai-data (0.1.9-4) to 0.1.9-4ubuntu0.9.04.2
libthai0 (0.1.9-4) to 0.1.9-4ubuntu0.9.04.2
libwbclient0 (2:3.3.2-1ubuntu3.2) to 2:3.3.2-1ubuntu3.3
libwxbase2.6-0 (2.6.3.2.2-3ubuntu4) to 2.6.3.2.2-3ubuntu4.1
libwxgtk2.6-0 (2.6.3.2.2-3ubuntu4) to 2.6.3.2.2-3ubuntu4.1
linux-generic (2.6.28.17.22) to 2.6.28.18.23
linux-headers-generic (2.6.28.17.22) to 2.6.28.18.23
linux-image-generic (2.6.28.17.22) to 2.6.28.18.23
linux-libc-dev (2.6.28-17.58) to 2.6.28-18.59
linux-restricted-modules-common (2.6.28-17.22) to 2.6.28-18.23
linux-restricted-modules-generic (2.6.28.17.22) to 2.6.28.18.23
mysql-common (5.1.30really5.0.75-0ubuntu10.2) to 5.1.30really5.0.75-0ubuntu10.3
openssl (0.9.8g-15ubuntu3.3) to 0.9.8g-15ubuntu3.4
pidgin (1:2.5.5-1ubuntu8.4) to 1:2.5.5-1ubuntu8.5
pidgin-data (1:2.5.5-1ubuntu8.4) to 1:2.5.5-1ubuntu8.5
python-wxgtk2.6 (2.6.3.2.2-3ubuntu4) to 2.6.3.2.2-3ubuntu4.1
python-wxversion (2.8.9.1-0ubuntu6) to 2.8.10.1-1
samba-common (2:3.3.2-1ubuntu3.2) to 2:3.3.2-1ubuntu3.3
smbclient (2:3.3.2-1ubuntu3.2) to 2:3.3.2-1ubuntu3.3
tor (0.2.1.20-1~jaunty+1) to 0.2.1.22-1~jaunty+1
tor-geoipdb (0.2.1.20-1~jaunty+1) to 0.2.1.22-1~jaunty+1
transmission-common (1.51-0ubuntu3) to 1.51-0ubuntu3.1
transmission-gtk (1.51-0ubuntu3) to 1.51-0ubuntu3.1
tzdata (2009s~repack-0ubuntu9.04) to 2009u~repack-0ubuntu9.04
vidalia (0.1.9-3) to 0.2.7-1~jaunty1
xulrunner-1.9 (1.9.0.15+nobinonly-0ubuntu0.9.04.1) to 1.9.0.17+nobinonly-0ubuntu0.9.04.1
xulrunner-1.9-gnome-support (1.9.0.15+nobinonly-0ubuntu0.9.04.1) to 1.9.0.17+nobinonly-0ubuntu0.9.04.1
xulrunner-1.9.1 (1.9.1.5+nobinonly-0ubuntu0.9.04.1) to 1.9.1.7+nobinonly-0ubuntu0.9.04.1

Installed the following packages:
linux-headers-2.6.28-18 (2.6.28-18.59)
linux-headers-2.6.28-18-generic (2.6.28-18.59)
linux-image-2.6.28-18-generic (2.6.28-18.59)
linux-restricted-modules-2.6.28-18-generic (2.6.28-18.23)
python-wxgtk2.8 (2.8.10.1-1)

---

