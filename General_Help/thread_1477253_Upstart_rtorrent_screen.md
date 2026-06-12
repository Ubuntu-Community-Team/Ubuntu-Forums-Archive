---
title: "Upstart rtorrent screen"
date: 2010-05-08
forum: General Help
---

### Post by kempy1000 on 2010-05-08
Hi,

Im trying to start rtorrent in screen so it runs on boot in lucid. So far I have this in /etc/init. It runs fine at boot and starts perfectly.
The problem is it doesnt end cleanly so on next reboot the session file still exists and rtorrent wont reopen. I need to excecute
```

kill -2 `pidof rtorrent`

```
on shutdown how can I do this?

Also ```
 sudo service rtorrent stop 
``` gives:
```

stop: Unknown instance:

```

```

#rtorrent start

description     "Rtorrent Service"
author          "Chris"

respawn
console none

start on (local-filesystems and net-device-up IFACE=eth0)
stop on [!12345]

script
        su chris -c "screen -dms rtorrentdeamon /usr/local/bin/rtorrent"
end script

```

---

### Post by Saosin7 on 2010-05-12
I'm interested in this as well. Anyone?

---

### Post by cadriel on 2010-05-25
I would be interested in this too.

It would appear there's a post and pre stop event you could use to appropriately shutdown rTorrent - however, the stop event doesn't seem to work as the original poster pointed out.

What I'd love to see is;

1/
rTorrent start up during boot and;

2/
Have it start under my byobu setup.

--
Craig

---

### Post by Grenage on 2010-05-25
I have rtorrent and rssdler start at boot with dtach, I'll post my setup when I get home.

---

### Post by cadriel on 2010-05-25
After thinking about this a bit more;

Since I run byobu, wouldn't it make sense to setup rtorrent as a default window in byobu, and then make sure byobu runs at startup under my user?

They way it'd be running and ready to go by the time I login to my session anyway?

Thereby negating the need for an upstart script for rtorrent - and adding then need for a byobu one instead? :D

---

### Post by Grenage on 2010-05-26
```
@reboot TERM=xterm dtach -n ~/.rtorrent rtorrent
```

Works for me in *crontab -e*; never seems to get locked.

---

### Post by Augmented Insanity on 2010-10-05
```
description		"ncurses BitTorrent client based on LibTorrent"

console none
expect fork
kill timeout 30

start on (local-filesystems and net-device-up and runlevel [2345])
stop on runlevel [016]

exec su <USER> -c "screen -dms rtorrent /usr/local/bin/rtorrent"

pre-stop script
	exec kill `cat <ABSOLUTE_PATH_TO_RTORRENT_.LOCK> | awk -F: '{print($2)}' | sed "s/[^0-9]//g"`
end script
```

I cooked this up. It "Works For Me(TM)". 
I'm not sure whether this is right but I'm sure it can be improved upon. 
The init.d script found on rtorrents website wasn't cleanly shutting down rtorrent. So when it boots up again, rtorrent won't start up unless the sessions lock file is removed. So I'm gona see how this does.

The pre-stop command was part of the init.d script found on rtorrents website and uses the sessions lock file (which contains the PID) to cleanly shutdown rtorrent.

Upstarts documentation is non existent. The wiki is out of date and the only way to get a clue about what to do is to look at existing files in /etc/init and the upstart changelog. The pid option would have been very useful here but contrary to what the wiki says its been removed!

---

