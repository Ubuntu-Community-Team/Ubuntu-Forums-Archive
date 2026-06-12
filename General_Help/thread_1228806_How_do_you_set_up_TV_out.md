---
title: "How do you set up TV out?"
date: 2009-08-01
forum: General Help
---

### Post by benhall on 2009-08-01
This is not a technical question, but I'm interested in how people set up their monitors/tv to watch movies sometimes and use a regular desktop other times. I have recently set up my own monitor/tv with nvidia twinview, but have discovered that I can't quite clone the screens as my native monitor resolution is too high for my (standard definition) TV (1280x1024 vs an apparent maximum of 1024x768). This is frustrating as though some programs work out appropriately how to do fullscreen resolution (mplayer), the BBC iplayer doesn't and neither does totem. Do people run separate X servers to get around this, or is there a way of scaling the tv output appropriately, or another way? I have tried using as a neighbouring screen, but fullscreen movies still play preferably on the monitor screen.

Thanks

Ben

---

### Post by newbe12 on 2009-10-12
I just set up twin view also. I did not care what resulution it was at all I use it only for playing movies. I made a script for mplayer and put it in  /usr/local/bin.

[B]#!/bin/sh
export DISPLAY=:0.1
/usr/bin/mplayer -fs -zoom "$*"[/B] 

Open notepad copy text above and save it as **mplayer.tv** and make it a script

---

