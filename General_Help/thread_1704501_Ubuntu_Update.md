---
title: "Ubuntu Update"
date: 2011-03-10
forum: General Help
---

### Post by dcool76 on 2011-03-10
I have a question my server shows in CPU usage 
 
99.8% apt-get -qq -y update
 
It will never go away even if there is a new update and I install them it will still be there If I kill the process it will come back in a few hours. Is there a way I can disable the update. Ill check my self every so often I just dont want this running in the backfground using that much CPU or is there a fix list both if you can thanks.

---

### Post by dcool76 on 2011-03-10
I have no updates to install and it just started running again and it will not go away till I kill it.

---

### Post by Cheesehead on 2011-03-10
What do your /var/log/syslog, /var/log/messages, and /var/log/apt/history.log show?

---

### Post by plucky on 2011-03-11
> **dcool76 said:**
> I have a question my server shows in CPU usage 
 
99.8% apt-get -qq -y update
 
It will never go away even if there is a new update and I install them it will still be there If I kill the process it will come back in a few hours. Is there a way I can disable the update. Ill check my self every so often I just dont want this running in the backfground using that much CPU or is there a fix list both if you can thanks.

If the process is "update-xapian-index" let it run and it will eventually stop.If you kill it,it will restart as it hasn't updated the apt-get database.Seems to run after every Software update.

Good Luck

---

