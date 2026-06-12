---
title: "Desktop Clock incorrect"
date: 2012-02-04
forum: General Help
---

### Post by SadaraX on 2012-02-04
I am using KDE 4.8 with Kubuntu 11.04. A few days ago the clock on my KDE ubuntu desktop became wrong and nothing I can do will make it fix itself. It is off by 20 hours and says "UTC".

When I try to adjust the time or region, I get the error message: "Unable to connect time server: Public Time Server (pool.ntp.org)"

I have edited /etc/default/rcS and set UTC=no, but even after a reboot the time is wrong. Help please?

UPDATE: Now I see the problem was most likely caused by updating to KDE 4.8. I simply needed to change the Digital Display Settings (not the time itself) to NOT show UTC.

---

### Post by llamabr on 2012-02-04
I had to install ntpdate:

```
sudo apt-get install ntpdate
```

then, it's just a matter of 

```
sudo ntpdate pool.ntp.org
```

or your favorite ntp server.  You also might want to try messing with your TZ setting:

[http://www.cyberciti.biz/faq/linux-unix-set-tz-environment-variable/](http://www.cyberciti.biz/faq/linux-unix-set-tz-environment-variable/)

---

### Post by SadaraX on 2012-02-05
> **llamabr said:**
> I had to install ntpdate:

```
sudo apt-get install ntpdate
```

then, it's just a matter of 

```
sudo ntpdate pool.ntp.org
```

or your favorite ntp server.  You also might want to try messing with your TZ setting:

[http://www.cyberciti.biz/faq/linux-unix-set-tz-environment-variable/](http://www.cyberciti.biz/faq/linux-unix-set-tz-environment-variable/)

Thank you.

Though now I see the problem was most likely caused by updating to KDE 4.8. I simply needed to change the Digital Display Settings (not the time itself) to NOT show UTC.

---

