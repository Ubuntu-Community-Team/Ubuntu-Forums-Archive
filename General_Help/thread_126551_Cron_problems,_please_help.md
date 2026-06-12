---
title: "Cron problems, please help?"
date: 2006-02-06
forum: General Help
---

### Post by Im_Just_GrayT on 2006-02-06
well I have been trying to create a linux based alarm clock to replace my windows one (i hate booting into that..."thing") but ive encountered some problems.

for a while i thought i had it set up right, but it didnt do anything. i have a good bash script that would start my music when i executed it, and i set a crontab entry to run that script at a time about 2 minutes in the future (to test it). but after 2-3 minutes it hadnt done anything. :confused: 

well now here comes the big problem. now when i run "cron" at the command line i get this:
```
cron: can't lock /var/run/crond.pid, otherpid may be 9268: Resource temporarily 
unavailable

```

any help would be greatly appreciated. (i cant stand booting into that...:evil: monster:twisted: , that microsoft calls an operating system, any longer)

Thanks!:)

---

### Post by RAOF on 2006-02-06
Wouldn't that error be because cron is already running (as a system service)?  I can't help with your actual *problem* but that error seems totally reasonable - you don't want 2 cron processes both trying to execute the same commands.

---

### Post by dcstar on 2006-02-06
[QUOTE=RAOF]Wouldn't that error be because cron is already running (as a system service)?  I can't help with your actual *problem* but that error seems totally reasonable - you don't want 2 cron processes both trying to execute the same commands.[/QUOTE]
Exactly, the issue I've noticed a few people with cron problems is that their commands may not have the full paths in them.

Also scripts run under cron should have full paths set in them - you cannot assume the paths set in a terminal session will be available to a cron job.

You should be able to see the cron error output by opening a terminal and using the "mail" command (for the user the cron job is running under, if it is a root job, then you must look at mail as root).

---

### Post by Im_Just_GrayT on 2006-02-06
whoa, i must be really tired (didnt get much sleep last night). i was typing "cron" instead of "crontab":mrgreen:  but i still have a problem.

my bash script will start my music when run manually but for some reason when i set up cron to run it, nothing happens

So anyone willing to help with this problem?
help would be greatly appreciately, thanks!

---

### Post by jcl on 2006-02-06
Like the poster said above, cron will send you a mail of the outcome of your job.  Post the contents of that mail to help us help you. Also a copy of your crontab would be nice :)

---

### Post by nanotube on 2006-02-06
why dont you paste your crontab entry in here so we can look to see if it is correct?

---

