---
title: "What is sending email to root@externalserver.com (exim4)"
date: 2012-02-04
forum: General Help
---

### Post by 5circles on 2012-02-04
I'm trying to figure out the source of some failing email to root@  on an internet server.  I don't know if it is anything to do with exim4, but that's the MTA.  

I can see the logs of the attempts with the external server in /var/spool/exim4/msglog, and what looks like a log of messages received by exim4 in /var/spool/exim4/input.  [Seems odd that I can't cd to some of the directories - even with sudo]  But I haven't been able to figure out the source of the emails.

I've searched all the mysql databases for the string - no luck.

I'm trying to search the entire disk for the string, but I'm not sure if I'm doing it correctly.  ```
sudo find / -print | sudo xargs grep string
``` 

Any ideas would be most appreciated.
Thanks

---

### Post by 5circles on 2012-02-04
Progress!

I set up a temporary forward on the external server so I could see the email.  It's coming from cron (or anacron) as the result of a faulty entry.

But I can't see why it's sending to [email]root@externalserver.com[/email].  I've looked in /etc/aliases - nothing unless that's not configured correctly.  
```
# See man 5 aliases for format
postmaster:    root
root: user
user: user@externalserver.com
```

Once I solve that, the other question is why exim4 is apparently trying every 5 seconds.

---

