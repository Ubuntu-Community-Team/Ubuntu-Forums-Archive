---
title: "Ubuntu 12.04 on amd64 unable to install eagle from repositories"
date: 2012-05-23
forum: General Help
---

### Post by neltnerb on 2012-05-23
I am running an up-to-date version of Ubuntu 12.04 on amd64 and am totally unable to get eagle to install from the repositories. I don't need the most up-to-date version of eagle, I only have a license for version 5 anyway, but I need it to *install*.

The error I am getting is as follows:
```

~$ sudo aptitude install eagle
The following NEW packages will be installed:
  eagle{b} 
The following packages are RECOMMENDED but will NOT be installed:
  extra-xdg-menus 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,580 kB of archives. After unpacking 15.5 MB will be used.
The following packages have unmet dependencies:
 eagle : Depends: eagle-data (= 5.11.0-1) but it is not going to be installed.
         Depends: ia32-libs (>= 20080808) but it is not going to be installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     eagle [Not Installed]

```

Obviously, I use this product extensively for professional work (I have an actual license after all), so this is extremely frustrating. I even tried putting in the natty repositories to try to satisfy these dependencies, but it was a no-go.

Anyone have any ideas? I can't imagine I am the only one with this issue, and I am loathe to try to install it directly from the eaglecad installer package for obvious integration reasons with apt/dpkg.

---

### Post by djenka on 2012-07-13
```
 sudo apt-get install eagle
```

and it worked for me.

Software centre has some issues

---

