---
title: "sysctl.conf Values Do Not Change"
date: 2012-08-13
forum: General Help
---

### Post by ShareBuntu on 2012-08-13
I've got three values in /etc/sysctl.conf that simply do not change after reboot. All the other values I've set change, except these three:

vm.dirty_background_ratio = 20
vm.dirty_ratio = 80
vm.dirty_writeback_centisecs = 1500

However, if I run sudo sysctl -p, they do update. Any ideas as to why these won't update on boot? Thanks!

---

### Post by ShareBuntu on 2012-08-13
Sorry to double-post, but it looks like this has been a bug in Ubuntu for six years now. Look here: [https://bugs.launchpad.net/ubuntu/+source/procps/+bug/50093]("https://bugs.launchpad.net/ubuntu/+source/procps/+bug/50093").

So, my question then is, how can I run "/sbin/sysctl -p /etc/sysctl.conf" and "/etc/init.d/sysfsutils restart" as root after I login without it asking for a password?

I'm surprised this has been a bug for so long (unless I'm mistaken)!

---

