---
title: "Error encountered when running init bash script."
date: 2010-04-16
forum: General Help
---

### Post by touchring on 2010-04-16
Hi, i'm a newbie.

I'm trying to get a daemon to start automatically using an init bash script - i suppose this is what it is called.  :)

This is what I did to 'install' the script.

sudo cp inittestdaemon /etc/init.d/ 
sudo update-rc.d inittestdaemon defaults 91
sudo chmod 777 /etc/init.d/inittestdaemon

The script didn't work, so I tried running it directly on the terminal and this is the error which i got:

> line 36: syntax error near unexpected token '{
line 36: 'start_service() {Here's my code:

The script.  Grateful for any pointers.  :)

```
#!/bin/sh
#/etc/init.d/inittestdaemon


### BEGIN INIT INFO
# Provides:          twistedplugin
# Required-Start:    $all
# Required-Stop:     $all
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Starts a service for the Twisted plugin 'twistedplugin'
# Description:       Just an example for http://twistedmatrix.com/trac/ticket/3434
### END INIT INFO
# Author: Garret Heaton (powdahound@gmail.com)

PATH=/bin:/usr/bin:/sbin:/usr/sbin

DAEMON=/home/user/Desktop/Testdaemon/testdaemon
SERVICE_NAME=testdaemon
SERVICE_DIR=/home/user/Desktop/Testdaemon/
PIDFILE=$SERVICE_DIR/testdaemon.pid
LOGFILE=$SERVICE_DIR/testdaemon.log
# DAEMON_OPTS="--pidfile=$PIDFILE --logfile=$LOGFILE twistedplugin"
DAEMON_OPTS="-r&"nn

if [ ! -x $DAEMON ]; then
  echo "ERROR: Can't execute $DAEMON."
  exit 1
fi

if [ ! -d $SERVICE_DIR ]; then
  echo "ERROR: Directory doesn't exist: $SERVICE_DIR"
  exit 1
fi

start_service() {      <---  line 36
  echo -n " * Starting $SERVICE_NAME... "
  start-stop-daemon -Sq -p $PIDFILE -x $DAEMON -- $DAEMON_OPTS
  e=$?
  if [ $e -eq 1 ]; then
    echo "already running"
    return
  fi

  if [ $e -eq 255 ]; then
    echo "couldn't start :("
    return
  fi

  echo "done"
}

stop_service() {  
  echo -n " * Stopping $SERVICE_NAME... "
  start-stop-daemon -Kq -R 10 -p $PIDFILE
  e=$?
  if [ $e -eq 1 ]; then
    echo "not running"
    return
  fi

  echo "done"
}

case "$1" in
  start)
    start_service
    ;;
  stop)
    stop_service
    ;;
  restart)
    stop_service
    start_service
    ;;
  *)
    echo "Usage: /etc/init.d/$SERVICE_NAME {start|stop|restart}" >&2
    exit 1   
    ;;
esac

exit 0

```

---

### Post by dcstar on 2010-04-17
> **touchring said:**
> Hi, i'm a newbie.

I'm trying to get a daemon to start automatically using an init bash script - i suppose this is what it is called.  :)

This is what I did to 'install' the script.

sudo cp inittestdaemon /etc/init.d/ 
sudo update-rc.d inittestdaemon defaults 91
sudo chmod 777 /etc/init.d/inittestdaemon

The script didn't work, so I tried running it directly on the terminal and this is the error which i got:

Here's my code:

The script.  Grateful for any pointers.  :)

```
#!/bin/sh
#/etc/init.d/inittestdaemon


### BEGIN INIT INFO
# Provides:          twistedplugin
# Required-Start:    $all
# Required-Stop:     $all
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Starts a service for the Twisted plugin 'twistedplugin'
# Description:       Just an example for http://twistedmatrix.com/trac/ticket/3434
### END INIT INFO
# Author: Garret Heaton (powdahound@gmail.com)

PATH=/bin:/usr/bin:/sbin:/usr/sbin

DAEMON=/home/user/Desktop/Testdaemon/testdaemon
SERVICE_NAME=testdaemon
SERVICE_DIR=/home/user/Desktop/Testdaemon/
PIDFILE=$SERVICE_DIR/testdaemon.pid
LOGFILE=$SERVICE_DIR/testdaemon.log
# DAEMON_OPTS="--pidfile=$PIDFILE --logfile=$LOGFILE twistedplugin"
**DAEMON_OPTS="-r&"nn**
.......

```

That looks suspicious.

---

### Post by prodigy_ on 2010-04-17
Running your code doesn't give me any syntax errors. What was the command you used to call the script?

---

### Post by touchring on 2010-04-18
> **prodigy_ said:**
> Running your code doesn't give me any syntax errors. What was the command you used to call the script?


I used 'bash /etc/init.d/inittestdaemon'

Later, i tried 'bash /etc/init.d/inittestdaemon', it returned /bin/sh^M: bad interpreter: No such file.....

On Googling, I realized that the problem was that I created the inittestdaemon file on Windows (using notepad).

I used dos2unix to fix the file, so the problem is solved for now.  Thanks to all for your help.  :)

---

