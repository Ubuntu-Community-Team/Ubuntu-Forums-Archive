---
title: "Wine seems to have uninstalled itself"
date: 2009-12-30
forum: General Help
---

### Post by AlphaWhelp on 2009-12-30
So I'm not exactly sure when this happened but Wine has seemed to uninstall itself, at least partially.  The Wine option is still in the menu but there are no wine icons or anything and wine itself seems to be gone.  sudo apt-get purge wine tells me it is not installed, here is the output of sudo apt-get install wine: 
```
[sudo] password for mario: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages

```

I would really like to get wine working again without having to restore a backup

---

