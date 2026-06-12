---
title: "Auto restarting daemon"
date: 2009-11-09
forum: General Help
---

### Post by uthfull on 2009-11-09
I am trying to setup an SMS gateway using GAMMU. I have my phone and SMSD (sms daemon) configured properly. However, I wanted a way to autostart the daemon each time it stops. I searched around and found the following :

I created a script at /usr/local/bin/**smsd.sh** with the following content :
```
#!/bin/sh
export LANG=en_US
/usr/bin/gammu-smsd -d
```

Next, I created a file in /etc/init for upstart and named it as **smsd.conf** with the following content :

```
# smsd
#
# This service maintains the SMS Daemon from the point the system is
# started until it is shut down again.

description	"SMSD daemon"

start on runlevel 3
start on runlevel 4
start on runlevel 5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 2
stop on runlevel 6

respawn
exec /usr/local/bin/smsd.sh 
```

I tried starting SMS daemon via the command **sudo /sbin/initctl start smsd** but got the error :
initctl: Job failed to start

**sudo /sbin/initctl status smsd** gives me :
smsd stop/waiting

What am I doing wrong here? I need the daemon to run always so that it can grab messages off my connected phone at all times. Any help would be great at this point.

**UPDATE:**
I've updated the smsd.conf as follows :
```
# smsd
#
# This service maintains the SMS Daemon from the point the system is
# started until it is shut down again.

description	"SMSD daemon"

start on runlevel [345]

stop on runlevel [0126]

respawn
exec "/usr/local/bin/smsd.sh"
```

**sudo /sbin/initctl start smsd** now gives me :
smsd start/running, process 2870

This means it executes the script and starts the daemon. Now, immediately when I run **sudo /sbin/initctl status smsd**, I get :
smsd stop/waiting

I'm confused!

---

### Post by sisco311 on 2009-11-09
The default runlevel in Ubuntu is 2, you probably don't want to stop your daemon on runlevel 2 ;)

```
# smsd
#
# This service maintains the SMS Daemon from the point the system is
# started until it is shut down again.

description	"SMSD daemon"

start on runlevel [**2**345]

stop on runlevel [016]

respawn
exec "/usr/local/bin/smsd.sh"
```

---

### Post by uthfull on 2009-11-09
I tried what you said and changed the runlevels accordingly and started the daemon but when I check the status it still gives me stop/waiting.

---

### Post by sisco311 on 2009-11-09
remove the quotes and add *console output* to redirect the output of your script to /dev/console:
```
# smsd
#
# This service maintains the SMS Daemon from the point the system is
# started until it is shut down again.

description	"SMSD daemon"

start on runlevel [2345]

stop on runlevel [016]

respawn
exec /usr/local/bin/smsd.sh
console output
```

---

### Post by uthfull on 2009-11-09
As soon as I remove the quotes, I get [B]nitctl: Job failed to start
[/B]. If I put them back along with console output, I still get just **smsd start/running, process 2739** and when I check the status it comes back as stop/waiting. Baffles me!

---

### Post by sisco311 on 2009-11-09
remove the -d flag from your script
```
#!/bin/sh
export LANG=en_US
/usr/bin/gammu-smsd
```

or even better use the script stanza:
```
# smsd
#
# This service maintains the SMS Daemon from the point the system is
# started until it is shut down again.

description	"SMSD daemon"

start on runlevel [2345]

stop on runlevel [016]

respawn

script
  export LANG=en_US
  /usr/bin/gammu-smsd
end script
```

---

### Post by uthfull on 2009-11-09
Some progress!! Removing "-d" flag does indeed keep the process running after it starts. But from the documentation of my script, I need to use to "-d" switch to daemonize the process. Any inputs here?

---

### Post by sisco311 on 2009-11-09
> **uthfull said:**
> Some progress!! Removing "-d" flag does indeed keep the process running after it starts. But from the documentation of my script, I need to use to "-d" switch to daemonize the process. Any inputs here?

deamonize means to run it in the background, that's exactly what upstart does.

check if  gammu-smsd is working.

---

### Post by uthfull on 2009-11-09
Oops! Sorry for being kinda stupid there! Thanks for all the help. You're a lifesaver. I guess the problem is sort of resolved here. Now that the process runs in the background, my work will be easier. Thanks again!

---

### Post by tedymut on 2010-10-05
> **sisco311 said:**
> remove the -d flag from your script
```
#!/bin/sh
export LANG=en_US
/usr/bin/gammu-smsd
```or even better use the script stanza:
```
# smsd
#
# This service maintains the SMS Daemon from the point the system is
# started until it is shut down again.

description    "SMSD daemon"

start on runlevel [2345]

stop on runlevel [016]

respawn

script
  export LANG=en_US
  /usr/bin/gammu-smsd
end script
```



i try but not work in my lucid :( , what wrong?

---

