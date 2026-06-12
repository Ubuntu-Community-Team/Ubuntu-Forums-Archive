---
title: "scheduling"
date: 2011-03-03
forum: General Help
---

### Post by Rakeshvijayan on 2011-03-03
Dear friends 


I wish to know  how to schedule my ubuntu shut down  in specific time 
in windows shutdown - s command possible
thanks

---

### Post by flipper T on 2011-03-03
sudo shutdown -h xx

where xx can either be the number of minutes until shutdown or the time of shutdown eg 65 or 01:20

ps open new terminal and sudo shutdown -c to cancel

---

### Post by Rakeshvijayan on 2011-03-06
how can i schedule this task for every day

---

### Post by anirudhtomer on 2011-03-07
There is a daemon callled "cron" which continuously checks the crontab (cron table).
You give schedule your tasks by making an entry in crontable. 

```
**[cron]("http://linux.die.net/man/8/cron")**(8) examines cron entries once every minute. 
The time and date fields are:  
field allowed values -----  --------------  
minute  
0-59  
hour  
0-23  
day of month  
1-31  
month  
1-12 (or names, see below)  
day of week  
0-7 (0 or 7 is Sun, or use names) 

```

Check out this link for sure: [http://linux.die.net/man/5/crontab](http://linux.die.net/man/5/crontab)

I hope it helps.

---

