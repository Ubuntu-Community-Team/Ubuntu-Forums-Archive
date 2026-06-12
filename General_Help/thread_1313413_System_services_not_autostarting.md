---
title: "System services not autostarting"
date: 2009-11-03
forum: General Help
---

### Post by nunki on 2009-11-03
I upgraded to Karmic, and have found that certain system services i.e. cron,ssh,atd,samba all need to be manually started. They used to autostart. I'm having a bit of trouble figuring out how to get these back to autostart.

---

### Post by Tipo on 2009-11-03
Try running 

```
chkconfig --list
```

in a Terminal window. Are the services you need autostarted listed as 'on' in runlevels 3, 4, and 5?

---

### Post by nunki on 2009-11-03
> **Tipo said:**
> Try running 

```
chkconfig --list
```

in a Terminal window. Are the services you need autostarted listed as 'on' in runlevels 3, 4, and 5?

No they are not. How do I get them where they need to be? Not sure whether I need anacron or cron to be autostarted. I think in Jaunty it was anacron.

Solution: I installed sysv-rc-conf and was able to set the correct startup levels for the services.

---

