---
title: "mysql and bacula temporal dependency"
date: 2011-04-04
forum: General Help
---

### Post by watricky on 2011-04-04
I've noticed an odd issue with installing bacula on Ubuntu. If I install bacula and mysql at the same time, bacula's configuration is broken:

apt-get installs but doesn't configure mysql-server
apt-get installs and configures bacula but fails due to mysql not yet functioning
apt-get then configures mysql-server

The pragmatic approach is to install mysql completely and then, afterwards, to install bacula. The "oops" workaround is to remove bacula completely then reinstall. There's probably a better way to do this part:
> for i in bacula{,-{c{lient,o{mmon,nsole}},director-{common,mysql},fd,sd{,-mysql},server}} ; do sudo dpkg -P $i ; done
> apt-get install bacula

Is there a better way to get around the whole issue other than just telepathically knowing to install mysql first?

---

