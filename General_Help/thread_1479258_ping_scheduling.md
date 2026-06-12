---
title: "ping scheduling"
date: 2010-05-10
forum: General Help
---

### Post by uncr347ivenam3 on 2010-05-10
I'm performing network tests and would like to ping google every 15 seconds between 4pm and 8pm.  So far, the command I have is
```
$ ping -i 15 google.com
```
How should I go about creating the schedule?  Should I just create a cron task at 4pm to start the ping and then a cron task at 8pm to killall ping?  It seems like there is a much more elegant solution but I haven't found it.  Any suggestions?

---

