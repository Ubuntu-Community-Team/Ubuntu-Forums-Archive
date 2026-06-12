---
title: "apt-get error: segmentation fault"
date: 2010-04-28
forum: General Help
---

### Post by WinterWeaver on 2010-04-28
About a week ago, I was in the process of installing something via apt-get. The laptop crashed halfway through, and now I cannot install anything new, do any updates/upgrades. I also cannot open Synaptic.

When running apt-get in the terminal I get the following error:
Segmentation fault

Is there any way I can fix this?

This laptop is running Jaunty.

Thanks in advance

WW

---

### Post by Sin@Sin-Sacrifice on 2010-04-28
```
sudo rm -rf /var/cache/apt/*.bin
``` then try again.

---

### Post by WinterWeaver on 2010-04-28
Thank you that solved the problem :)

---

### Post by wickett on 2010-07-16
This didnt work for me, but this did:

[http://ubuntuforums.org/showthread.php?p=9597643#post9597643](http://ubuntuforums.org/showthread.php?p=9597643#post9597643)

---

