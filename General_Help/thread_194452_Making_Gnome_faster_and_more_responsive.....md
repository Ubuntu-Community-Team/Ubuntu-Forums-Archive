---
title: "Making Gnome faster and more responsive...."
date: 2006-06-11
forum: General Help
---

### Post by Patrick-Ruff on 2006-06-11
hey all, can anyone tell me some optimization tweaks that you have used before that seem to make gnome more responsive in most perspectives? see, it takes like a quarter second to display icons in the top menu and all that, I don't think it should have such a delay, and I'm sure there are steps that can be taken to make it more responsive then windows even, my graphics card is setup perfectly, games work perfectly graphics wise.

here are my system specs
1.6GHz Pentium M 2.0MB L2 Cache
512MB PC3200 RAM DDR2
64MB (dedicated) ATI Mobility Radeon X300 PCI Express

thanks to those that actually attempt to help.

---

### Post by Ramses de Norre on 2006-06-11
```
gconf-editor /apps/metacity/general
``` and check reduced_resources. I always did this when using metacity, makes it a lot faster (but you'll lose a couple of graphical effects).

---

### Post by Patrick-Ruff on 2006-06-11
what graphical effects? I don't think I shoudl have to sacrifice, I'de rather keep all the good stuff I have with more performance. this is not a lack of power issue, because I've seen a couple hundred people with this problem and they had insanely fast computers.

---

### Post by Patrick-Ruff on 2006-06-11
I found something interesting on this, 'auto_raise_delay' should I set that to 0?

---

### Post by Ramses de Norre on 2006-06-11
I guess that'll make the panels or menus disappear and appear quicker, with graphical effects I mean that windows wont have contents while moving etc..

---

### Post by HeavyAl on 2006-06-11
[QUOTE=Patrick-Ruff]I found something interesting on this, 'auto_raise_delay' should I set that to 0?[/QUOTE]

This is only useful if you have windows set up to 'raise' when the mouse runs over them - which is a legacy default of X servers. In todays gnome and kde environments this is usually off and the default is similar to MS Windows where you click on the window to have it raise - which this setting has no effect on.

---

### Post by Patrick-Ruff on 2006-06-11
I see.. what about my sluggish gnome enviornment? I read something about installing XGL and Compiz remedeeing the problem, I find that quite hard to believe, what do you guys think?

---

### Post by Patrick-Ruff on 2006-06-11
xgl screwed up my laptop. it seems, when I restart it trys to go to the welcome screen but it shows the mouse and a grey black and white dotted background.

---

### Post by Patrick-Ruff on 2006-06-11
this is not cool people, my laptop aint working and nobody reponds to this?

---

### Post by Patrick-Ruff on 2006-06-11
well I'm gonna take a shower, you guys ask for information that I may be leaving out, my laptop freezes kinda at the welcome screen, it shows like a tun of black and white dots kinda blending into a grayish color, and then it shows the mouse pointer on the 'loading' icon but it stays there forever.

---

### Post by 23meg on 2006-06-11
How exactly did you install XGL/Compiz? Did you follow a guide? If so, which one? Commenting out the changes you made at the bottom of the /etc/gdm/gdm.conf-custom file should revert the default X server to Xorg.

---

### Post by 23meg on 2006-06-11
Things you can do about GNOME sluggishness:

- Use a simple, non-pixmap GTK theme with a fast theme engine, such as Clearlooks.

- Make sure your CPU is running at full speed and not slowed down by powernowd or a similar frequency scaling daemon. This has its uses but if your computer is adequately cooled you may want to run at full speed or close to full speed at all times instead of resorting to adaptive frequency scaling.

- Make sure your xorg.conf file is set up correctly for your hardware.

- Use a compositing manager such as xcompmgr and / or a GL based X setup such as XGL / AIGLX.

---

### Post by Patrick-Ruff on 2006-06-11
yes I installed it using the instructoins, and that second post is pretty much pointless, I've done all of that and then some, I'm TRYING to get XGL working lol...

---

### Post by Patrick-Ruff on 2006-06-11
I can log on in recovery modem by the way...

---

### Post by 23meg on 2006-06-11
> **Patrick-Ruff]yes I installed it using the instructoins, [/quote]And what I asked in the first post was: which instructions? It can make a lot of difference.>  and that second post is pretty much pointless, I've done all of that and then some,It's not pointless said:**
> I'm TRYING to get XGL working lol...
Your thread title says otherwise. If you're looking for help on getting XGL working you should have first asked at the appropriate thread where a guide is posted, or if you have a more specific problem, started a new thread with a more descriptive title.

---

### Post by Patrick-Ruff on 2006-06-11
well, I'm trying to get it working now :) I used the guide on the following page
[http://ubuntuforums.org/showthread.php?t=148351](http://ubuntuforums.org/showthread.php?t=148351)
sorry I have ADD so sometimes I mis-read things or skip some thigns and all that.

---

### Post by 23meg on 2006-06-11
[QUOTE=Patrick-Ruff]well, I'm trying to get it working now :) I used the guide on the following page
[http://ubuntuforums.org/showthread.php?t=148351](http://ubuntuforums.org/showthread.php?t=148351)
sorry I have ADD so sometimes I mis-read things or skip some thigns and all that.[/QUOTE]
Alright, but there are eight different guides linked from that thread. Again, which one? Why not ask at the thread where the guide you followed is posted, or the Compiz forums?

To get back your working Xorg in the meantime, follow my instruction in the first post.

---

### Post by Patrick-Ruff on 2006-06-11
how would I go about reverting to my old xorg?

---

### Post by 23meg on 2006-06-11
Can depend on which instructions you followed, but probably this way: make the end of your /etc/gdm/gdm.conf-custom file look like this:

```
[servers]
#0=Xgl 

#[server-Xgl] 
#name=Xgl server 
#command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
#flexible=true
```

---

