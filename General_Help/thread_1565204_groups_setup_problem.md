---
title: "groups setup problem"
date: 2010-08-31
forum: General Help
---

### Post by borepstein on 2010-08-31
Hi all,

We have a bunch of Linux machines (OpenSuSE, CentOS, Ubuntu) authenticating via NIS. If you are a member of multiple groups you come up as such on all systems but Ubuntu (via regular login) where id only shows your primary group. If you SSH into an Ubuntu machine your groups come up normally.

Example:


[adelaide@bepstein][~] id
uid=3010(bepstein) gid=3011(bepstein) groups=3011(bepstein)
[adelaide@bepstein][~] ssh adelaide
bepstein@adelaide's password: 
Linux adelaide 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

65 packages can be updated.
25 updates are security updates.

Last login: Wed Aug 18 08:23:52 2010 from 192.168.65.246
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

[adelaide@bepstein][~] id
uid=3010(bepstein) gid=3011(bepstein) groups=3011(bepstein),3023(admin),3300(video),10000(nrims-users),10001(nrims-admin)
[adelaide@bepstein][~] 


Any idea why this would be?

Thanks.

Boris.

---

### Post by efball3 on 2010-09-08
see [http://ubuntuforums.org/showthread.php?t=1471711&highlight=nis+groups](http://ubuntuforums.org/showthread.php?t=1471711&highlight=nis+groups)
and
[https://bugs.launchpad.net/ubuntu/+source/nis/+bug/553142](https://bugs.launchpad.net/ubuntu/+source/nis/+bug/553142)

This fix worked for me:
edit /etc/nsswitch.conf
to have
group: compat nis
(instead of just "group: compat")

---

