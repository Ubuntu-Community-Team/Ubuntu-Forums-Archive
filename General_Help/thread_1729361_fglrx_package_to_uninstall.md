---
title: "fglrx package to uninstall?"
date: 2011-04-14
forum: General Help
---

### Post by 12dan4 on 2011-04-14
Updating my Ubuntu 10.04 using Update Manager is not working. "Not all packages can be installed" and asks me whether or not to do a partial upgrade. I suspect a problem with packages, since my last upgrade from 9.10 was successful, so I run sudo apt-get install -f. However, what returns is 9 not upgraded and 1 to remove, with fglrx being the package to remove. Why is this? My ati proprietary display driver is running fine. There are also 4 other packages that need uninstalling along with the "9 to upgrade." I can't do either action without encountering an unfavorable forced uninstall of fglrx.

I would like to get my update functionality back.

Please help!
Thanks

---

### Post by 12dan4 on 2011-05-22
I found the problem: fglrx was marked to be uninstalled in Synaptic. But I couldn't seem to unmark it. Every time I try to unmark the package, it goes back marked to be uninstalled if I restart Synaptic or reload.
The solution was to mark for reinstall, and apply, which would fix the problem.

---

