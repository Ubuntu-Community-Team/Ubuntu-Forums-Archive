---
title: "Automatic shutdown issue"
date: 2010-12-07
forum: General Help
---

### Post by mattjones124 on 2010-12-07
This seems so silly. I set up a script or something months ago to automatically shutdown my workstation at 10 AM every day. I no longer wish to run this script, but I have no idea where I set it up.  Which log file can I look at to see how it is shutting down?

---

### Post by wojox on 2010-12-07
Maybe a cron job. Look here [Crontab]("https://help.ubuntu.com/community/CronHowto")

---

### Post by matt_symes on 2010-12-07
Hi

If it is a cron job there will be an entry in the syslog telling  you the command run (in this case the script).

System->Administration->Log file viewer and select syslog.

or at a terminal

cat /var/log/syslog | grep -i cron

Kind regards

---

### Post by mattjones124 on 2010-12-07
There is nothing in my crontab. Weird, no?

---

### Post by 3rdalbum on 2010-12-07
Check the Anacrontab, and the /etc/rc.local file, and the "System>Preferences>Session" window.

---

### Post by matt_symes on 2010-12-07
Hi

> There is nothing in my crontab. Weird, no?Is that _your_ cron tab? Have you checked roots cron tab? and looked in the logs?

At a terminal  type

```
sudo -i
```(enter your password)

```
crontab -e
```Kind regards

---

### Post by mattjones124 on 2010-12-08
Anacrontab - nothing
/etc/rc.local file - nothing
"System>Preferences>Session" window - nothing
root crontab - nothing

Any other suggestions?

---

### Post by matt_symes on 2010-12-08
Hi

Did you approach it a different way? When you switch on the computer is one of the startup scripts setting an 'at' job and running the script that way. Something like

at 10:00 < /script/to/run.sh

the command 

```
atq
```will tell you if you have any queued jobs and when they are scheduled to run.

is there anything in

/etc/at.allow

Kind regards

---

### Post by mattjones124 on 2010-12-13
I ran the atq command and nothing shows.
There is nothing in /etc/at.allow.
I am pretty baffled here.

---

### Post by matt_symes on 2010-12-13
Hi

In one of your init scripts do you have a command that says...

shutdown 10:00

Might be work greping to check this and that might take a little while.

It might even be worth just greping shutdown although you will get a number of false positives if it is there.

Kind regards

---

### Post by mattjones124 on 2010-12-14
I was logged into SSH this morning when it shut down. This was the broadcast message:


Broadcast message from root@ubuntu
	(unknown) at 10:00 ...

Does this tell you guys anything?

I tried to grep my entire hard drive, but it took so long that it restarted while it was performing.

Just to confirm, grep -r "shutdown 10:00" will scan the entire file system for those words?

---

### Post by matt_symes on 2010-12-14
Hi

> Broadcast message from root@ubuntu
(unknown) at 10:00 ...

Does this tell you guys anything?

Not really, no. It only says root has issued the command.

```
grep -l -r "shutdown 10:00" / 2> /dev/null
```

This will search for shutdown 10:00 and list the files that contain it. Small L switch.

You can ```


man grep
```

to get more info. This search is dependant on you having entered shutdown 10:00
It might just be worth searching for shutdown (in case you did not type shutdown 10:00 exactly)

```
grep -l -r "shutdown" /
```

but this, i suspect, will give a whole host of false positives. It will also take ages. It might be worth recursing the directories under root separately, missing out the directories like /dev and /proc etc.

.ie.
```
grep -l -r "shutdown" /etc
```

You might want to redirect the output to a file as well.

... And it still might not be what is shutting the system down ;)

Kind regards

---

