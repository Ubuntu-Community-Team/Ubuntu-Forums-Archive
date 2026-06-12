---
title: "update-rc.d clarification"
date: 2010-06-11
forum: General Help
---

### Post by matthew.parlette on 2010-06-11
I've searched a while for this, but can't seem to find the answer to what I am looking for in particular.

So I am setting up my ubuntu server with some startup scripts using update-rc.d, what I'm wondering is, how does the symlinks in rc#.d know what to call on the script?

For example, I have a misterhouse startup script which takes parameters of start, stop, and restart:

```
#/etc/init.d/mh
# This script starts and stops the MisterHouse service

# Misterhouse PID file
PID=/usr/bin/mh/data/matt/mh.pid

# Call the shell script to actually start the program
DAEMON=/home/matt/Dropbox/Documents/Projects/mh/mh.sh

start(){
        echo "Starting MisterHouse"
        start-stop-daemon --start --background --quiet --chuid mh --exec $DAEMON
        echo ""
}

stop(){
        echo "Stopping MisterHouse"
        start-stop-daemon --stop --quiet --pidfile $PID
}

case "$1" in
start)
        start
        ;;
stop)
        stop
        ;;
restart)
        stop
        sleep 5
        start
        ;;
*)
        echo "Usage: /etc/init.d/mh {start|stop|restart}"
        exit 1
        ;;
esac
exit 0
```

Now, when I run update-rc.d mh defaults, it adds the S20mh to the proper runlevels and K20mh to the others. How does it know to run /etc/init.d/mh start or stop? Is it based off of the S or K? If its S, it runs the symlink'd script with start, and a K runs it with stop?

I've tried to find the answer to this with no luck yet, so any information you have to help me understand this better would be fantastic.

---

### Post by gzarkadas on 2010-06-11
Yes, the S in the link name signals to start the service (script is called with start argument), the K signals to stop (script is called with stop argument) the service at that runlevel. The number following defines the order (00 - 99) to run the scripts. In general, you should set K-order = 100 - S-order. Use `man update-rc.d' to learn more of the fine details.

---

### Post by matthew.parlette on 2010-06-14
Thanks a ton for that description. I had it all pretty well down, but I couldn't find out for sure if S called start and K called stop, or if there was some other magic script that I didn't know about yet :)

Thanks for helping me out, though.

---

