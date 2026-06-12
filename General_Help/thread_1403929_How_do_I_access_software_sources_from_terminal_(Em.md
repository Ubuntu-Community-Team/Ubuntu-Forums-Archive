---
title: "How do I access software sources from terminal? (Emergency)"
date: 2010-02-10
forum: General Help
---

### Post by MasterNetra on 2010-02-10
I just attempted to upgraded to KDE 4.4 via backports but it seems a number of updates were blocked and now Plasma workspace crashes upon login. I can only get around via shift+alt+F2. And though I can access KPackageKit via shift+alt+F2 I can't seem to get software sources to load up from KPackage. I want to try enabling the pre-proposed and untested or whatever the other option was in software sources... Unless someone has a better idea? (other then re-installing Kubuntu, or replacing it...)

---

### Post by louieb on 2010-02-10
Repositories are defined in  file /etc/apt/sources.list

---

### Post by MasterNetra on 2010-02-10
Crap even with some addtional stuff enabled the following is still blocked:  ```
 akregator gwenview kaddressbook kdebase-workspace-bin kdebase-workspace-data
  kdebase-workspace-kgreet-plugins kdegraphics-strigi-plugins kdepim-groupware
  kdepim-kresources kdepim-runtime kdepim-runtime-data kdepim-runtime-libs4
  kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdm
  kipi-plugins kmail knotes kontact kopete korganizer ktimetracker
  kubuntu-desktop libkabcommon4 libkdepim4 libkleo4 libkontactinterfaces4
  libkopete4 libkorundum4-ruby1.8 libkpgp4 libksieve4 libmimelib4
  libsmokekde4-2 plasma-dataengines-workspace plasma-widgets-workspace
  python-kde4 
```

---

### Post by MasterNetra on 2010-02-10
Nvm didn't realize i was suppose to do a Distro Upgrade to get everything x.x

---

