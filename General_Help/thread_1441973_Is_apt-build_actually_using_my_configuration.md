---
title: "Is apt-build actually using my configuration?"
date: 2010-03-29
forum: General Help
---

### Post by sublimation on 2010-03-29
So I noticed something in the output of apt-build, and this seems to occur with every package I can catch a glimpse at this:

```
-----> Building deluge <-----
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value:
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package deluge
dpkg-buildpackage: source version 1.1.9+dfsg-1
dpkg-buildpackage: source changed by root <root@xxx>
dpkg-buildpackage: host architecture amd64
```

now considering my apt-build.conf is

```
build-dir = /var/cache/apt-build/build
repository-dir = /var/cache/apt-build/repository
Olevel = -O3
mtune = -mtune=amdfam10
options = " "
make_options = "  -j 5"
```

I'm wondering, does setting the config actually cause changes in the build?

on a related note, should I even bother running apt-build? There are a lot of differing opinions out there and I'd like some informed ones.

---

### Post by dxxvi on 2010-04-22
I'm having the same problem.

---

### Post by atomic777 on 2011-04-06
Anyone find a solution for this? I've been trying to get apt-build to work as well, but no luck getting it to use the flags I've put in the configuration file.

---

### Post by dxxvi on 2011-04-07
Not found the answer yet.

---

