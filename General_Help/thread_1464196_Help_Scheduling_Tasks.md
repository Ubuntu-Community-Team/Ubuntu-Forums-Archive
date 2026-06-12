---
title: "Help Scheduling Tasks"
date: 2010-04-27
forum: General Help
---

### Post by Nandus1 on 2010-04-27
Hello all,
I am attempting to get an Ubuntu 8.04 machine to restart daily at a specified time.

I installed Gnome-schedule to give me an easy way to schedule the task
using Cron.

In an attempt to test, I set the "Minute" and "Hour" to a specified time
22:45 and left the "Day", "Month" and "Weekday" fields blank.

In the "Command" field I typed in "sudo reboot".

Under the "Preview" area it says "On every day at 22:45". 

Note: I did not see any options to select AM or PM, so I chose to use the 
24hr format. 

Everything looked good to go, but when 10:45 came nothing happened. 

Any thoughts on what I am doing wrong?

Note: I am testing on a 9.10 box if that matters.

---

### Post by dcstar on 2010-04-28
> **Nandus1 said:**
> Hello all,
I am attempting to get an Ubuntu 8.04 machine to restart daily at a specified time.

I installed Gnome-schedule to give me an easy way to schedule the task
using Cron.

In an attempt to test, I set the "Minute" and "Hour" to a specified time
22:45 and left the "Day", "Month" and "Weekday" fields blank.

In the "Command" field I typed in "sudo reboot".
........

And are you there to type in the sudo password?

If you want to run root privilege commands then you must set it up in the root account:
```
sudo crontab -e
```
or this might also work:
```
gksudo gnome-schedule
```

---

### Post by Nandus1 on 2010-04-28
Hello,
Thank you for your reply. 

"And are you there to type in the sudo password?"

Not quite sure what you mean by that. I was not prompted to enter a 
password while setting up the task. Only the command.

Gnome-schedule does not ask for a password.

---

