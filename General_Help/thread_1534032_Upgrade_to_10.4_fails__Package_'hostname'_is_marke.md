---
title: "Upgrade to 10.4 fails  Package 'hostname' is marked for removal."
date: 2010-07-18
forum: General Help
---

### Post by The Desert Fox on 2010-07-18
When I try to upgrade from 9.10 to 10.4 the upgrade fails.

I am not sure whats going on. I looked at the logs /var/log/dist-upgrade and grepped for hostname and found this:

apt.log:Investigating hostname
apt.log:Package hostname has broken PreDepends on upstart-job
apt.log:  Considering upstart 12956 as a solution to hostname 5103
apt.log:  Removing hostname rather than change upstart-job
main.log:2010-07-18 22:49:07,574 DEBUG The package 'hostname' is marked for removal but it's a ESSENTIAL package
main.log:2010-07-18 22:53:01,415 ERROR Dist-upgrade failed: 'The essential package 'hostname' is marked for removal.'


Why is hostname being marked for removal?

---

### Post by The Desert Fox on 2010-07-18
The attached file is actually a tgz as opposed to tar.

---

