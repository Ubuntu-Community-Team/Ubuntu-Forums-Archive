---
title: "My First Shell Script"
date: 2010-07-19
forum: General Help
---

### Post by Simon_Haddad on 2010-07-19
O.K., so I wrote this script (below, "AutoHotSwapExternalMonitor.sh") to automatically enable a second monitor for my laptop whenever I plug one in.  As you can probably deduce from the xrandr settings, it's a really old CRT (the gamma settings) attached to a netbook (the resolution).  If I run the custom xrandr command manually, here are the possible outcomes.

[LIST]
[*][*]If compiz is running, I unplug the VGA cable and then I run the xrandr command compiz keeps running and the desktop constrains to one screen.
[*][*]If compiz is running, I keep the VGA cable as is (plugged or unplugged) and then I run the xrandr command compiz keeps running and the desktop remains the same.
[*][*]If compiz is running, I plug in the VGA cable and then I run the xrandr command compiz crashes and metacity takes over.
[*][*]If metacity is running, I have no problems with crashes.
[/LIST]

The script below checks if compiz should be running, runs the xrandr command and then restarts compiz if it should be running but crashed.  I've set up this script to run at logon and at calls itself again every three seconds after that.



```
#!/bin/bash

#find the current state of compiz

statebefore=`pgrep compiz`

#try the second monitor with my preferred settings

xrandr --output VGA1 --mode 800x600 --rate 60.3 --gamma .4:.4:.3

#if compiz was on, check if it's still on

if [ "$statebefore" != "" ]; then
#compiz was on

	#pause in case compiz needs more time to finish crashing (avoiding a false negative result)
	sleep 3

	#check if compiz has crashed
	stateafter=`pgrep compiz`

	if [ "$stateafter" = "" ]; then
	#compiz has crashed, restart it

	compiz
	fi

fi

#pause before running the script again

sleep 3
AutoHotSwapExternalMonitor.sh
```


It seems to work for the most part, but if I intentionally switch to metacity using, say, "Compiz Fusion Icon", there's a 50-50 chance that I've switched during the first three second "sleep" in the script.  The script interprets this as a crash and restarts compiz.

Does anyone know any easier way of doing this?  Barring that, maybe some suggestions for my 50-50 problem? I can't be the only one who wants to hot-swap a VGA cable.

---

