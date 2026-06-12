---
title: "package Dependicies cannot be resolved"
date: 2011-04-02
forum: General Help
---

### Post by suresh_vandiyur on 2011-04-02
Hi,

I try to install Adobe Flash player plugin 10 in ubuntu software center it shows error like this " Package dependicies cannot be resolved. and also i try install iptux that also not showing the installation option. how to fix the two issue. please help me.

Thank you,

Regards,
Suresh

---

### Post by Rubi1200 on 2011-04-02
Try the following commands in the terminal:

```
sudo apt-get install -f

sudo dpkg --configure -a

sudo apt-get update
```
If any of the commands returns with an error, please copy/paste here so we know what we are dealing with.

Thanks.

---

