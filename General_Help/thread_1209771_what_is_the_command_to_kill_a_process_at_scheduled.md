---
title: "what is the command to kill a process at scheduled time"
date: 2009-07-10
forum: General Help
---

### Post by brad_pitt on 2009-07-10
Hi All,

I used to play songs in my laptop and i would schedule a job like below in windows that would kill vlc process and shuts down my machine

at 19:50 tskill vlc
at 19:52 shutdown -s

I am looking for commands which serve the same purpose above in ubuntu.

Regars
Brad

---

### Post by t4thfavor on 2009-07-10
```

sudo crontab -e

50 19 * * * /bin/killall vlc
52 19 * * * /bin/poweroff

```


EDIT:

Sorry, I take for granted that people know what crontab is. It is the Linux equivalent of "at". 

To add an entry you type in "crontab -e" on a terminal.

The first field is the minute to execute the command, the second is the hour, third is the day of week, month, year, and final is the command to execute.

for the commands you showed, you will need root privileges you get those by prepending "sudo" to your command. 

You may need to put those into the root crontab which you can do by issuing "sudo su" and entering your password, and then the "crontab -e"

Sorry for being so vague the first time.

---

### Post by kerry_s on 2009-07-10
at 19:50 tskill vlc = **kill -9 vlc** or **killall vlc** (" **man kill** " for more info)

at 19:52 shutdown -s = **sudo halt** or **sudo poweroff** or **sudo shutdown -ah now** (requires root permission, so you'll need to set that up, shutdown has a shutdown.allow file you just add your user to. read the " man shutdown " )

---

### Post by CaptainMark on 2009-07-10
I didnt know there was a command for this, i would find that quite useful can you show an example, say if i wanted to kill banshee at 11.15 pm, what line would to add to crontab

---

### Post by t4thfavor on 2009-07-10
```

# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7)  OR sun,mon,tue,wed,thu$
# |  |  |  |  |
# *  *  *  *  *  command to be executed
  15 23 * * * /bin/killall banshee

```

Hope this helps you. Also if you want to execute a certain command sometime in the near future, you can use the:

```

sleep numberOfSecondsToSleep; command

```
method, I used to use it to hang up my dial line after 4 hours.

---

