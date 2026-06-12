---
title: "root user"
date: 2006-03-10
forum: General Help
---

### Post by nahas on 2006-03-10
hi everyone,
     ubantu doesnt ask for a root passwd while installing.However when i tried to install vmware it says "do it as root user".i dont have a root user.what shall i do......pls help
regards

---

### Post by glug101 on 2006-03-10
When running the installer, put sudo in front of the command.  This should give you superuser capabilities.

If this is no good, try the following:
```
sudo su
passwd 
(enter new passwd)
(confirm new passwd)

```

This should set a root passwd for your computer.  I personally setup the second option because most of the linux world seems to take root account for granted.  However, I barely use root.

Hope this helps :)

---

