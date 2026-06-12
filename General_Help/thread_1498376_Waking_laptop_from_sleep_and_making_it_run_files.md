---
title: "Waking laptop from sleep and making it run files"
date: 2010-05-31
forum: General Help
---

### Post by elidoperezmd on 2010-05-31
Hi all...

I have a laptop and wanna have it set up for going to sleep and waking up at certain time and then run certain files/programs.

i used a single program for this back in windows but cant remember the name...

Do yo know a program that will do this for me?

Thanks for replies / ur time

---

### Post by harrismh777 on 2010-05-31
what do you mean "wake-up"   from hibernate?  from suspend?

If what you want is for your laptop to run files at certain times use cron. 

crontab is configured (very flexible) for running "whatever" at specific times of the day, week, month, etc...    its easy to configure.

If you are talking about waking up from suspend you'll need to have some trigger (lan, keys, etc) that will bring the machine back so that the cron entries can fire.

---

### Post by sdennie on 2010-05-31
I believe you can do this if your hardware supports it but, I've not tried.  This seems to explain the process: [http://www.mythtv.org/wiki/ACPI_Wakeup#Archive:_Using_.2Fproc.2Facpi.2Falarm](http://www.mythtv.org/wiki/ACPI_Wakeup#Archive:_Using_.2Fproc.2Facpi.2Falarm)

After that, as posted above, you'd need a cron job that starts like 1 minute after the alarm wakeup.

---

### Post by tgalati4 on 2010-05-31
man cron
man crontab

Look in your BIOS for a wakeup time setting under power management.

There is no way to wake up a laptop with wireless that I know of.  You can wake up the machine using a wired connection.  Look into wakeonlan.

---

### Post by elidoperezmd on 2010-05-31
thanks all...ill try, and get back 2u

---

### Post by blackhawx on 2010-05-31
while on the topic, my system says the cron is installed but where is the execution button for it in ubuntu?  i look for it under applications and system but its not there.  

thanks

---

### Post by tgalati4 on 2010-06-04
Cron is always running:

ps -ef | grep cron

If you want to edit your own, person crontab:

crontab -e

Systemwide cron jobs are stored in /etc/crontab.

You can edit it to add systemwide jobs if you know what you are doing:

sudo cp /etc/crontab /etc/crontab.bak
sudo nano /etc/crontab

---

