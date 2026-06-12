---
title: "Messed up gnome.."
date: 2010-04-06
forum: General Help
---

### Post by gwu777 on 2010-04-06
hi there, this morning, I was cleaning up my system and i have done apt-get autoremove. I agreed to remove everything suggested. When I restarted, the bar on top of my windows to close/minimize and all had disapeared.

I found out that doing metacity --replace in the ternmianl would fix that... unhappy with that temporary fix I took matter in my own silly hand.

I installed xfce-desktop, uninstalled metacity from there and reinstalled it... I figured it would reinstall with all the packaged missing!

Now gnome won't even start, I do not want to reinstall everything, I rather try to learn why it isn't working and what it is I have done wrong, although I realize the list might be long!

Thank you for your help.

---

### Post by MichealH on 2010-04-06
Just type this in the terminal to reset all panels and settings to default.

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

Then log out login and It should be fixed.

---

### Post by gwu777 on 2010-04-06
OK, may have jumped ship too quickly, laptop restarted and after checking the disk, ubuntu starts again... I sill don't have my bar on top though... And I need to do "metacity --replace" all the time...

---

### Post by gwu777 on 2010-04-06
> **MichealH said:**
> Just type this in the terminal to reset all panels and settings to default.

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```Then log out login and It should be fixed.

Oh boy! It did reset alright! I am back like the old days! however, I still don't have my bar with the cross and all back, still need to do metacity --replace...

---

### Post by lordskid on 2010-04-06
did you try to install ubuntu desktop? easiest way will be through synaptic package manager search for ubuntu-desktop then reinstall it.

---

### Post by gwu777 on 2010-04-06
> **lordskid said:**
> did you try to install ubuntu desktop? easiest way will be through synaptic package manager search for ubuntu-desktop then reinstall it.

Done it, reinstalled compiz I uninstalled just in case, and it is still not working... No bar at the top unless I do metacity --replace...

---

### Post by gwu777 on 2010-04-06
Maybe it is not gnome that is messed up...

I usually run ubuntu without effect, i tried to enable them, I know they usually work on my laptop as I have donne it before. It tells me it can activate them. (However the bar is coming back to normal until next loggin...)

I then tried to install manually my ATI prioritary drivers, and there the installtion failed, however it used to work... Could the problem be located around there? How can I re-install my ATI driver - it used to work...

---

### Post by MichealH on 2010-04-06
You could do it through synaptic If you check you could purge ATI drivers in terminal then install it again.

---

### Post by gwu777 on 2010-04-06
After restarting the laptop, I was able to install the ATI Prioritary drivers. When they are activated and the desktop effect set to normal, no-more problem. It seems to me that the problem come from the open source drive of my graphic card, which has been working fine until now... I have reinstalled the following to see if it would solve the problem:

$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri

Still the same when running with the open source. I will be using the other drivers for the moment, but I would love to understand where the problem comes from...

---

### Post by Roamer145 on 2010-04-06
2 possible solutions for you to try out. They won't solve the drivers issue, but they may get metacity running on login again.

I know it's a "quick and dirty" (and lazy) way, but it *should* start metacity on login for you.
Open a terminal and type:
```
gedit .bashrc
```
(If you have a different text editor you prefer, replace gedit with the one you like.) Then, add:
```
metacity --replace
```
to the end of the file. Save it. Log out, and log back in. It *should* start metacity just fine.


For a alternative solution, did you happen to install another window manager/window decorator/desktop environment? If so, which one(s)? The reason I ask is because I had an issue with emerald that required a manual start of the window decorator. I had set CompizConfig to enable window decoration, but I forgot to type in the command (whoops...). Simple to fix, I just added the command (emerald --replace in my case) and it worked like a charm. :D

---

### Post by gwu777 on 2010-04-06
> For a alternative solution, did you happen to install another window manager/window decorator/desktop environment? If so, which one(s)? The reason I ask is because I had an issue with emerald that required a manual start of the window decorator. I had set CompizConfig to enable window decoration, but I forgot to type in the command (whoops...). Simple to fix, I just added the command (emerald --replace in my case) and it worked like a charm. :D

Thank you for the tip, I did think about doing this, but I rather not, for personal reason. It does work with the priotary drive and I guess I will use these, however, i would love to really fix the problem, if anyone knows!

I haven't installed another windows manager or other before the problem...

---

### Post by MichealH on 2010-04-06
So Is it fixed?

---

### Post by gwu777 on 2010-04-06
> **MichealH said:**
> So Is it fixed?

Yes and No

Yes, my laptop is back to normal and usable as I wish.

No because the root of the problem hasn't been found and I don't like it. I am now using the proprietary driver which is not my original configuration and I have to use compiz otherwise the problem come back.

Metacity still has a problem. If I understand well, when no special effect are used, it is metacity, otherwise it is metacity right?

I have purged metacity has said above and reinstalled but still no chance... I like to understant things and knowing that ubuntu won't work well if I remove the effect bugs me.

---

### Post by MichealH on 2010-04-06
Maybe try the Fusion icon? Install it by clicking [this APTURL link.]("apt://fusion-icon")

If the link doesn't work then goto Synaptic and install fusion-icon

---

### Post by lidex on 2010-04-06
Have you tried gconf-editor? Apps>Metacity>General>Compositing Manager

Alt+F2 command:
```
gconf-editor

```

---

### Post by gwu777 on 2010-04-22
> **lidex said:**
> Have you tried gconf-editor? Apps>Metacity>General>Compositing Manager

Alt+F2 command:
```
gconf-editor

```

This didn't change the original problem. However, here are the latest news, following testing of new catalyst drivers, i screwed my system even more!

The problem was with my xorg.conf file. The file karmic do not need anymore... I deleted it (actually moved it!) and upon the next restart ubuntu created a brand new one and I now have metacity working perfectly again.

I do not understand why all this happened, but deleting my xorg.conf file did the trick.

Thank you all for your help.

[SOLVED]

---

