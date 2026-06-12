---
title: "Noob wants to set up jack"
date: 2010-08-04
forum: General Help
---

### Post by mr. poopy pants on 2010-08-04
im running 10.04 desktop amd 64. First of all, is this the correct version i should be using on a intel i3 machine? it seems to run great!

Ive been trying to set up jack. I havnt done anything but download q controll and im not sure what i need to do to set it up. eventually i want to run aurdor.

Please keep in mind that im new to linux but i want to learn how to make it work under the hood. thanks for any help!

 p, li { white-space: pre-wrap; }  [COLOR=#999999]11:40:47.562 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]11:40:47.627 Statistics reset.[/COLOR]
 [COLOR=#66cc99]11:40:47.772 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]11:40:47.923 ALSA connection change.[/COLOR]
 [COLOR=#999999]11:40:51.252 Startup script...[/COLOR]
 [COLOR=#990099]11:40:51.252 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]11:40:51.655 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]11:40:51.655 JACK is starting...[/COLOR]
 [COLOR=#990099]11:40:51.655 /usr/bin/jackd -dalsa -dhw:0 -r48000 -p1024 -n2[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
 [COLOR=#999999]11:40:51.658 JACK was started with PID=1764.[/COLOR]
 Please check your /etc/security/limits.conf for the following lines
 and correct/add them:
   @audio          -       rtprio          100
   @audio          -       nice            -10
 After applying these changes, please re-login in order for them to take effect.
 You don't appear to have a sane system configuration. It is very likely that you
 encounter xruns. Please apply all the above mentioned changes and start jack again!
 [COLOR=#999999]11:40:51.689 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]11:40:51.689 Post-shutdown script...[/COLOR]
 [COLOR=#990099]11:40:51.690 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]11:40:52.105 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]11:40:53.828 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

---

### Post by mr. poopy pants on 2010-08-04
un checked real time audio, jack will start now. now i need to set up real time audio for low latency right?

---

