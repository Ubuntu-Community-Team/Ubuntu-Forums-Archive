---
title: "ROOT Repository"
date: 2010-07-21
forum: General Help
---

### Post by Klaw117 on 2010-07-21
I just installed ROOT from the Ubuntu Software Center for my nuclear chemistry research, but the version it installed is 5.18 while the newest version is 5.27. Does anyone know the repository to update ROOT?

---

### Post by bumanie on 2010-07-21
There is a .deb [here]("http://sourceforge.net/projects/cernrootdebs/") - at least I think it's the thing you are looking for.

---

### Post by Klaw117 on 2010-07-22
Thanks, but that didn't really work. The version number for ROOT still says 5.18/00b. According to the ROOT website ([http://root.cern.ch/drupal/]("http://root.cern.ch/drupal/")), the most recent version is 5.27/04, but it looks like it's only for Scientific Linux. I'm trying to either find a repository so that the Update Manager will update ROOT or find a way to just install the binaries from the website.

---

### Post by dvd_it on 2010-08-30
It works, since I built it :)
simply read the instructions!
it's installed in /opt to preserve ubuntu root version...
you can launch it from
/opt/root/bin/root

(or make a link in /usr/bin if you prefere, e.g.
sudo ln -s /opt/root/bin/root /usr/bin/root-latest
and then simply launch root-latest)
ciao
d

---

