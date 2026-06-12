---
title: "Xubuntu dual monitor?"
date: 2011-09-22
forum: General Help
---

### Post by zeating on 2011-09-22
I have one main 1920x1080 LCD monitor and one 1024x768 CRT monitor. The secondary monitor is just a "clone" of the first one, and displays everything that the main one shows. I can't figure out how to switch it to "extended" mode where I can drag windows onto it and such. Catalyst won't let me enable it because it says I only have one monitor plugged in when clearly I'm using 2..How can I fix this?

---

### Post by TeoBigusGeekus on 2011-09-22
Use xrandr. See [this]("https://wiki.ubuntu.com/X/Config/Resolution").

---

### Post by zeating on 2011-09-22
Is that the only way? looks confusing

---

### Post by qiemem on 2011-12-05
Try arandr. It's a graphical front-end for xrandr. Works like a charm for me.

---

### Post by hypertyper on 2011-12-08
I'll jump on the bandwagon:

My problem with arandr is, that the changes aren't persistent. I tried creating an .xinitrc file but it must not have gotten executed, or at the wrong time. Also I doubt it's a good solution since the login screen is then in a different setup.

How do you make persistent changes to the monitor setup in xubuntu? 

(I'm using version 11.10)

---

### Post by The Cog on 2011-12-08
I created this little one-line script:
> xrandr --output LVDS1 --auto --output VGA1 --auto --right-of LVDS1 --rotate normal and added it to my path so I could call it quickly. 

Nowadays, the PC just seems to remember the setting. If I have this command in a place where it runs when I log in anywhere, I can't find it now so I think maybe XFCE is just remembering the last setting.

---

### Post by qiemem on 2011-12-10
There is a much easier way to get the settings to take effect at login. So, have arandr save the settings to some file (in your home directory). Mine's ~/.xrandr/dual or something (not on my xubuntu machine atm).

Via XFCE settings manager, you can choose programs that start automatically at login. Not sure of the exact location, since I'm not on my xubuntu machine, but it's something obvious like "Sessions".

If anybody needs clarification, I can post exact instructions when I get to work on Monday.

---

### Post by moodle on 2012-05-27
I know it's a long time after Monday, but I need some clarification/precise instructions.

Thanks!

---

### Post by qiemem on 2012-05-30
Wow, I'd forgotten about this thread. Here are the precise instructions:

1) Install arandr
```
sudo apt-get install arandr
```
2) Start arandr
```
arandr
```
3) Arrange the your screens in arandr however you wish
4) Layout->Save As. I saved mine as ~/.screenlayout/dual.sh
5) Go into the Settings Manager. Choose "Session and Startup". Go to the "Application Autostart" tab.
6) Hit "Add". Enter the following:
Name: Whatever you want. Mine is "dual-monitor"
Description: Dual monitor layout script
Command: Browse to where ever you saved your layout script and select it.

That's it! Note, you might have to make the layout script executable. To do that, browse to it in Thunar. Right click->Properties->Permissions tab. Check "Allow this file to run as a program".

---

