---
title: "Don't understand error message"
date: 2011-05-29
forum: General Help
---

### Post by jacatone on 2011-05-29
Been trying to install and uninstall some programs but keep getting the following error message:

E: I wasn't able to locate file for the linux-headers-2.6.35-28 package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

How do I fix this? Thanks.

---

### Post by Rubi1200 on 2011-05-29
Hi,
you can try troubleshooting with the following commands.

```
sudo apt-get install -f
sudo dpkg --configure -a
```

Please post back with the specific errors.

---

