---
title: "monitor and TV"
date: 2010-04-12
forum: General Help
---

### Post by metalmaniac248 on 2010-04-12
has anyone successfully got there ubuntu boxes working with their TVs?
i have an nvidia graphics card with dvi out (going to 19 inch monitor) and HDMI out
i would like to connect my pc to the 32" TV occasionally however whenever i try dual monitors i end would both screens being screwed up and even when i disable the monitor and have only the TV i have bits a thin border of the desktop missing round the edges (going off the screen) 

any advice on how to get this working?

---

### Post by scouser73 on 2010-04-12
> **metalmaniac248 said:**
> has anyone successfully got there ubuntu boxes working with their TVs?
i have an nvidia graphics card with dvi out (going to 19 inch monitor) and HDMI out
i would like to connect my pc to the 32" TV occasionally however whenever i try dual monitors i end would both screens being screwed up and even when i disable the monitor and have only the TV i have bits a thin border of the desktop missing round the edges (going off the screen) 

any advice on how to get this working?

Please follow these instructions for setting up dual monitors.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - **X Server Display Configuration** will now start, now you can set up your monitors to your liking

**3** - Once you have done so click **Apply** then click **Save To X Configuration File**

You will now have dual monitors working.

---

### Post by metalmaniac248 on 2010-04-13
thanks for response, i have tried that before but when i do i have a thin border missing from the display on the TV. the output fills the TV screen but i cannot see the top panel for instance

---

### Post by scouser73 on 2010-04-13
See the screenshot below for further help.

[[IMG]http://img405.imageshack.us/img405/9876/40266078.th.png[/IMG]](http://img405.imageshack.us/my.php?image=40266078.png)

---

### Post by aeiah on 2010-04-13
> **metalmaniac248 said:**
> thanks for response, i have tried that before but when i do i have a thin border missing from the display on the TV. the output fills the TV screen but i cannot see the top panel for instance

this is very common. HDTVs overscan for some mysterious reason - probably because tv signals and dvds expect the tv to overscan and the tv wants to make sure there isnt any black area around the edges.

there's no easy way around this unfortunately. if you're just using it for watching videos you can set mplayer to paint a black border. things like xbmc let you correct overscanning too. before moving to xbmc, i used to use the mplayer command ```
mplayer -vf expand=-22:-15:0:15
``` which got rid of overscanning.

you can mess with xorg.conf to create a resolution within a resolution but this is usually a massive pain in the ***. since you're not using this all the time you might want to consider just making mplayer do the work if its videos you're watching.

some window managers allow you to specify margins around the edges, and this can be another solution. openbox definitely does it and i think xfce does too.

the most simple and inelegant way is to create gnome panels the same thickness as the overscan area and then put your normal panels on top.

---

