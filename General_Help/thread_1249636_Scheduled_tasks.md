---
title: "Scheduled tasks"
date: 2009-08-25
forum: General Help
---

### Post by seadt on 2009-08-25
Hi,

Is it possible to use "Scheduled tasks" if I (for example) want to:

first play a video-file in 2 hours and then play an other video-file in 3 hours
and after that start again first video...

If not...  How can I achieve "Autoplay" on my desktop??

---

### Post by jesuisbenjamin on 2009-08-25
You can find a program called Alarm Clock in your repositories that could do that for you.

---

### Post by seadt on 2009-08-26
I have installed the Alarm Clock, but even there I must set a terminal-command to start some video-player and I don't know how...

Is it possible ??  :confused:

---

### Post by The Cog on 2009-08-26
You can schedule one-off tasks with **at**. For example:
> steve@dingly:~$ **at 20:50**
warning: commands will be executed using /bin/sh
at> **export DISPLAY=:0.0**
at> **xeyes**
at> <EOT>
job 2 at Wed Aug 26 20:50:00 2009
Type all your commands at the at> prompt. After the last command is entered, press Ctrl-D which prints <EOT> and enters the job.

However, for regular repeating jobs, you should use the **cron** facility. This can run periodic jobs every 5 minutes, hourly, every thursday night etc. The job is entered into a table with the command **crontab -e**. It's a bit cryptic, so google for the file format and how to use it. If using cron, it is best to make a script containing the commands and then just enter a single command to run that script into crontab.

---

