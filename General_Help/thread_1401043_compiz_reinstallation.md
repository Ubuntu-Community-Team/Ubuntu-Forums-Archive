---
title: "compiz reinstallation"
date: 2010-02-07
forum: General Help
---

### Post by Odd_sam on 2010-02-07
I am having trouble figuring out how to re install compiz. I was being stupid and running a script on my computer that would help me install compiz from git. and well some how the script didn't work and I am trying to revert back to a more stable version of compiz.

I tried the following:
```

sam@rawr:~$ sudo apt-get install compiz compiz-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compiz is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package compiz has no installation candidate
sam@rawr:~$ sudo apt-get remove compiz compiz-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compiz is not installed, so not removed
Package compiz-core is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 22 not upgraded.

```

I quite confused that compiz is not somewhere in my repositories. Could someone assist me? I am running 9.10. I believe the script uninstalled compiz I did notice that part unfortunately I did not grab the log.

---

