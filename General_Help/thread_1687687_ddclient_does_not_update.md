---
title: "ddclient does not update"
date: 2011-02-14
forum: General Help
---

### Post by unix_user on 2011-02-14
I have Ubuntu 10.04 at home have a dyndns account. I use ddclient to update the IP periodically, I am noticing ddclient fails to update sometimes when home server cannot reach checkip.dyndns.org. I have setup to update every 300seconds, please let me know if where to start troubleshoot and resolve,

Has anyone noticed this and have suggestions on how to force ddclient to update itself. Let me know if further information is required to diagnose.

Thanks,

---

### Post by cariboo on 2011-02-14
It is pretty hard to update dns if you can't reach checkip.dyndns.org. I'd suggest trying mtr, to see if there is anything between you and it that isn't allowing a connection to go through.

```
mtr checkip.dyndns.org
```

---

### Post by unix_user on 2011-02-14
Thanks, I did run mtr and see output, however I don't see final destination, instead I see last line listed as 
15. ???

ddclient seems to have this problem only when it cannot reach checkip.dyndns.org. Is there a way to force ddclient to reach out periodically after a specified time. Most of the days it is fine and updates itself.

I couldn't find details on how to specify that settings, so I started looking for anyone who may have resolved this issue.

Thanks,  I have listed contents of /etc/ddclient.conf for reference.

protocol=dyndns2
daemon=300
use=web, web=checkip.dyndns.com, web-skip='IP Address'
server=members.dyndns.org
login=mylogin
password='mypasswd'
servernames...
ssl=yes
syslog=yes

---

