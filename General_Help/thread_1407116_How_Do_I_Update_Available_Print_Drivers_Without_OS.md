---
title: "How Do I Update Available Print Drivers Without OS Upgrade?"
date: 2010-02-14
forum: General Help
---

### Post by lightnb on 2010-02-14
Ubuntu 9.04 includes the print driver I need (HP Color LaserJet CP2025dn). I have a production server running 8.04, which does not have this driver available in it's list.

How can I update my server to the latest printer driver list, without doing a dist-upgrade?

---

### Post by sandyd on 2010-02-14
Download HPLIP from : [http://hplipopensource.com](http://hplipopensource.com)

---

### Post by Julita on 2010-02-14
Or you can just add to your /etc/apt/sources.list the jaunty repository that contains the driver.

---

### Post by lightnb on 2010-02-15
Thanks guys!

---

