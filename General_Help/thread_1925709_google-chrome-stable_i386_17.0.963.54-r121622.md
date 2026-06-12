---
title: "google-chrome-stable i386 17.0.963.54-r121622"
date: 2012-02-15
forum: General Help
---

### Post by vasa1 on 2012-02-15
```
The following packages will be upgraded:
  google-chrome-stable
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.7 MB of archives.
After this operation, 4,096 B disk space will be freed.
Do you want to continue [Y/n]? y
Err http://dl.google.com/linux/chrome/deb/ stable/main google-chrome-stable i386 17.0.963.54-r121622
  404  Not Found [IP: 74.125.236.72 80]
Failed to fetch http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_17.0.963.54-r121622_i386.deb  404  Not Found [IP: 74.125.236.72 80]
```
Anyone having problems updating Chrome? I suspect it may be temporary ..

---

### Post by cneil on 2012-02-15
I'm having the same problem for Google Chrome with a 12.04 release.

---

### Post by vasa1 on 2012-02-15
[http://www.google.com/support/forum/p/Chrome/thread?tid=68c2a5693feb2f62&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=68c2a5693feb2f62&hl=en)

The funny thing is that there's no announcement here:
[http://googlechromereleases.blogspot.in/](http://googlechromereleases.blogspot.in/).

---

### Post by duncan12 on 2012-02-15
Same here, Ubuntu 11.10

---

### Post by vasa1 on 2012-02-15
Looks like it's been "fixed" in that the non-working update is not being offered currently.

---

### Post by aeiah on 2012-02-15
from here: [https://www.google.com/chrome/index.html?platform=linux](https://www.google.com/chrome/index.html?platform=linux)

it looks like the installer adds the chrome repo to /etc/apt/sources.list on installation. perhaps if you take a copy of /etc/apt/sources.list and reinstall it'll add the new links if they've changed

---

### Post by vasa1 on 2012-02-15
> **aeiah said:**
> from here: [https://www.google.com/chrome/index.html?platform=linux](https://www.google.com/chrome/index.html?platform=linux)

it looks like the installer adds the chrome repo to /etc/apt/sources.list on installation. perhaps if you take a copy of /etc/apt/sources.list and reinstall it'll add the new links if they've changed

My feeling is that, most likely, we don't have to do anything from our side. I think someone, somewhere, jumped the gun because the release (which I think will have an updated Flash) was not announced on the site where such announcements are made.

---

### Post by vasa1 on 2012-02-15
> **vasa1 said:**
> My feeling is that, most likely, we don't have to do anything from our side. I think someone, somewhere, jumped the gun because the release (which I think will have an updated Flash) was not announced on the site where such announcements are made.

Today, the update was successful without my having to do anything out of the way. The Chrome Releases page also references the update.

---

