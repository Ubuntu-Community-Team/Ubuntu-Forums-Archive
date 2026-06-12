---
title: "crontab help"
date: 2011-03-04
forum: General Help
---

### Post by usman291 on 2011-03-04
hey, 

 I have a java code to run on my university LAB server (which is fedora distro) and collects netFlows and other traffic/network statistics. I made a shell(bash) script to execute my java code and it is working fine. Then i made a cron job to run my shell script after every 10 mins and it is also working fine (i confirmed it with the output sent to my mail and also, every time my java code executes, it produce some output files which are also being created). Now i am trying to do same job on a newly built machine with ubuntu 10.04. Shell script is running fine producing desired results from java code and cron jobs are added to crontab (confirmed with 'crontab -l' command) BUT it doesn't generate any mail and also, no file is produced. I am working as root on this new machine with ubuntu 10.04.

 kindly help

regards,
usman

---

### Post by usman291 on 2011-03-04
hey, 

I have a java code to run on my university LAB server (which is fedora distro) and collects netFlows and other traffic/network statistics. I made a shell(bash) script to execute my java code and it is working fine. Then i made a cron job to run my shell script after every 10 mins and it is also working fine (i confirmed it with the output sent to my mail and also, every time my java code executes, it produce some output files which are also being created). Now i am trying to do same job on a newly built machine with ubuntu 10.04. Shell script is running fine producing desired results from java code and cron jobs are added to crontab (confirmed with 'crontab -l' command) BUT it doesn't generate any mail and also, no file is produced. I am working as root on this new machine with ubuntu 10.04.

kindly help

regards,
usman

---

### Post by cariboo on 2011-03-05
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by gmargo on 2011-03-05
You must install an [MTA]("http://en.wikipedia.org/wiki/Message_transfer_agent") such as postfix or exim4, or else cron output is tossed.

---

### Post by CharlesA on 2011-03-05
You can also redirect the output of the commands run in cron to a file.

```
somecommand > /tmp/somelog 2>&1
```

---

### Post by usman291 on 2011-03-07
thanks all, 

 though redirecting output to log file wasn't the solution, but i somehow manage to solve my problem with the help of generated logs.

---

### Post by CharlesA on 2011-03-07
Glad you got it working - don't forget to mark the thread as solved from thread tools.

---

