---
title: "No kde -&gt; kdm dependency"
date: 2006-03-13
forum: General Help
---

### Post by Rovenhot on 2006-03-13
I receently switched to KDE (and love it), but while apt-getting it I noticed that the kde does not depend on kdm, as the package description says, and so I had to get that package as well.  Is this lack of dependency intentional?

---

### Post by niviche on 2006-03-13
The proper way to install Kubuntu from the Gnome version of Ubuntu is to install the "kubuntu-desktop" package, not the "kde" one. If you installed KDE but are missing the whole KDM & co stuff, try to apt-get "kubuntu-desktop".

---

### Post by feathers on 2006-03-14
kde is not dependent on kdm. Kdm is only the login manager and you get into kdm via xdm or gdm, it doesn't matter. If you want the whole stuff install kubuntu-desktop which depends on a lot of packages, kdm as well.

---

