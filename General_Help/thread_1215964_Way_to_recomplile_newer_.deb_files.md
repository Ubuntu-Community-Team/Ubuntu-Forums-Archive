---
title: "Way to recomplile newer .deb files?"
date: 2009-07-17
forum: General Help
---

### Post by Raskula on 2009-07-17
Is there a way to recompile (or whatever the term is) .deb files? Because I am using Kubuntu 8.04 and I don't want to upgrade, because all my customizations, etc. will be lost. For when nobody makes .debs for 8.04 anymore. Is there a way to recompile the deb file so it works with 8.04?

---

### Post by devosion on 2009-07-17
Instead of making the deb file you are better off compiling from source. Download the package you want to install, unzip the  archive. and review the readme or install file for information on how to compile the package for the distribution.

---

### Post by cariboo on 2009-07-17
You should be good until 2011, before your version is unsupported. For newer versions of some of the packages, make sure you have backports enabled in System-->Administratiom-->Software Sources.

---

### Post by Raskula on 2009-07-17
I'm using Kubuntu so I don't see software sources anywhere.

And I was just wondering like after 2011 or whenever its not supported that there would be a way to recompile a newer .deb just in case.

---

### Post by CatKiller on 2009-07-17
Come 2011 you can upgrade-in-place to the next LTS release, which will keep you going for another three years. You won't lose your customisations since all the configuration files will be the same.

It's not a case of getting .deb files for the packages that you want to install, it's a case of having to track down and install all the dependencies for that package yourself, meaning that you'll have to upgrade a whole bunch of libraries and all sorts. That's what happens during a dist-upgrade, but it happens automatically.

---

### Post by Raskula on 2009-07-17
I don't think Kubuntu has LTS versions, even though its the same thing as ubuntu. I also don't want to lose KDE 3.5.

---

