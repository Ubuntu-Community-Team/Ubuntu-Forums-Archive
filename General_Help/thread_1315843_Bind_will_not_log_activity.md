---
title: "Bind will not log activity"
date: 2009-11-05
forum: General Help
---

### Post by davehansen22 on 2009-11-05
Hello - Ubuntu 8.04.3

I'm using the bind9 package I installed with "apt-get install bind9"

I moved (and edited) my named.conf from another working installation.  It was logging just fine over there.
Here's an excerpt from my named.conf:

logging {
    channel my_channel {
        file "/etc/bind/log" versions 3 size 2m;
        severity dynamic;
    };

    category default { my_channel; };
    category queries { my_channel; };
};

/etc/bind is 775 owned by root, group is bind
/etc/bind/log is 664 owned by bind, group is bind
named is running as bind 

Is the bind implementation on Ubuntu different?  This worked just fine on Fedora 9 using bind version 9 that I downloaded from isc.org.

---

### Post by davehansen22 on 2009-11-06
Solved it.
/etc/apparmour.d/usr.sbin.named contained a line allowing rw to /var/log/named/**
I didn't choose that log location.  Once I moved the log and adjusted named.conf, everything worked.

---

