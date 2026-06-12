---
title: "libnet1 dpkg error"
date: 2010-03-09
forum: General Help
---

### Post by compgeek83 on 2010-03-09
I'm getting the following errors when ever i try to do an update, i've tried sudo apt-get clean, autoclean, autoremove, any ideas?

```
desktop:/var/lib/dpkg/info$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libnet1
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 193kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 259138 files and directories currently installed.)
Removing libnet1 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing libnet1 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 libnet1
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by compgeek83 on 2010-03-09
sorry fixed it myself
sudo apt-get install libnet1 seems to have done the trick

---

