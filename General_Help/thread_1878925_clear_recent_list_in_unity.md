---
title: "clear recent list in unity?"
date: 2011-11-10
forum: General Help
---

### Post by soryu on 2011-11-10
how do i clear the recent list in unity11.10?

---

### Post by philinux on 2011-11-10
> **soryu said:**
> how do i clear the recent list in unity11.10?

 [http://www.webupd8.org/2011/05/zeitgeist-activity-log-manager-now.html](http://www.webupd8.org/2011/05/zeitgeist-activity-log-manager-now.html)

I think you might also need the gnome activity journal.

---

### Post by soryu on 2011-11-10
installed zeitgeist actvity manager.
installed gnome activity manager.
now
"The following packages have unmet dependencies:

zeitgeist: Depends: python-zeitgeist but it is not installed"


???

---

### Post by soryu on 2011-11-10
Unpacking python-zeitgeist (from .../python-zeitgeist_0.8.99~alpha1b-1ubuntu1~ppa1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/python-zeitgeist_0.8.99~alpha1b-1ubuntu1~ppa1_all.deb (--unpack):
 trying to overwrite '/usr/share/pyshared/zeitgeist/__init__.py', which is also in package zeitgeist-core 0.8.2-1
Errors were encountered while processing:
 /var/cache/apt/archives/python-zeitgeist_0.8.99~alpha1b-1ubuntu1~ppa1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


???

---

### Post by soryu on 2011-11-10
E: /var/cache/apt/archives/python-zeitgeist_0.8.99~alpha1b-1ubuntu1~ppa1_all.deb: trying to overwrite '/usr/share/pyshared/zeitgeist/__init__.py', which is also in package zeitgeist-core 0.8.2-1

---

### Post by thebananarepublican on 2011-11-11
I am having the same issue. Anyone find a fix yet? I can't seem to find one. Not really digging not being able to update my system.

---

### Post by lechien73 on 2011-11-11
Personally, I prefer the quick and dirty method for clearing the history.

```
cd ~/.local/share/zeitgeist
rm activity.sqlite
```

Reboot :)

---

### Post by soryu on 2011-11-11
installed zeitgeist actvity manager.
installed gnome activity manager.


cleared history in both and stopped logging.
activity still shown in unity "recent"

rebooting now.

---

### Post by andersaaberg on 2011-11-14
If you fancy not installing an extra repository to just make a dash configuration change, then you can use my fairly simple guide: [http://www.andersaaberg.dk/blog/blog/2011/unity-dash-privacy-at-ubuntu-11-10-oneiric-ocelot-hide-porn-folder/](http://www.andersaaberg.dk/blog/blog/2011/unity-dash-privacy-at-ubuntu-11-10-oneiric-ocelot-hide-porn-folder/)

---

### Post by soryu on 2011-11-14
i have logging stopped but i still see recent activity in unity dash.:confused:

---

