---
title: "Syslog and sensord messages"
date: 2010-01-02
forum: General Help
---

### Post by sh_kilnao on 2010-01-02
I have a problem with a syslog setting to log all sensors deamon messages. Basically, the specified file remains empty, while all messages end up in syslog and daemon.log, for no apparent reason. This below is what I believe is the relevant portion from /etc/syslog.conf:

```

*.*;auth,authpriv.none          -/var/log/syslog
daemon.*                        -/var/log/daemon.log
*.=info;*.=notice;*.=warning;\
        auth,authpriv.none;\
        cron,daemon.none;\
        mail,news.none;\
        local4.none;local4.warn -/var/log/messages

#sensors
local4.*                          /var/log/sensors
local4.alert                    /dev/console
local4.alert                    *
```The file /var/log/sensors exists but is empty! The selected facility for sensord is local4 and release is 8.10. Any ideas? 

Cheers,

Nikola

---

