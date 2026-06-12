---
title: "Schedule unattended updates to install at a specific time"
date: 2010-12-08
forum: General Help
---

### Post by CharlesA on 2010-12-08
Hiya,

I've been quite puzzled by the behavior of unattended updates - it seems it runs the updates at or before 7am (on all the server installs I've got).

They are only set to do security updates unattended, but what I am wondering is if there is a way to change the time that they install? I want the updates to install early in the morning, at like 3am or such, so I can reboot the machine when I get up if needs a reboot.

I found a few mentions about it, but nothing specifically talking about the time.

[http://forums.overclockers.com.au/showthread.php?p=12604154](http://forums.overclockers.com.au/showthread.php?p=12604154)
[https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)
[https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo](https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo)

Any ideas?

Thanks.

---

### Post by Rubi1200 on 2010-12-08
Hi Charles,
not sure if this helps, but in this link:
[http://www.vanutsteen.nl/2008/06/09/unattended-upgrades-on-a-ubuntu-hardy-server/](http://www.vanutsteen.nl/2008/06/09/unattended-upgrades-on-a-ubuntu-hardy-server/)

One of the respondents (LeonB) suggests editing crontab to adjust the time to your needs.

---

### Post by CharlesA on 2010-12-08
Thanks Rubi. That kinda helps, but I would have thought there would have been an easier way to set the time.

No big deal, but it would be nice to have it to install updates and reboot, if needed, before I leave for work.

EDIT: Looks like you can edit /etc/crontab to set the time you want it to run.

Thanks Rubi. :)

---

### Post by Rubi1200 on 2010-12-09
You are more than welcome Charles :)

---

