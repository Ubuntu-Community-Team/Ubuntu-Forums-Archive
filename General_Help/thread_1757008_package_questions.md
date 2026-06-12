---
title: "package questions"
date: 2011-05-12
forum: General Help
---

### Post by mr.farenheit on 2011-05-12
i just finished an install of xubuntu to my netbook. i went into the software center to remove some programs that i felt i didn't need. while doing this i saw many applications installed for gnome and kde packages. i figured with runnning xfce i wouldn't need them but am curious if i actually do. are any of the gnome and kde packages needed or can i uninstall them?

---

### Post by jerrrys on 2011-05-13
what packages ?  just took a look for kde packages and cant find any

---

### Post by mr.farenheit on 2011-05-13
one is gdebi installer for kde. another is kpackagekit. there is also one for software sources. i found these in the ubuntu software center. i also when running a distro try to avoid installing any apps from another desktop enviro, and to my knowledge i haven't installed any so far.

---

### Post by snowpine on 2011-05-13
Most packages "depend" on other packages. These are called "dependencies." You should always read this list carefully before installing.

For example kpackagekit has the following dependencies: [http://packages.ubuntu.com/natty/kpackagekit](http://packages.ubuntu.com/natty/kpackagekit)

There is nothing "wrong" with installing KDE applications in Xubuntu. The only downside is using a little bit more hard drive space compared with a similar application that does not have KDE dependencies.

---

### Post by mr.farenheit on 2011-05-13
gotcha. well i'm not too hard up for hdd space so i guess i can leave them be. thanks for the info.

---

### Post by jerrrys on 2011-05-13
> **mr.farenheit said:**
> one is gdebi installer for kde. another is kpackagekit. there is also one for software sources. i found these in the ubuntu software center. i also when running a distro try to avoid installing any apps from another desktop enviro, and to my knowledge i haven't installed any so far.

these two are not part of the xubuntu standard install.  so like snowpine said your dealing with dependencies from something else installed.  take a look in synaptic>status>not installed residual.  also you can load deborphan to see whats going on, but use care with that package.

---

