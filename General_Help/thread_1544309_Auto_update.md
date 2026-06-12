---
title: "Auto update"
date: 2010-08-02
forum: General Help
---

### Post by Cavs23 on 2010-08-02
Seeing as ubuntu doesn't have a feature to auto update at a specific time, I made a cron command to do it. But I am pretty sure I did it wrong because it doesn't work.

```
30 1 * * * root (apt-get -y update && apt-get -y safe-upgrade) > /home/ron/cronglog.log

```

Ignore the misspelling in the cron log name.

---

### Post by Cavs23 on 2010-08-02
Bump

---

### Post by hansdown on 2010-08-02
Hi Cavs23.

You can set these with the update manager.

Click system> administration> update manager.

Click "settings", in the bottom left corner.

Click "updates".

Under, automatic updates, check the boxes for, 

-install security updates without confirmation

-download all updates in the background

---

### Post by Cavs23 on 2010-08-02
I already know that. I want to update at a specified time, not whenever the manager feels like it.

---

### Post by Cavs23 on 2010-08-04
Bump

---

### Post by dino99 on 2010-08-04
install cron-apt

[http://www.debianadmin.com/automatic-update-of-packages-using-cron-apt.html](http://www.debianadmin.com/automatic-update-of-packages-using-cron-apt.html)

[https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo](https://help.ubuntu.com/community/AutoWeeklyUpdateHowTo)

---

