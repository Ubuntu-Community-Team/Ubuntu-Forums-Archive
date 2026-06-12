---
title: "Apt not working - Segmentation faulty tree"
date: 2010-02-24
forum: General Help
---

### Post by SchizmWolf on 2010-02-24
Hey all, I'm running Kubuntu 9.04 right now. It's working fine except the aptitude program is giving me errors. It all started a few days ago after my system failed a boot-up routine check of drives, rebooted, and ran fine after that. Now, though, whenever I type in "sudo apt-get install -insert whatever here-" it gives me the following output (for example, epiphone):
```
schizm@schizm-laptop:~$ sudo apt-get install epiphone
[sudo] password for schizm:
Reading package lists... Done
Segmentation faulty tree... 50%
schizm@schizm-laptop:~$

```
Any ideas???

---

### Post by n0dix on 2010-02-24
try
```
sudo rm /var/cache/apt/*.bin
```

---

