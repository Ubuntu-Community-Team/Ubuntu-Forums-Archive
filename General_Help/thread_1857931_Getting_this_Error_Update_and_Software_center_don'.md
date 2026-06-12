---
title: "Getting this Error Update and Software center don't work"
date: 2011-10-11
forum: General Help
---

### Post by thedoorwayto on 2011-10-11
I'm Using Ubuntu 11.04  and tired to update Libre office to 3.4 I removed libre office as was getting errors with that but still getting this please help..

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:


W:Ignoring file 'mitya57-ppa-natty.list.save.2' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension, W:Ignoring file 'mitya57-ppa-natty.list.save.1' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension, E:Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/libreoffice-ppa-natty.list'

---

### Post by oldos2er on 2011-10-11
Remove the files with bad extensions ```
sudo rm /etc/apt/sources.list.d/mitya57-ppa-natty.list.save.2 && sudo rm /etc/apt/sources.list.d/mitya57-ppa-natty.list.save.1
```

Edit /etc/apt/sources.list.d/libreoffice-ppa-natty.list to fix typos, ```
gksu gedit /etc/apt/sources.list.d/libreoffice-ppa-natty.list
```

deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) natty main 
deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) natty main

Save and exit, run ```
sudo apt-get update
```

---

### Post by thedoorwayto on 2011-10-11
Thank you so much . I'm back up and running ...

---

### Post by oldos2er on 2011-10-12
You're welcome.

Could you please mark the thread as solved under Thread Tools?

---

