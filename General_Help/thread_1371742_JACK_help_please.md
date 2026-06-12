---
title: "JACK help please"
date: 2010-01-03
forum: General Help
---

### Post by trooster89 on 2010-01-03
I recently installed JACK because I'd like to use it with Ardour; however, I cannot seem to get it working properly. Any time I open it, I get errors. 

here is what the QjackCtl message displays:

 p, li { white-space: pre-wrap; }  [COLOR=#999999]17:44:27.158 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]17:44:27.234 Statistics reset.[/COLOR]
 [COLOR=#999999]17:44:27.263 Startup script...[/COLOR]
 [COLOR=#990099]17:44:27.264 artsshell -q terminate[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66CC99]17:44:27.270 ALSA connection graph change.[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]17:44:27.761 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]17:44:27.761 JACK is starting...[/COLOR]
 [COLOR=#990099]17:44:27.762 /usr/bin/jackd -R -p128 -t5000 -dalsa -dhw:0 -r48000 -p64 -n2 -S[/COLOR]
 [COLOR=#999999]17:44:27.764 JACK was started with PID=18070.[/COLOR]
 /usr/bin/jackd: symbol lookup error: /usr/bin/jackd: undefined symbol: clock_source
 [COLOR=#999999]17:44:27.807 JACK was stopped with exit status=127.[/COLOR]
 [COLOR=#999999]17:44:27.808 Post-shutdown script...[/COLOR]
 [COLOR=#990099]17:44:27.808 killall jackd[/COLOR]
 [COLOR=#FF0000]17:44:27.965 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#CCCC99]17:44:30.598 ALSA connection change.[/COLOR]
 jackd: no process found
 [COLOR=#999999]17:44:30.817 Post-shutdown script terminated with exit status=256.[/COLOR]

[COLOR=#999999][/COLOR]

[COLOR=#999999][/COLOR]
Any help would be much appreciated. 
[COLOR=#999999][/COLOR]

[COLOR=#999999][/COLOR]

---

### Post by a_flj_ on 2010-01-17
I have exactly the same problem. Could somebody please help us?

---

### Post by patchwork on 2010-01-17
Before you start JACK control (qjackctl) you need to start the jack daemon.  First, make sure jackd is installed:    sudo apt-get install jackd  Next, before starting JACK control, start jackd in the terminal with a specified backend (In my case I use ALSA)  jackd -d alsa   More help using the jackd command can be found using   jackd -h

---

### Post by trooster89 on 2010-04-19
sorry for the belated thanks.
running jackd -d alsa worked just fine.

---

