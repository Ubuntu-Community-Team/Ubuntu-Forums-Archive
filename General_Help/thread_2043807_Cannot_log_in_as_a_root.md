---
title: "Cannot log in as a root"
date: 2012-08-17
forum: General Help
---

### Post by shakeitbaby on 2012-08-17
Hi,

After ```
chmod 777 -R /
``` I cannot log in as a root user ```
sudo su
``` gives me ```
sudo: must be setuid root
```

Could you give me any solution?

Thanks

---

### Post by sisco311 on 2012-08-17
Thread moved to **General Help**.

You changed the permissions of all files in / recursively. As far as I know, there is no automated way to fix the permissions. 

Your best and fastest option is to backup your data and reinstall Ubuntu.

---

### Post by lisati on 2012-08-17
You might also want to have a read of this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

