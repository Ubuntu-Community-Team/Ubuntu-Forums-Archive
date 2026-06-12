---
title: "Check unlock time"
date: 2011-02-24
forum: General Help
---

### Post by nnn= on 2011-02-24
Is there a way to see what time I unlocked the lock screen (by typing the password)?

---

### Post by thefasterblueone on 2011-02-24
Run this in terminal:

```
uptime
```

uptime gives a one line display of the following information.
The current time, how long the system has been running, how many users are  currently logged  on, and the system load averages for the past 1, 5, and 15 minutes.

---

### Post by nnn= on 2011-02-25
Thanks, but I meant not necessarily just the last time. I. e., all recent unlocks. And a log of when the user logged in would also be helpful.

---

### Post by thefasterblueone on 2011-02-25
Try this then,

```
last -F > ~/userlog.txt
```


This will create a log file of all the users and put it in your /home/_username_/userlog.txt

---

### Post by nnn= on 2011-02-25
That's great. What is the best way to go about learning what command one needs short of asking about it? Searching might not yield the desired results. And there are so many commands...

---

### Post by Telengard C64 on 2011-02-25
> **nnn= said:**
> What is the best way to go about learning what command one needs short of asking about it? Searching might not yield the desired results. And there are so many commands...

Overwhelming isn't it?

I don't know a simple answer that works for everyone, but there are a few tricks I find very helpful. Any of the following can find commands related to any topic, even if you don't know the name of a specific command.

```
apropos YOUR_TOPIC
man -k YOUR_TOPIC
info --apropos=YOUR_TOPIC

```

Either of these can find commands even if you don't have the program installed.

```
apt-cache search YOUR_TOPIC
aptitude search YOUR_TOPIC
```

Last trick is simple: Read, read, and read more.

If you know the name of **any** command related to your topic, read the manpage for that command. At the bottom of the manpage look for links to related manpages. Now read those too.

Read some of the free Linux books online, such as [http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz). Try some of the better known paper books too.

Actively search for new commands to master at sites like:
[http://www.tldp.org/](http://www.tldp.org/)
[http://www.gnu.org/manual/manual.html](http://www.gnu.org/manual/manual.html)
[http://en.flossmanuals.net/](http://en.flossmanuals.net/)
[http://linuxcommand.org/](http://linuxcommand.org/)
[http://ss64.com/bash/](http://ss64.com/bash/)

HTH

---

