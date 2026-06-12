---
title: "Crond not working?"
date: 2006-02-06
forum: General Help
---

### Post by Im_Just_GrayT on 2006-02-06
how do i check if the cron deamon is running?

the reason i ask is that im trying to set up an alarm clock using cron. I have a bash script that starts music when i execute it. but for some reason when i set up a crontab to run the script, it does nothing at the time i set in the crontab.

when i run "crond" at the command line, bash just gives me a "command not found" error

I'm really confused, anyone know whats going on?:confused:

---

### Post by dcstar on 2006-02-06
[QUOTE=Im_Just_GrayT]how do i check if the cron deamon is running?

the reason i ask is that im trying to set up an alarm clock using cron. I have a bash script that starts music when i execute it. but for some reason when i set up a crontab to run the script, it does nothing at the time i set in the crontab.

when i run "crond" at the command line, bash just gives me a "command not found" error

I'm really confused, anyone know whats going on?:confused:[/QUOTE]
ps -ef | fgrep cron

---

### Post by jcl on 2006-02-06
Assuming cron is running (which it probably is), did you check your mail, cron will send the user mail if the job failed for whatever reason. Also it might help if you would post a copy of your crontab file (crontab -l as the owner of the cron job).

---

