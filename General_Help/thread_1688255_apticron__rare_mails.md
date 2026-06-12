---
title: "apticron : rare mails"
date: 2011-02-15
forum: General Help
---

### Post by magowiz82 on 2011-02-15
Hi everyone,
some time ago I installed apticron to keep track of when updatetes are available and which are the updates. The problem is that rarely I receive mails. In the file /etc/apticron/apticron.conf I put only my email address. I think that the settings are ok because I received some mails from apticron. The mail agent is postfix.
Often it happens that I connect to machines via ssh and I can see in the motd that updates are available but I didn't receive any mail.

---

### Post by kellemes on 2011-02-15
Cannot help you here.
I did find an alternative methode that you could try..
[cron-apt howto and more]("https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo")

---

### Post by magowiz82 on 2011-02-16
I think I solved : I disabled updating in update-manager and this morning I received mails from all my pc. I think that update-manager overlaps database update in apticron that doesn't see any change.

---

