---
title: "problem with checkinstall"
date: 2011-11-04
forum: General Help
---

### Post by catarano on 2011-11-04
> **lkraemer said:**
> You can also use checkinstall to build a deb file.

REF:
[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)

```

man checkinstall

```

lk

I tried to do something similar however I see in Oneiric that packages generated this way simply do not install

Does anybody have another view on this?

---

### Post by catarano on 2011-11-04
I compiled some software and tried to make packages using checkinstall on Oneiric

the .deb files get properly generated

however, if I try to install them using

sudo dpkg -i name.deb

the response it that the package is installed, however it does not appear in the list of installed packages from synaptic and the executable does not launch when invoked.

These compiled apps install and work normally if I would use 

sudo make install 

from the source tree.

Interestingly, if I double click on the package from the GUI, gdebi starts, however I do not get a prompt for the password administrator and the package does not install at all.

Am I missing something maybe specific for oneiric?

---

### Post by gsmanners on 2011-11-04
What was the output of checkinstall? Did it complete properly without errors? If you got errors, then try:

```
sudo checkinstall --fstrans=no
```

This issue comes and goes a lot between revisions of Ubuntu, I've noticed.

---

### Post by oldos2er on 2011-11-04
Posts merged. Please keep all posts on your issue in one thread; thanks.

---

### Post by catarano on 2011-11-04
> **gsmanners said:**
> What was the output of checkinstall? Did it complete properly without errors? If you got errors, then try:

```
sudo checkinstall --fstrans=no
```

This issue comes and goes a lot between revisions of Ubuntu, I've noticed.

after compiling I switched to su and installed
now it works and the package appears as installed in synaptic

thanks for your help anyway

---

