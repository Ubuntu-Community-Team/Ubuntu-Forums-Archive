---
title: "dbus daemon, loads of activity (slowing down machine)"
date: 2010-03-24
forum: General Help
---

### Post by manolo_asdf on 2010-03-24
Hi,

when calling 'top' dbus is having load of activity ('dbus-monitor --session') outputs also a lot of action (see attachement). this has effect that my machine is slowing down and normal work takes ages.

I have no clue where the activity is coming from. I also had a look at [https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/441828](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/441828). But there are no unnormal devices plugged in... (just keyboard + cordless mouse).

when starting the machine the cpu load is ~9%. After a while (after 1 day) it goes up to 70-80%. the started applications do not change during that time. so i guess somewhere there is a leak.

thanks for help.

---

### Post by manolo_asdf on 2010-03-30
i removed evolution (anyway am using thunderbird). weirdly it (or some dependencies) was occupying system ressources.

this solved my issue.

---

### Post by manolo_asdf on 2010-04-19
damn it. my problems started again after last ubuntu automatic update.

does anyone have an advice how to analyze which program is causing this high dbus load?

thanks.

---

### Post by benplanet on 2010-04-20
I have the same problem, dbus deamon being a memory hog and my machine having a hard time coping with it

---

### Post by benplanet on 2010-04-21
anyone have any answers or tips about this dbus-deamon issue a bunch of people are facing??

thanks!

---

### Post by maxsharples on 2010-06-23
I also have this problem. Recently upgraded to 9.10 and noticed that my cursor is perpetually showing the loading/waiting status.

'top' shows dbus-daemon always at 10% cpu or more and 'dbus-monitor' spews forth and endless stream of structured data (similar to json).

My machine is a netbook (HP Mini) with no peripherals attached.

---

### Post by maxsharples on 2010-06-23
UPDATE:

Possibly relevant message in /var/log/messages

```
bonobo-activation-server (max-21898): could not associate with desktop session: Failed to connect to socket /tmp/dbus-oS94n4ThFo: Connection refused
```

And in /var/log/syslog (repeated many times)

```
gnome-session[1344]: CRITICAL: error getting session bus: Failed to connect to socket /tmp/dbus-oS94n4ThFo: Connection refused
```

---

### Post by maxsharples on 2010-06-27
Don't know if this is a solution for everyone or not, but I removed Ubuntu One Gnome client via Synaptic and the problem has disappeared.

---

### Post by maxsharples on 2010-07-05
hmmm, false alarm. problem persists, though not always commenced on start up. 

curiously, I did notice recently that it started when I loaded maps.google.com using the chrome browser.

if there are any solutions I would love to know, it is rather annoying.

---

### Post by Ganton on 2010-11-21
I used
```
sudo service dbus restart
```
the last time it happened to me.

---

### Post by dylan noktum on 2010-12-14
i am also having the same problem as this in 10.10 i closed x chat then it stoped its happend a few times but i dont realy know whats doing it and i really to know how to stop it from happening

---

