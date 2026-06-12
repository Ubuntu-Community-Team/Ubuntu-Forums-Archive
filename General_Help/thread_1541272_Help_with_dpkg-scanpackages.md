---
title: "Help with dpkg-scanpackages"
date: 2010-07-28
forum: General Help
---

### Post by carrlos on 2010-07-28
When building a Packages archive, previously I was running this script:
```
dpkg-scanpackages -m . /dev/null >Packages
```
Then I would right click the Packages file and choose compress and choose .gz, but someone told me I could run this script which then worked fine:
 
```
dpkg-scanpackages -m . /dev/null | gzip -9c >Packages.gz
```
 
But now I need a .bz2 archive instead. What would be the new script? Any help would be appreciated.

---

