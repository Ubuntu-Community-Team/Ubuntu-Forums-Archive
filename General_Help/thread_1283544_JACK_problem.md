---
title: "JACK problem"
date: 2009-10-05
forum: General Help
---

### Post by MegaCoolishMan on 2009-10-05
Hello!

I'm having some problems with my JACK thingy. I just want to be able to make music :guitar: and don't have to learn the entire system to figure out a solution, so thats why I'm asking to you:).

My problem is that: I started JACK and pressed Start. A error pops up saying:
"  p, li { white-space: pre-wrap; }Could not connect to JACK server as client. - Overall operation failed.
 - Unable to connect to server.
 Please check the messages window for more info."


And in the messages box it stands:


p, li { white-space: pre-wrap; }And 
[COLOR=#999999]22:31:26.183 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]22:31:26.358 Statistics reset.[/COLOR]
 [COLOR=#66cc99]22:31:26.367 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]22:31:26.569 ALSA connection change.[/COLOR]
 [COLOR=#999999]22:31:29.874 Startup script...[/COLOR]
 [COLOR=#990099]22:31:29.874 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]22:31:30.275 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]22:31:30.275 JACK is starting...[/COLOR]
 [COLOR=#990099]22:31:30.275 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n3[/COLOR]
 [COLOR=#999999]22:31:30.279 JACK was started with PID=15205.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot use real-time scheduling (FIFO at priority 10) [for thread -1211345216, from thread -1211345216] (1: Operation not permitted)
 cannot create engine
 [COLOR=#999999]22:31:30.310 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]22:31:30.310 Post-shutdown script...[/COLOR]
 [COLOR=#990099]22:31:30.311 killall jackd[/COLOR]
 jackd: ingen process avslutad (no process terminated (my translation:)))
 [COLOR=#999999]22:31:30.718 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]22:31:32.374 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
[COLOR=#ff0000][COLOR=Black]
[/COLOR][/COLOR]
[COLOR=#ff0000][COLOR=Black]
[/COLOR][/COLOR]
If you need more information, just ask, because I don't really know how much is needed.


Thanks in advance:P

---

### Post by MegaCoolishMan on 2009-10-05
I turned of the realtime (which is strange because I should have a "really:)" good card) and now I have this error:


p, li { white-space: pre-wrap; }  [COLOR=#999999]22:40:04.039 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]22:40:04.213 Statistics reset.[/COLOR]
 [COLOR=#66CC99]22:40:04.222 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]22:40:04.419 ALSA connection change.[/COLOR]
 [COLOR=#999999]22:40:19.922 Startup script...[/COLOR]
 [COLOR=#990099]22:40:19.923 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]22:40:20.324 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]22:40:20.324 JACK is starting...[/COLOR]
 [COLOR=#990099]22:40:20.324 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n3[/COLOR]
 [COLOR=#999999]22:40:20.326 JACK was started with PID=15601.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 44100
 creating alsa driver ... hw:0|hw:0|1024|3|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: use 3 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: got smaller periods 2 than 3 for playback
 ALSA: cannot configure playback channel
 cannot load driver module alsa
 [COLOR=#999999]22:40:20.362 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]22:40:20.363 Post-shutdown script...[/COLOR]
 [COLOR=#990099]22:40:20.363 killall jackd[/COLOR]
 jackd: ingen process avslutad
 [COLOR=#999999]22:40:20.769 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]22:40:22.401 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

---

### Post by HyperFlexed on 2010-04-28
edit:

solved my problem by following this guide:
[http://alsa.opensrc.org/index.php/Quick_Install](http://alsa.opensrc.org/index.php/Quick_Install)

Why that can't be done by the Ubuntu default install is beyond me.

---

