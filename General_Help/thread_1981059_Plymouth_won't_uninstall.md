---
title: "Plymouth won't uninstall"
date: 2012-05-16
forum: General Help
---

### Post by Lucradia on 2012-05-16
I don't want plymouth, as X doesn't start right away (causing plymouth to look all garbled and whatnot due to my drivers not installed either.) Can I remove plymouth somehow? Because when I do **sudo apt-get purge plymouth** (I always do purge when I remove something, as it also removes configs) it gives the following error,

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 upstart : Depends: initscripts
           Depends: mountall
           Depends: ifupdown (>= 0.6.10ubuntu5)
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

---

