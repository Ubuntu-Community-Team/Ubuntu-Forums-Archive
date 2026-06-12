---
title: "Apache/2.2.11 core cfg files missing"
date: 2009-10-11
forum: General Help
---

### Post by mtsgeo on 2009-10-11
hi,
      any files that would normally reside in /etc/apache2/ are now all gone, excluding subdirectories  (yup, ran rm * on accident).   my question is about the files that were here.  this is a pretty standard installation, but all I can remember was an envvar, httpd.conf, and apache2.conf.  was that it by default?
    - and would i be able to find the default version of these 3 files somewhere without reinstalling the apache2 server?  (i'm afraid if i reinstall, a lot more configuration will be lost)

Ubuntu 9.04
Linux box 2.6.28-15-generic

cheers,
mts


Update~  so a bit more searching revealed the default files are available by downloading the apache2.2-common.deb file from the repo, opening it up in an archive manager, and extracting the config files.

---

