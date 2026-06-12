---
title: "squid cache_dir in different partion problem"
date: 2009-10-15
forum: General Help
---

### Post by tr3s on 2009-10-15
hi! i managed to install and can successfully start squid when it's using the default cache_dir (/var/spool/squid). but when i changed the cache_dir to a separate partition (/cache/squid), then a permission denied error is encountered in creating cache files when i restart squid.

i'm running fedora 11. /cache/squid directory is already owned by the squid user and has 710 permission, just like the permission of /var/cache/squid. the /cache partition is a member of a LVM group and has ext4 as its filesystem.

what else could be the problem?

many thanks

---

### Post by blueridgedog on 2009-10-16
Any chance there is a typo in the config?  Can you open up the permissions to 777 and test?

---

