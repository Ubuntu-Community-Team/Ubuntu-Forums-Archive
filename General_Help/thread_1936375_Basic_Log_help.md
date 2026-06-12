---
title: "Basic Log help"
date: 2012-03-05
forum: General Help
---

### Post by Damascushead on 2012-03-05
I when my laptop gets running with a lot of processes, I hear the fan start going into overdrive and recently a few times my laptop has even turned off, before I could check anything in System Monitor.   It is not the best laptop (Acer Aspire 4530) 2GB Ram, and an Athlonx2, so I am almost positive that it is overheating.  I just need some help knowing which basic log files to look in (if any) to see what the actual cause of shutdown may have been. I have dealt very little with log files as I have a bit of trouble understanding them.   Any help would be appreciated ! Thanks

---

### Post by Script Warlock on 2012-03-05
you can check also via "top" command to which process has eatin much of your machines resources or start to investigate inside the log file viewer. or sometimes fan are just clogged up with dusts.

---

### Post by efflandt on 2012-03-06
Logs are in /var/log.  If you are still running 10.10 the system log is **/var/log/messages**.  11.10 uses **/var/log/syslog** instead (if you upgraded and did not update your profile).  Not sure if that will tell you anything, especially if it powers off suddenly.

But as mentioned, **top** in a terminal can give you a live idea what is using the most resources.

---

### Post by Damascushead on 2012-03-06
Thanks this does help. Right now I either use System Monitor or conky, which I have configured slightly to show some live processes.
 
But efflandt those log files should help me, I will have to start exploring. I just needed to know which one(s) to look in, as there are so many I didn't want to begin a blind search. Hopefully there will be something logged in here as to what happened, even though the power randomly shut off. 
 
I will check it out. Thanks!

---

### Post by Damascushead on 2012-03-13
Hey Script Warlock,
 
Thanks for the "top" command advice. I have been using it like a madman for the last week. How could I have not known about this before. I am never using System Monitor again :p

---

