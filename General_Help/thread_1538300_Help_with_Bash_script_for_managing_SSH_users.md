---
title: "Help with Bash script for managing SSH users"
date: 2010-07-24
forum: General Help
---

### Post by ThatBum on 2010-07-24
Hey, I recently set up an SSH server here on my desktop so I can have a terminal and X forwarding and VNC through a tunnel and all that. I use key authentication, and I'm going to have a few people have keys that are in my authorized_keys file soon.

What I would like the script to do is show all the remote users currently logged in, their session's PID, and possibly some stuff from **w** like WHAT and FROM, and an option to kill the PID session by selecting a number corresponding to the user.

I found I can get SSH users' PIDs from **ps aux|grep sshd|grep pts**, which yields something like this:
```
justyn   28848  0.0  0.0  63236  1884 ?        S    18:48   0:00 sshd: justyn@pts/1
justyn   28863  0.0  0.0   3324   800 pts/0    S+   18:48   0:00 grep sshd
```If I run **w** I get this...```
 18:49:36 up  8:42,  3 users,  load average: 2.75, 3.12, 3.49
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
justyn   tty7     :0               11:16    8:42m 49:15   0.78s gnome-session
justyn   pts/0    :0.0             18:33    0.00s  0.01s  0.00s w
justyn   pts/1    192.168.1.102    18:48    1:23   0.00s  0.00s -bash

```...the SSH user obviously the one with the IP in the FROM field.

How would I go about making this script? Sorry, I'm fairly new at scripting.

Also, while I'm here, I seem to be having a problem with sshd's configuration. For the AuthorizedKeysFile value, it won't work if my authorized_keys is anywhere in /home. The only reason I can think of is that my /home is on a different drive than /. I have to put my auhorized_keys in /etc/ssh, which means it will work for any user, which isn't good. It doesn't matter if I use an absolute path (such as /home/justyn/.ssh/authorized_keys) or use a wildcard (%h/.ssh/authorized_keys or /home/%u/.ssh/authorized_keys).

Thank you for the help Ubuntunians!

---

### Post by ghostdog74 on 2010-07-24
Look at your /etc/ssh/sshd_config. There should be a logging section somewhere look like this
```

# Logging
# obsoletes QuietMode and FascistLogging
#SyslogFacility AUTH
SyslogFacility AUTHPRIV
#LogLevel INFO


```
you can make use of this to log your ssh sessions. check man sshd_config for more info.

---

### Post by ThatBum on 2010-07-24
> **ghostdog74 said:**
> log your ssh sessions

Where is the log file? The manpage doesn't seem to say.

**E:** Nevermind, I found it, it's /var/log/auth.log. Still want that script, though.

---

