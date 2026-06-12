---
title: "running program as a daemon"
date: 2011-04-10
forum: General Help
---

### Post by ole123 on 2011-04-10
Hello,
i am trying to daemonize my (java) program on ubuntu.
For that end i created a script based on /etc/init.d/skeleton script which obviously uses start-stop-daemon.

But I cannot make the process (java program) run on the background. it keeps running in the same terminal i start my daemon script. Trying --background option for start-stop-daemon does not help.
Any ideas what is missing here?

thanx alot

---

### Post by d3v1150m471c on 2011-04-10
can i take a look at the daemon itself? if it needs to run in the background you'll want to launch it outside of a terminal. IE adding it to startup or launching via alt+f2.

---

### Post by ole123 on 2011-04-10
you mean the code?
essentially it is this:

# PATH should only include /usr/* if it runs after the mountnfs.sh script
PATH=/sbin:/usr/sbin:/bin:/usr/bin
DESC="Description of the service"
NAME="clientnode"
DAEMON=/usr/bin/java
DAEMON_ARGS="-cp $CLASSPATH MainClientNode"
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/clientnode

# Exit if the package is not installed
[ -x "$DAEMON" ] || exit 0

start-stop-daemon --start --pidfile $PIDFILE --exec $DAEMON -- $DAEMON_ARGS -b


the problem is that i have to run this service (daemon) on servers which i can only access remotely via telnet.  what is this alt+f2 option?
Adding it to startup is not good either 'cause i need to start/stop it occasionally.

---

### Post by ole123 on 2011-04-10
actually i can add it to startup and then use start and stop functions, right?

---

### Post by d3v1150m471c on 2011-04-10
alt+f2 is a gnome-launcher, but that assumes you're using gnome. you should add it to startup but throw in some conditionals as to when and why it would startup and shutdown IMO. What criteria should cause the daemon to start and stop. I might be able to point you in the right direction. 

edit:
You probably already know this but you can background it by running the command following by &
```

echo something &

```
Although, when the terminal closes it will probably kill it.

---

### Post by ole123 on 2011-04-10
What file in ubuntu is responsible for runlevels? there is no /etc/inittab. there is no /etc/event.d/rc-default either ...

thnx

---

