---
title: "How to install freeradius?"
date: 2011-10-05
forum: General Help
---

### Post by ic-foxiq on 2011-10-05
Hello all.

I am trying to install freeradius in ubuntu 11.04.
I go to administration, synaptic package manager. Find freeradius, select it for installation, along with dependencies, then apply. Ubuntu says it installs it and configures it, and then says all is done.

Now, where the hell did it install it to, how can I use it?
I type "radiusd" and it responds to me something like:
The program 'radiusd' can be found in the following packages:
 * radiusd-livingston
 * xtradius
 * yardradius
Try: sudo apt-get install <selected package>

I try finding file "radiusd.conf", and there is no such file anywhere.
There is no /etc/raddb, and so on.

It is as if it never actually installed anything anywhere, but the packages in synaptic are displayed as installed.

Help me please, how can I install freeradius so I can use it?

---

### Post by TeoBigusGeekus on 2011-10-05
Try this find command
```
find / -iname "*freeradius*" 2>/dev/null
```

---

### Post by ic-foxiq on 2011-10-05
Here is the result:

foxiq@foxiq-VirtualBox:~$ find / -iname "*freeradius*" 2>/dev/null
/var/cache/apt/archives/freeradius-utils_2.1.10+dfsg-2ubuntu2_i386.deb
/var/cache/apt/archives/freeradius_2.1.10+dfsg-2ubuntu2_i386.deb
/var/cache/apt/archives/freeradius-common_2.1.10+dfsg-2ubuntu2_all.deb
/var/cache/apt/archives/libfreeradius2_2.1.10+dfsg-2ubuntu2_i386.deb
/var/lib/dpkg/info/freeradius-utils.list
/var/lib/dpkg/info/freeradius.shlibs
/var/lib/dpkg/info/freeradius-common.postinst
/var/lib/dpkg/info/libfreeradius2.md5sums
/var/lib/dpkg/info/freeradius-common.list
/var/lib/dpkg/info/freeradius.postinst
/var/lib/dpkg/info/freeradius.prerm
/var/lib/dpkg/info/freeradius-utils.md5sums
/var/lib/dpkg/info/freeradius-common.prerm
/var/lib/dpkg/info/freeradius.postrm
/var/lib/dpkg/info/freeradius-common.md5sums
/var/lib/dpkg/info/freeradius.list
/var/lib/dpkg/info/freeradius.md5sums
/var/lib/dpkg/info/libfreeradius2.list
/var/lib/dpkg/info/freeradius.conffiles
/var/lib/dpkg/info/freeradius-common.conffiles
/var/lib/dpkg/info/freeradius.preinst
/var/lib/dpkg/info/libfreeradius2.shlibs
/var/lib/dpkg/info/freeradius-common.postrm
/var/lib/update-rc.d/freeradius
/var/run/freeradius
/var/run/freeradius/freeradius.pid
/var/log/freeradius
/usr/sbin/freeradius
/usr/lib/freeradius
/usr/lib/freeradius/libfreeradius-eap-2.1.10.so
/usr/lib/freeradius/libfreeradius-radius-2.1.10.so
/usr/share/doc/freeradius-common
/usr/share/doc/freeradius
/usr/share/doc/libfreeradius2
/usr/share/doc/freeradius-utils
/usr/share/lintian/overrides/libfreeradius2
/usr/share/lintian/overrides/freeradius-utils
/usr/share/freeradius
/usr/share/freeradius/dictionary.freeradius
/usr/share/freeradius/dictionary.freeradius.internal
/usr/share/man/man8/freeradius.8.gz
/etc/rc1.d/K19freeradius
/etc/rc4.d/S50freeradius
/etc/init.d/freeradius
/etc/rc0.d/K19freeradius
/etc/rc2.d/S50freeradius
/etc/rc5.d/S50freeradius
/etc/freeradius
/etc/rc3.d/S50freeradius
/etc/default/freeradius
/etc/logrotate.d/freeradius
/etc/rc6.d/K19freeradius

---

### Post by TeoBigusGeekus on 2011-10-05
Try then
```
/usr/sbin/freeradius
```

---

### Post by ic-foxiq on 2011-10-06
Yes, it works! (after modifying some file permissions also)
Thanks!

---

