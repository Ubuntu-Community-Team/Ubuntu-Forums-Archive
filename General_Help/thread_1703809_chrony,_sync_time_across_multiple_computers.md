---
title: "chrony, sync time across multiple computers"
date: 2011-03-09
forum: General Help
---

### Post by Gatemaze on 2011-03-09
Hello,

I am trying to sync multiple computers with common time without caring whether this time is the correct one, ie. it is synced with a web time server. I have setup a machine as the master. The rest of the computers sync to this master using "ntpdate -b <master_ip>" which is the /etc/crontab so it executes every 5 mins. The problem I am facing is that some of the machines are on the wifi and because I am doing large transfers of data the network saturates, which results in the ntpdate having a lag and large drift. Is there any way I can setup the chrony deamon to run as a client too and are there any benefits there?

Thanks.

---

