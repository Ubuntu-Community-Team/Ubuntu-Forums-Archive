---
title: "mysql apparmor inode_permission error/warning reading /sys/devices/system/cpu/"
date: 2009-07-21
forum: General Help
---

### Post by meonkeys on 2009-07-21
I'm seeing a cryptic warning or error in /var/log/syslog while mysql is running:

```
Jul 21 20:33:05 scraps kernel: [312367.523998] type=1503 audit(1248226385.209:213): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=0 name="/sys/devices/system/cpu/" pid=451 profile="/usr/sbin/mysqld"
```

Is this a problem? MySQL seems to be running fine.

I'm using Ubuntu 9.04 and MySQL from the "mysql-server-5.1" package.

---

### Post by meonkeys on 2009-09-22
I fixed this, but I forgot what I did! I think I just needed to fix ownership or permissions of the place where MySQL stores its configuration or data files. These may have been part of the solution:

[http://brainwreckedtech.wordpress.com/2008/04/25/ubuntu-804-bug-with-mysql-and-apparmor/](http://brainwreckedtech.wordpress.com/2008/04/25/ubuntu-804-bug-with-mysql-and-apparmor/)

[https://launchpad.net/bugs/201799](https://launchpad.net/bugs/201799)

---

### Post by LepeKaname on 2010-01-29
I had the same error when upgrading to Karmic. The problem was that I didn't replace my.cnf file during the upgrade and it seems that some line in the file was causing the problem. So, try using the one named "my.cnf.dpkg-dist" that should be placed in /etc/mysql/.

That worked for me.

---

### Post by meonkeys on 2010-02-03
Here's the fix. Added the following rule to /etc/apparmor.d/usr.sbin.mysqld :

```
/sys/devices/system/cpu/ r,
```

Then ran

```
sudo /etc/init.d/apparmor reload
sudo /etc/init.d/mysql restart
```

(there's probably an upstart equivalent I should be using, but that works)

[More details on apparmor]("http://en.opensuse.org/AppArmor_Geeks#Anatomy_of_a_Profile").

---

