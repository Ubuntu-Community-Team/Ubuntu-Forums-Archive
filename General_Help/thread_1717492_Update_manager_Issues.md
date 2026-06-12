---
title: "Update manager Issues"
date: 2011-03-29
forum: General Help
---

### Post by sports fan Matt on 2011-03-29
I get when trying to update: W:Ignoring file 'tiheum-equinox-maverick.list.old' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension, E:Type 'u-mozilla-daily/ppa/ubuntu' is not known on line 3 in source list /etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-maverick.list'..why?

###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted universe

###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################


deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) maverick-getdeb games
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) maverick main
deb [http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu) maverick main
deb [http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu) maverick main
deb [http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu) maverick main

---

### Post by plucky on 2011-03-30
Post output from a terminal of ```
ls -l /etc/apt/sources.list.d/
```

> W:Ignoring file 'tiheum-equinox-maverick.list.old' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension,

Rename the file to tiheum-equinox-maverick.old or delete it.

> E:Type 'u-mozilla-daily/ppa/ubuntu' is not known on line 3 in source list /etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-maverick.list'

Post output of ```
cat /etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-maverick.list
```

> deb [http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu) maverick main
deb [http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu) maverick main
deb [http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu) maverick main


You only need one not three of the same line.

Good Luck

---

### Post by sports fan Matt on 2011-03-30
total 156
-rw-r--r-- 1 root root 138 2011-03-29 21:10 alecive-antigone-maverick.list
-rw-r--r-- 1 root root 138 2011-03-29 21:10 alecive-antigone-maverick.list.save
-rw-r--r-- 1 root root  82 2011-03-04 16:44 am-monkeyd-nautilus-elementary-ppa-lucid.list.distUpgrade
-rw-r--r-- 1 root root 119 2011-03-04 20:00 am-monkeyd-nautilus-elementary-ppa-lucid.list.save
-rw-r--r-- 1 root root 174 2011-03-29 21:10 am-monkeyd-nautilus-elementary-ppa-maverick.list
-rw-r--r-- 1 root root 174 2011-03-29 21:10 am-monkeyd-nautilus-elementary-ppa-maverick.list.save
-rw-r--r-- 1 root root 126 2011-03-29 21:10 bisigi-dev-maverick.list
-rw-r--r-- 1 root root 126 2011-03-29 21:10 bisigi-dev-maverick.list.save
-rw-r--r-- 1 root root   0 2011-03-18 12:34 do-core-ppa-maverick.list
-rw-r--r-- 1 root root  66 2011-03-18 12:34 do-core-ppa-maverick.list.save
-rw-r--r-- 1 root root 140 2011-03-29 21:10 elegant-gnome-ppa-maverick.list
-rw-r--r-- 1 root root 140 2011-03-29 21:10 elegant-gnome-ppa-maverick.list.save
-rw-r--r-- 1 root root  55 2011-03-04 16:44 fta-ppa-lucid.list.distUpgrade
-rw-r--r-- 1 root root  92 2011-03-04 20:00 fta-ppa-lucid.list.save
-rw-r--r-- 1 root root   0 2011-03-18 12:28 fta-ppa-maverick.list
-rw-r--r-- 1 root root  92 2011-03-18 12:28 fta-ppa-maverick.list.save
-rw-r--r-- 1 root root  68 2011-03-04 16:44 nikount-orta-desktop-lucid.list.distUpgrade
-rw-r--r-- 1 root root 105 2011-03-04 20:00 nikount-orta-desktop-lucid.list.save
-rw-r--r-- 1 root root 146 2011-03-29 21:10 nikount-orta-desktop-maverick.list
-rw-r--r-- 1 root root 146 2011-03-29 21:10 nikount-orta-desktop-maverick.list.save
-rw-r--r-- 1 root root 416 2011-03-29 21:10 opera.list
-rw-r--r-- 1 root root 416 2011-03-29 21:10 opera.list.save
-rw-r--r-- 1 root root 888 2011-03-29 21:10 pidgin-developers-ppa-maverick.list
-rw-r--r-- 1 root root 888 2011-03-29 21:10 pidgin-developers-ppa-maverick.list.save
-rw-r--r-- 1 root root 148 2011-03-30 10:28 pidgin-ppa.list
-rw-r--r-- 1 root root 148 2011-03-29 21:10 pidgin-ppa.list.save
-rw-r--r-- 1 root root 128 2011-03-29 21:10 shutter-ppa-maverick.list
-rw-r--r-- 1 root root 128 2011-03-29 21:10 shutter-ppa-maverick.list.save
-rw-r--r-- 1 root root  62 2011-03-04 16:44 tiheum-equinox-lucid.list.distUpgrade
-rw-r--r-- 1 root root  99 2011-03-04 20:00 tiheum-equinox-lucid.list.save
-rw-r--r-- 1 root root 134 2011-03-29 21:10 tiheum-equinox-maverick.list
-rw-r--r-- 1 root root 134 2011-03-20 16:44 tiheum-equinox-maverick.list.old
-rw-r--r-- 1 root root 134 2011-03-29 21:10 tiheum-equinox-maverick.list.save
-rw-r--r-- 1 root root  61 2011-03-04 16:44 tualatrix-ppa-lucid.list.distUpgrade
-rw-r--r-- 1 root root  98 2011-03-04 20:00 tualatrix-ppa-lucid.list.save
-rw-r--r-- 1 root root 132 2011-03-29 21:10 tualatrix-ppa-maverick.list
-rw-r--r-- 1 root root 132 2011-03-29 21:10 tualatrix-ppa-maverick.list.save
-rw-r--r-- 1 root root  72 2011-03-04 16:44 ubuntu-mozilla-daily-ppa-lucid.list.distUpgrade
-rw-r--r-- 1 root root 109 2011-03-04 20:00 ubuntu-mozilla-daily-ppa-lucid.list.save
-rw-r--r-- 1 root root 154 2011-03-29 21:10 ubuntu-mozilla-daily-ppa-maverick.list
-rw-r--r-- 1 root root 154 2011-03-29 21:10 ubuntu-mozilla-daily-ppa-maverick.list.save

deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) maverick main
# disabled on upgrade to maverick
u-mozilla-daily/ppa/ubuntu maverick main

---

### Post by sports fan Matt on 2011-03-30
Can't remember this morning how to Rename the file to tiheum-equinox-maverick.old

---

### Post by plucky on 2011-03-30
> **sox fan Matt said:**
> Can't remember this morning how to Rename the file to tiheum-equinox-maverick.old

```
gksudo nautilus
``` and navigate to the /etc/apt/sources.list.d and delete all the files with lucid in the name and rename the file tiheum-equinox-maverick.list.old to tiheum-equinox-maverick.old or delete it.

Good Luck

---

### Post by sports fan Matt on 2011-03-30
I'll tackle this when I get home :)

---

