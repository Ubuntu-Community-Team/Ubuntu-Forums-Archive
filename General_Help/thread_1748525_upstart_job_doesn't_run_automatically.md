---
title: "upstart job doesn't run automatically"
date: 2011-05-03
forum: General Help
---

### Post by ygoe on 2011-05-03
Hi,

I have just created my first upstart job for my own daemon application. I can start and stop the job manually and view its status. But it doesn't start with the system, although other jobs with the same configuration do start. Where's the bug?

Here is my job config file: (/etc/init/logstate.conf)

[INDENT]description "LogState logging daemon"

start on started mysql
stop on stopping mysql

respawn
chdir /usr/webadmin/logstate
exec /usr/webadmin/logstate/LogState.exe -d
[/INDENT]

---

### Post by sisco311 on 2011-05-03
My guess is that the -d flag causes LogState.exe to run as a daemon. If this is the case, then either omit it or use an **expect daemon** stanza.

See:
[http://upstart.ubuntu.com/cookbook/#expect](http://upstart.ubuntu.com/cookbook/#expect)

---

### Post by ygoe on 2011-05-03
No, it's for debug logging. The LogState process doesn't fork, daemonise or anything, it's a normal .NET console application that runs forever and only quits on SIGINT or SIGTERM.

---

### Post by sisco311 on 2011-05-03
What's the point of the **chdir** line? I can't find any reference to it in the upstart documentation.

Do you have to change the current working directory to /usr/webadmin/logstate?
```
 description "LogState logging daemon"

 start on started mysql
 stop on stopping mysql

 respawn

 script
   cd /usr/webadmin/logstate
   ./LogState.exe -d
 end script
```

---

### Post by ygoe on 2011-05-04
You can't find it? Google did. :-)

[http://upstart.ubuntu.com/wiki/Stanzas](http://upstart.ubuntu.com/wiki/Stanzas)

---

### Post by ygoe on 2011-07-17
I changed my job and it still doesn't even seem to be regarded at boot time, but I can still start, stop and status it interactively.

```
description "LogState logging daemon"

#start on started mysql
start on filesystem
#stop on stopping mysql
stop on runlevel[!2345]

respawn
#chdir /usr/webadmin/logstate
#exec /usr/webadmin/logstate/LogState.exe -d

script
    logger BEFORE starting LogState
    update-binfmts --display | logger
    /usr/webadmin/logstate/LogState.exe -d
    logger AFTER returning from LogState
end script

```

There's no message in syslog regarding this script, its execution or its contents.

I thought that maybe mono-cli wasn't registered yet when the script should run, but even the logger call wasn't visible in the syslog.

Next stop is upstart debugging (see [my other thread about how to accomplish that with grub]("http://ubuntuforums.org/showthread.php?p=11056119").)

---

### Post by ygoe on 2011-07-20
Well, here's the simple answer: The mono binfmt entry isn't enabled yet at the time when the application is to be started. I have to change my programme call from:

exec /usr/webadmin/logstate/LogState.exe -d

to:

exec /usr/bin/mono /usr/webadmin/logstate/LogState.exe -d

And then it works. :)

---

