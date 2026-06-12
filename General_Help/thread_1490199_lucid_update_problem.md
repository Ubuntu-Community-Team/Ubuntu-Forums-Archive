---
title: "lucid update problem"
date: 2010-05-22
forum: General Help
---

### Post by Midnytpudding on 2010-05-22
successfully installed ubuntu but i cant install its updates, heres the prob:

  dpkg: parse error, in file '/var/lib/dpkg/available' near line 19410 package 'initscripts':
 missing version


thanks.

---

### Post by Midnytpudding on 2010-05-22
pls. any help?

---

### Post by James78 on 2010-05-22
Try this and see if it helps.```
sudo dpkg --clear-avail
```If that fails, then see if this helps you out...
[http://ubuntuforums.org/showpost.php?p=297868&postcount=2](http://ubuntuforums.org/showpost.php?p=297868&postcount=2)

---

