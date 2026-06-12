---
title: "Problems getting Jack server to start"
date: 2011-11-09
forum: General Help
---

### Post by HuaiDan on 2011-11-09
Hello,
I'm trying to connect a Digitech effects processor, which I had done successfully in 10.04. Now that I'm in 11.04, I've been through sevral how-to's , each resolving one error or other that had been preventing me getting Jack started correctly. 
I've solved the real-time memory problem, added user to audio group, installed pulseaudio plugin, have the digitech USB enabled in sound settings.
To the best of my knowledge, I have it set up the same way in 10.04, but in  10.04 it will start, in 11.04 it crashes.

> 17:40:09.050 Patchbay deactivated.
17:40:09.057 Statistics reset.
17:40:09.067 ALSA connection change.
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
17:40:09.147 ALSA connection graph change.
17:40:18.785 JACK is starting...
17:40:18.785 /usr/bin/jackd -S -t5000 -u -dalsa -dhw:1 -r44100 -p128 -n3 -H -D -Phw:0
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
17:40:18.815 JACK was started with PID=27280.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
control device hw:1
control device hw:0
audio_reservation_init
Acquire audio card Audio1
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:1|128|3|44100|0|0|hwmon|swmeter|-|32bit
control device hw:0
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xf6000000 irq 45
configuring for 44100Hz, period = 128 frames (2.9 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 3 periods for playback
17:40:25.911 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.
17:40:25.948 JACK is stopping...
JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
Driver is not running
Cannot create new client
JackSocketClientChannel read fail
Cannot open qjackctl client
jackd: ../common/JackGraphManager.cpp:45: void Jack::JackGraphManager::AssertPort(jack_port_id_t): Assertion `port_index < fPortMax' failed.
17:40:26.001 JACK was stopped successfully.
17:40:26.014 JACK has crashed.

Looks like everything's running smoothly until "Could not connect to JACK server as client."



Any ideas / suggestions?

Thanks!


11.04 AMD64 build

---

### Post by HuaiDan on 2011-11-10
Bump

---

### Post by HuaiDan on 2011-11-13
Bump

---

### Post by HuaiDan on 2011-11-14
Bump

---

### Post by HuaiDan on 2011-12-10
Still an issue...

---

### Post by jalor@yousee.dk on 2012-04-08
Hi

Have that exact same problem, Ubuntu Studio 11.10 using realtime kernel. Like you I am trying to use different cards for capture and playback. 

If I use the same card for capture and playback jack starts fine. As soon as I use different cards for playback and capture Jack cannot start and I get the error message you describe.

Jack 0.3.8

It works using hw:0 for capture and playback:
------------------------------------------------
JACK server starting in realtime mode with priority 10
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|64|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 64 frames (1.5 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 3 periods for playback
12:54:47.185 JACK connection change.
12:54:47.186 Server configuration saved to "/home/jablo/.jackdrc".
12:54:47.187 Statistics reset.
12:54:47.192 Client activated.
12:54:47.196 JACK connection graph change.

I get an error when using hw:3 for capture and hw:0 for playback
--------------------------------------------------------------------
JACK server starting in realtime mode with priority 10
control device hw:3
control device hw:0
audio_reservation_init
Acquire audio card Audio3
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:3|64|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 64 frames (1.5 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 3 periods for playback
12:55:50.443 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.
JackProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
Driver is not running
JackSocketClientChannel read fail
Cannot create new client
Cannot open qjackctl client
Unknown request 4294967295
jackd: ../common/JackGraphManager.cpp:45: void Jack::JackGraphManager::AssertPort(jack_port_id_t): Assertion `port_index < fPortMax' failed.
12:55:50.480 JACK was stopped successfully.
12:55:50.481 JACK has crashed.

--- update
I can start jackd directly on the command line using:
/usr/bin/jackd -p128 -dalsa -r44100 -p64 -n3 -D -Chw:3 -Phw:0

then I get the error message when the first client connects to jack

--- update;solved
It works if I set the frames/period to 256 or more, so it's probably something with the usb sound device not accepting the more aggressive setting.

---

