---
title: "JACK Audio Problems"
date: 2011-12-22
forum: General Help
---

### Post by Musick Man on 2011-12-22
Hi, 

I just installed Ubuntu Studio and I am testing out audio programs. One of them that I wanted to try was Internet DJ Console and it required JACK Audio server. So I installed it and it made all of my sound not work. I did a little research on how to get it set up and when I go to run the server I get this error message. 

```
16:22:43.067 JACK is starting...
16:22:43.068 /usr/bin/jackd -r -dalsa -dhw:0 -r44100 -p256 -n2 -m
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:22:43.192 JACK was started with PID=6975.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in non-realtime mode
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|256|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
Using ALSA driver ICH4 running on card 0 - Intel 82801DB-ICH4 with ALC658D at irq 17
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
16:22:43.835 JACK was stopped with exit status=255.
16:22:45.290 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
```

Im stuck here and no sound works at all. For anything. 

Any ideas on whats going on? 

Thanks!!

---

