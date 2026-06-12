---
title: "Notifications from gnome calendar do not respect the time zone"
date: 2012-07-21
forum: General Help
---

### Post by coverup1128 on 2012-07-21
My Ubuntu PC and my Google calendar are both set to a correct timezone (Australia, Sydney). The default email/calendar client is Evolution, which is set to use the system timezone. The Network time slider shows ON. However, the notifications about my Google calendar appointments show up about 10-11 hours later. I cannot blame Google for that, since email reminders arrive on time. The problem is somehow related to my computer. Can anybody please point out where i should look for a fix?

---

### Post by coverup1128 on 2012-07-24
Solved... My PC was configured to sync time with an ntp server. This is the default setting (The Network time slider shows ON), however it appears that the ntp package was not even installed! I pushed the slider to OFF, and notifications are now shown on time.

Nice work, Gnome/Unity developers, it took only four days for me to figure this out (that's a sarcasm, just in case...).

---

