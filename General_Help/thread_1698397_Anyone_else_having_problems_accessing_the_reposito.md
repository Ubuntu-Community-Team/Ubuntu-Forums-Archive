---
title: "Anyone else having problems accessing the repositories?"
date: 2011-03-02
forum: General Help
---

### Post by imbjr on 2011-03-02
Started yesterday. A typical run is like:

> 
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages
  502  apt-cacher: libcurl error: Failed connect to archive.canonical.com:80; Operation now in progress
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources
  404  Unable to connect to extras.ubuntu.com
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages
  404  Unable to connect to extras.ubuntu.com
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz)  502  apt-cacher: libcurl error: Failed connect to archive.canonical.com:80; Operation now in progress

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  404  Unable to connect to extras.ubuntu.com

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Unable to connect to extras.ubuntu.com

E: Some index files failed to download, they have been ignored, or old ones used instead.


Yes, I'm using apt-cacher, but that should not matter.

Looks like extras.ubuntu.com and archive.canonical.com are struggling.

---

### Post by mastablasta on 2011-03-02
yesterday i had 3 - 7KiB/s transfer on updates. my connection is 20/20Mbit :-O
 
i also heard some others reported slow downs. not sure why. i use local repo server so i though it's a local issue.

---

### Post by jamting on 2011-03-02
Me to! Seems like it causes Ubuntu Software Centre to hang also.

/Mattias

---

### Post by Frogs Hair on 2011-03-02
The U.S sever was terrible yesterday , it took five attempts to update . I got my Mozilla daily update a few minutes ago with no problems. Lucky maybe ?

---

### Post by imbjr on 2011-03-02
> **Frogs Hair said:**
> The U.S sever was terrible yesterday , it took five attempts to update . I got my Mozilla daily update a few minutes ago with no problems. Lucky maybe ?

The problem seems intermittent. It cleared up enough for me to pull the latest kernel updates down.

---

### Post by Temporary Saint on 2011-03-02
Yup, had the problem yesterday and today as well.

Steve

---

### Post by ubudog on 2011-03-02
> **imbjr said:**
> The problem seems intermittent. It cleared up enough for me to pull the latest kernel updates down.

Yep, same here.

---

### Post by 45acp on 2011-03-02
Same here.

---

### Post by ubudog on 2011-03-02
Strange. :(

---

### Post by houseworkshy on 2011-03-02
Sometimes things do slow down, and there is a lot of internet blocking going on ( historic events in the middle east, north Africa and surrounding regions )  so perhaps that is affecting routes.  One can select "other" when when choosing where to download from and your system will ping around for whichever server happens to be best for you at the moment.  That often helps a lot, I do it for any large install.  Oddly my system sticks on Brazil for a while while doing the tests,  no idea why ..it's been that way for years.
System>Admin>Software sources and there is a hot spot on the first tab.  You can get to the same place via settings in synaptic.

---

