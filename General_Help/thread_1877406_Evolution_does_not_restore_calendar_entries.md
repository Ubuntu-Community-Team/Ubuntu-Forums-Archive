---
title: "Evolution does not restore calendar entries"
date: 2011-11-08
forum: General Help
---

### Post by rdh61 on 2011-11-08
Hi,

I am using Evolution version 2.30.3 on Ubuntu 10.10. After restoring from an evolution backup my calendar entries (appointments) are missing. Other data (messages, addresses) are backed up correctly.
Any help gratefully received.

Thanks.

---

### Post by dcstar on 2011-11-08
> **rdh61 said:**
> Hi,

I am using Evolution version 2.30.3 on Ubuntu 10.10. After restoring from an evolution backup my calendar entries (appointments) are missing. Other data (messages, addresses) are backed up correctly.
Any help gratefully received.

Thanks.

Look in the (hidden) .evolution/calendar/local/system folder, there should be a calendar.ics file that holds all your "Personal" calendar info.

Check inside the backup file for the same thing, and manually extract it if it is different.

---

### Post by rdh61 on 2011-11-08
Thanks for your answer. In actual fact, I didn't need to do what you suggested. Today my calendar entries appeared normally. I don't know whether it was simply an evolution restart or a reboot that did it, but it's all working now.

---

