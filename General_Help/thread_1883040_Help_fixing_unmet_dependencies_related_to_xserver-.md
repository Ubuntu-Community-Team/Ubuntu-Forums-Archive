---
title: "Help fixing unmet dependencies related to xserver-xorg-core"
date: 2011-11-18
forum: General Help
---

### Post by ryankask on 2011-11-18
X often crashes on me. I want to investigate further and am trying to install the debug symbols.

It seems I have some unmet dependencies which prevent me from installing the packages.

Here is the error I get:

```
$ sudo apt-get install xserver-xorg-core-dbg                                                    
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-dri : Breaks: libgl1-mesa-glx (< 7.10.3-0ubuntu1) but 7.10.2-0ubuntu2 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

If I open the update manager, I can see three packages that want to be upgraded but can't:

[LIST=1]
[*]xserver-xorg-core (Installed version: 2:1.10.1-1ubuntu1.3, Available version: 2:1.10.4-1ubuntu4.2)
[*]libgl-mesa-dri (Installed version: 7.10.2-0ubuntu2, Available version: 7.11-0ubuntu3)
[*]libgl-mesa-glx (Installed version: 7.10.2-0ubuntu2
Available version: 7.11-0ubuntu3)
[/LIST]

How can I find out what is stopping these packages from being upgraded?

Thanks!

---

### Post by ryankask on 2011-11-18
I was able to fix this problem.

I used to use the [xorg-edgers PPA]("https://launchpad.net/~xorg-edgers/+archive/ppa").

The instructions on that page indicate that

```
If you are upgrading from one release to another and are using this PPA, be sure to install ppa-purge and use it to downgrade all of this PPA's packages before the upgrade or you will have a broken system. In 11.04, you also need to sudo apt-get purge libffi6 and libglapi-mesa after the ppa-purge to upgrade to oneiric.
```

When I purged libglapi-mesa, the packages were able to upgrade properly.

---

