---
title: "Autostart of Mysql server"
date: 2010-07-23
forum: General Help
---

### Post by Thoralyon on 2010-07-23
I'm using a mysql-database with amarok.
Suddenly mysql is no longer starting on boot. I can start it fine using sudo service mysql start, but I don't want to have to start it manually every time, Putting it into the startup applications should work, but I'd rather know why it stopped working in the first place.
Could some kind of software update be to blame? (I don't recall there being any mysql updates though)

---

### Post by ajgreeny on 2010-07-23
It will not start with just your user Startup Applications list, I don't think so anyway, if it needs sudo to start.  You could add it to the /etc/.rc.local file by adding the line ```
service mysql start
```just above the final **exit 0** line.

It would, however, be good to know why it has stopped, I agree.  I presume this is not an amarok update problem?  I do not use KDE so have no idea about that possibility.

---

### Post by rafe101 on 2010-07-27
I have the exact same problem and I know it was after an update because I started the computer, ran the updates, restarted and--bam--no more mysql. It's really made the mythbox unusable for my wife.

---

### Post by rafe101 on 2010-07-27
Okay, adding the command in rc.local does get it started automatically again. I had seen some suggestions to modifying the /etc/init/mysql.conf file, but nothing was working for me. If this was something caused by an update that they will fix, will calling mysql twice cause problems?

---

### Post by rafe101 on 2010-08-26
As an update: I had some mysql updates the other day and just commented out the line in the rc.local file. It starts up fine again.

---

