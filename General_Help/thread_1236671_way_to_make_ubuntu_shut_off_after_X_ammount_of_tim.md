---
title: "way to make ubuntu shut off after X ammount of time?"
date: 2009-08-10
forum: General Help
---

### Post by matt12345 on 2009-08-10
Well I'm running a server and I would like it to be up for 7 hours a day at the most, is there any thing I can do like setting a timer for my computer to shut off at a certeen time?

---

### Post by CatKiller on 2009-08-10
Check out **man shutdown**. You can use shutdown to shut the computer down at a given time or after a given period of time. It needs to be run as root.

If you want the computer to shut down at a certain time every day, you could set up a cron job for it.

---

