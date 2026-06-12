---
title: "Record from USB device"
date: 2009-08-30
forum: General Help
---

### Post by Shugs81 on 2009-08-30
Hmmmm.... tried to post this in Multimedia but apparently don't have permissions.... anyhow...

Trying to connect a sub device up to Jack to use ardour or something similar to record with...

at first i hadn't realized that i had the realtime kernal ticked... props for that! lol... then i realised i hadn't selected the usb device itself... but past that I'm stuck

in the settings I've got usb on HW:1,0.

I've got nothing connected in connections as only have 14:midi through on both sides, obviously ardour comes up when it's running

getting the following error codes:

```
12:21:51.830 Startup script...
12:21:51.831 artsshell -q terminate
sh: artsshell: not found
12:21:52.239 Startup script terminated with exit status=32512.
12:21:52.240 JACK is starting...
12:21:52.241 /usr/bin/jackd -R -dalsa -dhw:1,0 -r44100 -p1024 -n2 -C
12:21:52.250 JACK was started with PID=7795.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1563601168, from thread -1563601168] (1: Operation not permitted)
cannot create engine
12:21:52.287 JACK was stopped successfully.
12:21:52.288 Post-shutdown script...
12:21:52.289 killall jackd
jackd: no process killed
12:21:52.710 Post-shutdown script terminated with exit status=256.
12:21:54.377 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

any ideas on how i can get it to show in the connections panel too?

is there a Jack forum? I'm using Qtjack... or whatever it's called...

HELP!!!

---

