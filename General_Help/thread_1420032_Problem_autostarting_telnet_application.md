---
title: "Problem autostarting telnet application"
date: 2010-03-02
forum: General Help
---

### Post by MemorX on 2010-03-02
Hi, I have an application that uses a telnet console, and I have an autostart script to start it (and check that it is running).

The problem is that if the program is not startet by root, or by using sudo, I cant get access to the telnet console, it just says "connection refused".

The application works fine, but I cant acces its console, so I have to shut it down, and then restart it with sudo to be able to log in to it.

Anyone know how to make the script start the application with enough rights?

This is the script I am using. It is run every minute with crontab.

```

#!/bin/sh
SERVICE='application'

if ps ax | grep -v grep | grep $SERVICE > /dev/null
then
    echo "$SERVICE service running, everything is fine"
else
    echo "$SERVICE is not running"
    application
fi

```

Any help would be greatly appreciated!

---

### Post by dcstar on 2010-03-02
> **MemorX said:**
> Hi, I have an application that uses a telnet console, and I have an autostart script to start it (and check that it is running).

The problem is that if the program is not startet by root, or by using sudo, I cant get access to the telnet console, it just says "connection refused".

The application works fine, but I cant acces its console, so I have to shut it down, and then restart it with sudo to be able to log in to it.
.........
Any help would be greatly appreciated!

You have the root crontab with that job, not the user crontab.

---

