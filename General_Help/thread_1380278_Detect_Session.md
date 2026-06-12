---
title: "Detect Session"
date: 2010-01-13
forum: General Help
---

### Post by Vitamin_A on 2010-01-13
Hi All,

I've recently installed KDE and Xfce sessions onto my Ubuntu machine, so that I can have those options available, but, I have a bit of a problem.
Basically, for my GNOME session, I have a myriad of programs running at start-up, which I want, but only in GNOME.  In KDE and Xfce, these programs also start up, although I do not want them to.
Is there a way to configure the programs to only run in GNOME?
I was thinking that I could create a script to detect which session I am running, and run programs accordingly; and then run that at start-up, but, I don't know how to code a session detector.

Thanks.

---

### Post by VCoolio on 2010-01-13
One option is to find the launchers for your startup apps in /etc/xdg/autostart or ~/.config/autostart and play with a line:

OnlyShowIn=GNOME;

Launchers in /etc/xdg/autostart are overruled by the ones in .config, and can be set to not launch automatically by copying them to .config/autostart and change/add the line:
X-GNOME-Autostart-enabled=false

Other option (which I use) is to create different files in which you put your startup commands, and call in each session the one for that session. Like:

```
#!/bin/sh
conky &
tint2 &
whatever &
anotherthing -a -b &
```

Just end all commands with '&' to put them to background (except if they go to background automatically, like conky probably, depending on your config).

---

