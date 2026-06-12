---
title: "linux-restricted-modules-2.6.28-16-generic package"
date: 2009-12-10
forum: General Help
---

### Post by Akumetsu on 2009-12-10
When ever I start up the Ubuntu Software Center I get the error Package Operation Failed with the details saying E:I wasn't able to locate file for the linux-restricted-modules-2.6.28-16-generic package. This might mean you need to manually fix this package.: I've tried going through the repair but I still can't figure out what's wrong. Thanks

---

### Post by Xbehave on 2009-12-10
I'm not sure but something like
sudo dpkg-reconfigure <package-name> 
may help, otherwise try using aptitude (sudo aptitude) as it will try and solve problems more than apt can.

---

