---
title: "where is other_vhosts_access.log configured?"
date: 2011-03-11
forum: General Help
---

### Post by xirochanh on 2011-03-11
my box is ubuntu 10.10, installed with apache2.
I can find where access.log in error.log configured: apache2.conf & sites-available/default.
But can not find where to configure other_vhosts_access.log, I want to stop this log.

Please help

---

### Post by Smika on 2012-07-24
etc/apache2/conf.d/other-vhost-access-log

# Define an access log for VirtualHosts that don't define their own logfile
CustomLog ${APACHE_LOG_DIR}/other_vhosts_access.log vhost_combined


Comment out the last line.

---

