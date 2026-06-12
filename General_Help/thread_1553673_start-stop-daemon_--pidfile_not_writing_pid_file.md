---
title: "start-stop-daemon --pidfile not writing pid file"
date: 2010-08-15
forum: General Help
---

### Post by shwoodard on 2010-08-15
I have an init.d script to start stop nginx, etc.  It is the one from google code.  Start function works fine, but stop fails.  I can only assume this is because start does not write the pid.

```

start() {
        log_daemon_msg "Starting $DESCRIPTION"
	
	isRunning
	isAlive=$?
	
        if [ "${isAlive}" -eq $TRUE ]; then
                log_end_msg $SCRIPT_ERROR
        else
                start-stop-daemon --start --quiet --chuid $RUNAS --pidfile $PIDSPATH/$PIDFILE --exec $DAEMON
                setFilePerms
		log_end_msg $SCRIPT_OK
        fi
}

```

```

stop() {
	log_daemon_msg "Stopping $DESCRIPTION"
	
	isRunning
	isAlive=$?
        if [ "${isAlive}" -eq $TRUE ]; then
                start-stop-daemon --stop --quiet --pidfile $PIDSPATH/$PIDFILE

		removePIDFile

                log_end_msg $SCRIPT_OK
        else
                log_end_msg $SCRIPT_ERROR
        fi
}

```

Source: [http://code.google.com/p/nginx-init-ubuntu/](http://code.google.com/p/nginx-init-ubuntu/).

Anyone have any thoughts on what might be going on here?

Thanks,
Sam

---

### Post by topler on 2011-01-24
I had the same issue and eventually noticed that the parameter "--make-pidfile" needs to be included. Please see the "start-stop-daemon" documentation for more details.

[http://manpages.ubuntu.com/manpages/maverick/man8/start-stop-daemon.8.html](http://manpages.ubuntu.com/manpages/maverick/man8/start-stop-daemon.8.html)

However, in my case it didn't really work as it saved the wrong process ID. If the process ID was for example 4812 it would have saved the number 4811. As of the documentation, this can happen if the process forks from its main process.

Since my script was supposed to start and stop the process only I ended up doing the following.

```
  start)
    log_daemon_msg "Starting scanner daemon Canon imageFORMULA P-150 High Speed Portable Document Scanner" "scannerd"
    if start-stop-daemon --start --quiet --oknodo --pidfile /var/run/scannerd.pid --exec /usr/sbin/scannerd; then
            cat /dev/null > /var/run/scannerd.pid
            pidof scannerd >> /var/run/scannerd.pid
        log_end_msg 0
    else
        log_end_msg 1
    fi
    ;;
```

---

