---
title: "/etc/init.d script not loading on startup"
date: 2011-07-14
forum: General Help
---

### Post by gnaget on 2011-07-14
I fear I may have missed something simple, but I have a "miner" under /etc/init.d

```

#!/bin/sh

### BEGIN INIT INFO
# Provides:             Miner
# Required-Start:       $all
# Required-Stop:        $all
# Default-Start:        2 3 4 5
# Default-Stop:         0 1 6
# Description:          Phoenix miner
### END INIT INFO

case "$1" in
  start)
    echo -n "Starting Miner...\n"
    cd /opt/phoenix
    screen -dmS miner -c /opt/phoenix/.screenrc-miner
    ;;
  stop)
    echo -n "Stopping Miner...\n"
    screen -S miner -X quit
    ;;
  restart)
    screen -S miner -X quit
    screen -dmS miner -c /opt/phoenix/.screenrc-miner
    ;;
esac

```All this does is start up a screen session with windows defined in .screenrc-miner.  The file is owned by root, and has perm 755.  

```

chkconfig -l miner
miner                     0:off  1:off  2:on   3:on   4:on   5:on   6:off

```Is is setup to launch on runlevel 2, which I can confirm:
/etc/rc2.d$ ls -la S03miner
lrwxrwxrwx 1 root root 15 2011-07-13 18:06 S03miner -> ../init.d/miner

I can also manually can start, stop, and restart on it.  However, it does not launch on startup.  I can find no messages in /var/log/syslog showing any attempt to start it.  Did I miss a step?

FYI: uname -a
Linux wrath 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 athlon i386 GNU/Linux

---

### Post by gnaget on 2011-07-14
bump to keep it from being lost to the ether that is page 3+

---

### Post by mikejonesey on 2011-07-14
init.d scripts don't run at start, rc inits do, give it a run level 2 and bobs ur uncle, fannys ur aunt lol...

didn' read fully lol;

cd /etc/rc2.d
ls

:)

try again;

mv /etc/rc2.d/S03miner /etc/rc2.d/S20miner

---

### Post by gnaget on 2011-07-14
wait, what?

a link does exist in rc2.d as I explained in my OP

---

### Post by gnaget on 2011-07-15
I hate to bump this again, but there has to be a simple reason why this is not working

---

### Post by sakishrist on 2011-07-15
Hi there,

In the rc?.d folders there is a readme file that says you have to run **update-rc.d script defaults**.

I think I had a similar problem in the past but I don't remember what it was.

Good luck!

---

### Post by gnaget on 2011-07-15
> **sakishrist said:**
> Hi there,

In the rc?.d folders there is a readme file that says you have to run **update-rc.d script defaults**.

I think I had a similar problem in the past but I don't remember what it was.

Good luck!


I originally used update-rc.d to generate the sym link, and it didn't work.  chkconfig does the same thing, and is a lot more user friendly

---

### Post by gnaget on 2011-07-15
Solved, screen requires a user context, so I solved it by changing my /etc/init.d/miner script to call su <username> -c 'screen ....'

---

