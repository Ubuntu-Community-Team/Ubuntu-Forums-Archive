---
title: "ssh: Could not resolve hostname restart: Name or service not known"
date: 2009-11-14
forum: General Help
---

### Post by getmizanur on 2009-11-14
elloo,

i've changed the configuration of something and my ssh does not restart. i get the following message:

ssh: Could not resolve hostname restart: Name or service not known

can it be the host.conf file where i have this single line
```

multi on

```

can somebody help. thanks in advance.

---

### Post by Brandon Williams on 2009-11-14
My host.conf also has this line:
```
order hosts,bind
```

But a comment in the file indicates that this line should not be necessary with newer libc implementations, so that's probably not the issue.

The error output that you quote looks like the result of 'restart' not being a resolvable hostname when you run:
```
ssh restart
```

Is this the command that you're trying to run to restart ssh? It should be:
```
sudo service ssh restart
```

---

### Post by getmizanur on 2009-11-15
I've tried changing host.conf to your settings and try to restart ssh however it did not work.

to restart ssh i use
```

sudo ssh restart

```

i've tried
```

sudo service ssh restart

```

however i get the following message
```

ssh: Could not resolve hostname restart: Name or service not known

```

thanks for the reply, any other ideas

---

### Post by Iowan on 2009-11-15
**service** is new to Karmic, but I found [this]("http://www.manpagez.com/man/8/service/") page. Notice the line:>  Currently, the available commands are 'start' and 'stop'.
Apparently, this still works:```
sudo /etc/init.d/networking restart
```

---

### Post by Brandon Williams on 2009-11-15
The service command is not new to karmic, it's part of the upstart system, which has been in use for at least one or two prior releases. Most of the old SysV5 init scripts have been converted to upstart jobs, and it's best to use the service command instead of running scripts out of /etc/init.d directly.

The specific commands supported (start, stop, restart, etc.) are service specific, but ssh supports restart.

The command to restart ssh with service is:
```
sudo service ssh restart
```
as I noted before.

If this is not working, please post the output from running the command. I don't see any case where running this command would result in the system attempting to resolve 'restart' as if it were a hostname.

Attempting to restart ssh with the commabnd 'ssh restart' will definitely not work, and will definitely result in the error message that you indicate.

---

### Post by Iowan on 2009-11-15
I must have misread the thread (or OP was mistaken) about **service** being new to Karmic. I found info via **man service** on my Jaunty laptop.

---

### Post by dcstar on 2009-11-15
> **getmizanur said:**
> I've tried changing host.conf to your settings and try to restart ssh however it did not work.

**to restart ssh i use**
```

sudo ssh restart

```
.......

Why?, **ssh** is a client program that you are trying to connect to host "restart".
```

man ssh
```

---

