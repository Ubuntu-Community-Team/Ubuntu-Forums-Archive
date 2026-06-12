---
title: "XWINWRAP at startup"
date: 2011-06-13
forum: General Help
---

### Post by dan1981football on 2011-06-13
Ubuntu noobie here.. Loving Linux though

Okies, i'm very slowly getting to grips with ubuntu.. mainly thanks to you guys..

I've installed XWINWRAP and now all i do is right click on desktop run the script choose the video i want and voila .. pretty moving picture

I would love to however have my animated background appear at start..

i've gone into startup manager and found the script file when i click browse however i still need to manually click on your videos then the video i want before it appears..

Is there a way for when ubuntu starts it can automatically choose run xwinwrap with a background or is it impossible..

If a custom script is needed pls can it be explained in the noobiest terms possible as like i mentioned before i'm still learning :)

Many thanks

Dan

---

### Post by overdrank on 2011-06-13
Hi and found some info on the commands [Here]("http://www.khattam.info/howto-video-wallpaper-on-ubuntu-10-04-lucid-lynx-2010-02-15.html"). :)

---

### Post by dan1981football on 2011-06-14
Hello and thankyou for the reply...

I managed to install it fine and i must say it looks pretty impressive..

I've managed to get startup to start the a-desk script where it asks you to select the video, however i cannot get it to autoplay a video..

Any ideas?

---

### Post by overdrank on 2011-06-14
> **dan1981football said:**
> Hello and thankyou for the reply...

I managed to install it fine and i must say it looks pretty impressive..

I've managed to get startup to start the a-desk script where it asks you to select the video, however i cannot get it to autoplay a video..

Any ideas?

The command given worked for me. 
```
xwinwrap -ni -o 0.9 -fs -s -st -sp -b -nf -- mplayer -wid WID -nosound /full/path/to/video.mpg
```
For me it would be like
```
xwinwrap -ni -o 0.5 -fs -s -st -sp -b -nf -- mplayer -wid WID -nosound /home/user name/Videos/video.3g2

```
When you are entering the command in the terminal and you get to /home you can use the tab keys for help. :)
Edit. Don't forget to add the loop=0 command or the video will stop.

---

