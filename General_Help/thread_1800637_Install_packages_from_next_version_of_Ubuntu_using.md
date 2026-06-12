---
title: "Install packages from next version of Ubuntu using apt?"
date: 2011-07-09
forum: General Help
---

### Post by hymerman on 2011-07-09
I want to install something that's only in oneiric, but currently have natty. Specifically, The 'nut' package is at version 2.6.0 in the natty repository and 2.6.1 in oneiric, and 2.6.0 has a major problem with my UPS:

[http://packages.ubuntu.com/hu/natty/nut](http://packages.ubuntu.com/hu/natty/nut)
[http://packages.ubuntu.com/hu/oneiric/nut](http://packages.ubuntu.com/hu/oneiric/nut)

Is there some way for me to upgrade to the version in the oneiric repository without completely upgrading to oneiric? I want to remain on natty until oneiric is released.

---

### Post by Bachstelze on 2011-07-09
You can download the package manually from packages.ubuntu.com and install it.  It's simple but the problem is that if there are updates in the Oneiric repositories, you will miss them.  Alternatively, you can add the Oneiric repositories you your sources.list, and tell Apt to only get the nut package from them (and all other packages from Natty).  To do this, add something like that to /etc/apt/preferences:

```
Package: nut
Pin: release n=oneiric
Pin-Priority: 990

Package: *
Pin: release n=natty
Pin-Priority: 990
```

---

