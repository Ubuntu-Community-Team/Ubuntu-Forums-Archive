---
title: "Identify process that creates a file?"
date: 2011-10-17
forum: General Help
---

### Post by digitijit on 2011-10-17
Something in one of my systems (10.04 LTS, x86_64) has started creating null (0-byte) directory files under /home (i.e., /home/user/~).  My first thought was a cron job gone bad, but that was not the case.  I have also searched the logs for events with time stamps matching file creation time, without success.  How might I find the specific process that is creating those files?  

My (limited) understanding of tools like inotify is that they report events, but not the processes that cause them.

Cheers,
DI

---

