---
title: "Need help with analog web stats"
date: 2010-11-04
forum: General Help
---

### Post by acidblue on 2010-11-04
These are the directions for applying the images for analog on a debian system:

Analog reports link to some images that are distributed as part of analog.
These images are made available by creating the symbolic link
/path/to/webserver/root/analog, (Usually /var/www/analog) pointing to
/usr/share/analog/images/, and analog defaults to linking to /analog/ for
the images. This will also not work if you have generated a report and are
viewing it directly, not via the web. In this case you should set IMAGEDIR
to point to /usr/share/analog/images/.

Ive set IMAGES to just what it says to: /usr/share/analog/images/ but I still not getting the images to load.

Also I keep getting the error: analog: Warning F: Failed to open logfile /var/log/apache/logfile.log:
Even though I've set it to /var/log/apache2/access.log

---

