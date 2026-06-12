---
title: "How to get time of disk formated or partition created or Ubuntu installed?"
date: 2011-01-13
forum: General Help
---

### Post by abcuser on 2011-01-13
Hi,
I need to know when I have bought a notebook. I know I have formatted disk myself and partition created and Ubuntu installed.

Is there any way I can get info when I bought a notebook? Like time of disk formatting, partitions created, Ubuntu installed?

My system: Ubuntu 8.04
Thanks

---

### Post by solar george on 2011-01-13
Try
```
sudo cat /var/log/installer/syslog
```
to access the installed logs. If you don't have that file try looking around /var/log for something similar (I think theres another posibility but I can't recall it right not).

---

### Post by oldfred on 2011-01-13
I run this report on my system config and it shows create & changed dates for my NTFS & ext partitions.


HTML version of info
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html

---

