---
title: "aptitude &amp; /etc configuration files"
date: 2010-02-21
forum: General Help
---

### Post by benoitcsirois on 2010-02-21
Hi!

I removed some files from /etc using rm -rf (more specifically, rm -rf /etc/postgresql* , thus getting rid of /etc/postgresql and /etc/postgresql-common ). I thought that by re-installing postgresql using apt-get install, the default configuration files would also be placed in /etc, but I thought wrong.

How do I recover Ubuntu's default /etc configuration files for a specific app? (In this case postgresql)

Thanks

---

### Post by nixclusive on 2010-02-21
```
apt-get --reinstall install postgresql
``` should work.

---

### Post by benoitcsirois on 2010-02-22
> **nixclusive said:**
> ```
apt-get --reinstall install postgresql
``` should work.

Hi! I have tried the sudo apt-get --reinstall install postgresql-8.4 and the /etc/postgresql folder still does not exist.

How can I re-instate Ubuntu's original /etc/postgresql/ folder (containing folders 8.3 and/or 8.4)?

Thanks

---

### Post by benoitcsirois on 2010-02-22
Ok this has been fixed. In case anyone has this same problem, here's how I fixed it (probably not kosher, so only do this if you know what you're doing):

```
sudo apt-get --purge remove postgresql-8.4 postgresql-8.3
sudo rm -rf /var/lib/postgresql
sudo apt-get --reinstall install postgresql-8.4
```

done!

-Ben

---

