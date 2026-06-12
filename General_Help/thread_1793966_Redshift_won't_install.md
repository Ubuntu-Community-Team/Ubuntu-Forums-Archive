---
title: "Redshift won't install"
date: 2011-06-30
forum: General Help
---

### Post by aykoola on 2011-06-30
installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 191293 files and directories currently installed.) 
Unpacking gtk-redshift (from .../gtk-redshift_1.2-2_all.deb) ... 
dpkg: error processing /var/cache/apt/archives/gtk-redshift_1.2-2_all.deb (--unpack): 
 trying to overwrite '/usr/bin/gtk-redshift', which is also in package redshift 1.6-0ubuntu1 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 /var/cache/apt/archives/gtk-redshift_1.2-2_all.deb



This is what it says when i try to install it and crash. HELP! :)

---

### Post by November Snow on 2011-09-25
Hi there!
Have you solved your problem?
If not, this is what I've just found on Redshift's main dev blog.

> Make sure you either only install packages from official ubuntu or only from my ppa. They don't mix well.

He suggests removing the Ubuntu packages redshift & gtk-redshift before using his ppa.

Hope this helps.

(For my part, I'm using the 1.6 version I found in the repositories on 11.04, and it works like a charm.)

---

