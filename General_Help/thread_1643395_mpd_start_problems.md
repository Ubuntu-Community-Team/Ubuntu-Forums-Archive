---
title: "mpd start problems"
date: 2010-12-11
forum: General Help
---

### Post by Neon612 on 2010-12-11
I don't have mpd set to start up on log in, session start, whatever its called... But when i try to start mpd I get:
```
listen: Failed to listen on *:6600: Address already in use
Aborted
```

I have to run:
```
sudo /etc/init.d/mpd stop
```

before I can start it up again.

Is there anyway to get mpd to start up right the first time, maybe even at startup?

Thanks.

---

### Post by Brandon Williams on 2010-12-13
You've got two different high-level options: run mpd as a system-level service or run mpd as a user. I do both ... it runs as a service on my primary music server and it runs as a user on my other machines.

On the machine where I run it as a system-level service, /etc/default/mpd contains the following settings:```
START_MPD=true
MPDCONF=/etc/mpd.conf
``` In this case, /etc/mpd.conf contains the configuration.

On the machines where I run it as a regular user, /etc/default/mpd contains the following setting:```
START_MPD=false
``` In this case, I put my config in ~/.mpd.conf and I autostart mpd with the following script:```
#!/bin/sh

if ! ps -C mpd > /dev/null
then
    exec mpd $HOME/.mpd.conf
fi
``` This script will only start mpd if it isn't already running.

---

