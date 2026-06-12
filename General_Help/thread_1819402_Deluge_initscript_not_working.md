---
title: "Deluge initscript not working"
date: 2011-08-06
forum: General Help
---

### Post by nickeh on 2011-08-06
Hi, I've been running deluged from an init script for a while. It has been working great until I decided to do a distupgrade yeaster day. 

I use the scripts from deluges homepage. 

```

# Configuration for /etc/init.d/deluge-daemon
# The init.d script will only run if this variable non-empty.
DELUGED_USER="deluge"
# Should we run at startup?
RUN_AT_STARTUP="YES"

```

[http://pastebin.com/EEWWwdtW](http://pastebin.com/EEWWwdtW)

The only things I've changed is the options sent to the daemon. 

But when i boot the script doesn't start deluged. 

When i try to start deluged via service command i get no response...

```

nicke@egendomlig:~$ sudo service deluge-daemon start
[sudo] password for nicke: 
nicke@egendomlig:~$

```

And deluged isn't running. 

```

-rwxr-xr-x 1 root root 4377 2011-03-26 23:59 /etc/init.d/deluge-daemon

```

The init script is executable.

And if i take the parameters from the initscript and run it, it starts.

```

nicke@egendomlig:~$ sudo deluged -d -c /home/deluge -l /var/log/deluged.log -L warning

```

So what i think could be the problem is that i try to run the daemon as deluge user, but that user shouldn't have been changed due to the upgrade right?

Any help on where to look fore some output on what's happening when i try to run the service would be great!



EDIT: Solved it, seems the problem was that i ran ubuntu 1.3.3 from ubuntu ppa. After removing the ppa and reinstalling 1.3.1 it works as a charm.

---

