---
title: "Samba reinstall problem"
date: 2010-09-24
forum: General Help
---

### Post by slamMaster on 2010-09-24
Since I upgraded to 10.04 I haven't needed samba, so I hadn't installed it.  When I tried recently I screwed it up, so I tried to uninstall it with 

```
sudo apt-get remove --purge samba smbfs
```

And it worked, but now when I reinstall it it's not creating any configuration files (/etc/samba/...).  Any ideas?  Did I uninstall it incorrectly?

---

### Post by searchfgold6789 on 2010-09-24
You might try reinstalling all your printers to get the config files.
You removed the packages correctly.

---

