---
title: "apt-get looks for libdbus-c++ but can't find it"
date: 2011-10-26
forum: General Help
---

### Post by nickde on 2011-10-26
A few weeks ago I installed [sflphone using these instructions]("http://sflphone.org/download/stable-release") on 10.04 but now that I'm trying after a fresh installation it complains about a non existing package **libdbus-c++** (note [1]). I can see that a package **libdbus-c++-1-0** exists[2]. It looks like it must be the package that sflphone is looking for but with a different name. Is there something I can do to make it use the -1-0 package that does exist in the repositories?
The problem has [been reported]("https://projects.savoirfairelinux.com/issues/7124") to the developers of sflphone about 2 weeks ago but got no reply till now so I'm looking for alternatives. 

_______________________________________
Notes:
[1]
[FONT=Courier New]> sudo apt-get install  sflphone-common 
...
The following packages have unmet dependencies:
  sflphone-common: Depends: libdbus-c++ but it is not installable
[/FONT] 
[2]
[FONT=Courier New]> apt-cache search libdbus-c++
libdbus-c++-1-0 - C++ API for D-BUS (runtime package)
libdbus-c++-dev - C++ API for D-BUS (development package)
[/FONT]

---

### Post by nickde on 2011-10-31
I've documented a workaround here:
[https://projects.savoirfairelinux.com/issues/7124#note-3](https://projects.savoirfairelinux.com/issues/7124#note-3)

---

