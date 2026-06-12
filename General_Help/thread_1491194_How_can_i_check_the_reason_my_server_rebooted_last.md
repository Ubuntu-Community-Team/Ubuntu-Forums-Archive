---
title: "How can i check the reason my server rebooted last night?"
date: 2010-05-23
forum: General Help
---

### Post by malarie on 2010-05-23
Hi,

I've got KArmic 9.1 Server, no UI.  My server rebooted yesterday and I dont know why.  I checked the logs and i did not find anything..  I suspect  security updates but im not sure where i can find the logs for the automatic updates installation.  I thought they were turned off.. I checked var logs but not sure which file to check..

Worst.. I have a cronjob that monitors my  jboss server every 5 mins and it did not even restart the web server... :S
Thanks.

---

### Post by new_tolinux on 2010-05-23
> **malarie said:**
> I've got KArmic 9.1 Server, no UI.  My server rebooted yesterday and I dont know why.  I checked the logs and i did not find anything..  I suspect  security updates but im not sure where i can find the logs for the automatic updates installation.
As far as I know there's no such thing as automatic updates on a server. I guess you'll have to look for the reason elsewhere. Can't it be a (very short) power-loss?

---

### Post by malarie on 2010-05-25
> **new_tolinux said:**
> As far as I know there's no such thing as automatic updates on a server. I guess you'll have to look for the reason elsewhere. Can't it be a (very short) power-loss?

Cant really be a powerloss, the server is connected to a UPS.
And I think the security updates are getting installed.. Although i have no entries in cron..

---

