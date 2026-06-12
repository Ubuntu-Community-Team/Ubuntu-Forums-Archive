---
title: "No such file or directory"
date: 2011-05-09
forum: General Help
---

### Post by HellionDarkLord on 2011-05-09
When trying to execute files I get this error. Doesn't matter where the file came from, internet download... etc... or what permissions it has.

The file IS there, and it is readable. I can change permissions for it and everything, but NOTHING will execute the file. I got fed up with this behavior and formatted the hard drive and reinstalled Ubuntu 10.04 LTS thinking that the LTS version might actually work. (no change)

```
ls -l X-PlaneDVDInstallerLinux
-rwxr-xr-x 1 gabriel gabriel 5635558 2011-01-31 17:29 X-PlaneDVDInstallerLinux

```

More than one file is affected, and I NEED this to work properly!! I use this computer for work and school. I have bills to pay and don't have the money to buy microsoft OS otherwise I would just revert to using M$windows which always seems to be able to execute EVERYTHING even if you don't want it to. =0)

---

### Post by oldos2er on 2011-05-10
You might see this error if you have a 64-bit system trying to run a 32-bit executable. If this is the case, install ia32-libs and try again.

---

