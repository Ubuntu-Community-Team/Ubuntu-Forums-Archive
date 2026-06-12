---
title: "Task scheduling with granularity to seconds"
date: 2010-09-05
forum: General Help
---

### Post by kestrelcz on 2010-09-05
I am looking for scheduler, which will have option to setup tasks start in seconds. I am planning to use it for capturing photos of satellites and stars using gphoto2. Crontab, Gnome scheduler and Kalarm hase granularity only minutes.
Suggestions appreciate ;).

---

### Post by jaya28inside on 2010-09-09
uh? neverheard taking picture of stars....

---

### Post by Rubi1200 on 2010-09-09
Not sure if I can answer your question in its entirety, but you might want to use crontab and add a loop forever script that uses the sleep command to achieve what you want in terms of granularity.

---

### Post by dcstar on 2010-09-09
> **Rubi1200 said:**
> Not sure if I can answer your question in its entirety, but you might want to use crontab and add a loop forever script that uses the sleep command to achieve what you want in terms of granularity.

Use basic crontab with a script where you pass the seconds value in the particular minute to trigger to it, and then a sleep" command inside the script which uses it.

---

### Post by kestrelcz on 2010-09-13
Thanks all - adding sleep is the best solution):P.

---

