---
title: "ndiswrapper to module"
date: 2009-08-14
forum: General Help
---

### Post by warlord130 on 2009-08-14
I was reading how to fix my wg111t and am stuck.

im getting my info from [here]("https://help.ubuntu.com/community/WifiDocs/Device/WG111T").

Im stuck at were I add Ndiswrapper to module.

Is this how it is supposed to go
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

ndiswrapperor am I doing Something wrong. (OR is this problem STILL not solved)

---

### Post by rudy.b on 2009-08-14
That will load the ndiswrapper module at boot time.  If you want to check if the driver is installed, you can use this command to list the installed drivers: ```
ndiswrapper -l
```

---

