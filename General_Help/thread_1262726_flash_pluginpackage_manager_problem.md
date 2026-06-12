---
title: "flash plugin/package manager problem"
date: 2009-09-10
forum: General Help
---

### Post by usien on 2009-09-10
i installed flash plugin from adobe website using the .deb, it worked fine initially but somehow it got messed up.now no package manager works on my system.i cant remove it using apt-get or dpkg. the message i get when i run synaptic is: 

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by chriskin on 2009-09-10
isn't is asking you to reinstall it using the deb again?
it can't find the package because it was a package you get to it,not one of the repositories

---

### Post by chriskin on 2009-09-10
i would prefer to uninstall the .deb through computer janitor and install the adobe flash plugin through synaptic, by the way

---

### Post by usien on 2009-09-10
when i run the deb it says the deb is corrupted or you dont have permissions, i tried downloading it again but still the same.

janitor doesnt work either.

---

### Post by stumbleUpon on 2009-09-10
first remove the package 

```
sudo aptitude remove adobe-flashplugin
```

and then install through the repos as suggested earlier

---

### Post by usien on 2009-09-10
that doesnt work either

---

