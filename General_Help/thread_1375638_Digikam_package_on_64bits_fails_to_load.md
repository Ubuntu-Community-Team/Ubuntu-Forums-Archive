---
title: "Digikam package on 64bits fails to load"
date: 2010-01-08
forum: General Help
---

### Post by syncmasterpt on 2010-01-08
Hi!

I have two computers running Kubuntu 9.10 (using the upgrade paths from 8.04 and so on) one running 32bit and the other running 64 bit and I have the following problem:

On the 32bit version installing the repository package for Digikam, everything works just fine.

On the 64bit version I have two problems:

First digikam won't start due to the following error:

digikam: symbol lookup error: /usr/lib/kde4/digikamimageplugin_freerotation.so:
undefined symbol: _ZN7Digikam11ImagePlugin17setActionCategoryERK7QString

I'll have to delete all digikamplugin files from /usr/lib/kde4 and then it works from the command line. It appears that everything is working as it should.

Second, starting digikam from Lancelot does nothing....

Any ideas?

---

### Post by syncmasterpt on 2010-01-08
Found the issue.

Had an old compiled version in usr/local bin and lib...

Deleted everything, re-installed and it works now.

---

