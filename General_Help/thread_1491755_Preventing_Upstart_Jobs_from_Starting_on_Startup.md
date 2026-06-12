---
title: "Preventing Upstart Jobs from Starting on Startup"
date: 2010-05-24
forum: General Help
---

### Post by szim90 on 2010-05-24
Hello,

I'd like to reconfigure vsftpd so that it does not start on boot (and I can enable/disable it using service vsftpd start/stop).

Though I've seen posts in the forums that stated that upstart jobs can be disabled by moving the /etc/init/job.conf file, other sites commented that the original file will be recreated on updates.

The other two suggestions were to alter the upstart script such that either the process starts on never:
```

start on (never
        and filesystem
        and net-device-up IFACE!=lo)
stop on runlevel [!2345]

```

or tell the process to stop on run level 2:
```

start on (filesystem
        and net-device-up IFACE!=lo)
stop on runlevel [0123456]

```

Will either of these edits stay in effect if vsftpd is updated? Of the two methods, is one more correct?

Thanks for any help with this.

Regards,
szim90

---

### Post by szim90 on 2010-07-21
Bump?

---

### Post by ayourk on 2011-08-11
My suggestion would be to disable the start and stop lines in /etc/init/vsftpd.conf

---

