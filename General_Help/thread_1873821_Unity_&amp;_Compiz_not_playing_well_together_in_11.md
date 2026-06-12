---
title: "Unity &amp; Compiz not playing well together in 11.10"
date: 2011-11-02
forum: General Help
---

### Post by nstynkt on 2011-11-02
I installed Compiz on a fresh install of Ubuntu 11.10. By doing so I lost the Unity 3D interface and was left with Unity 2D. I tried to make a change in the Unity Plugin and lost Unity altogether. I had to remove and re-install Ubuntu from scratch.

I tried again and the same thing happened.

Re-installed Ubuntu again and tried one more time. Same result.

All I was trying to do is get back the transparent top bar I had in 11.04, where Compiz worked perfectly.

Short of going back to 11.04, is there anything I can do to get a transparent top bar?

---

### Post by stinkeye on 2011-11-02
With the **first** running of ccsm it loads the default settings
and for some reason the unity plugin isn't included hence loss of panel and launcher.

I have messed with compiz a fair bit and can always get 
out of any stuff ups by using 
**ccsm > preferences**
and set back to default (or importing my saved profile)
or 
the same thing in terminal
```
gconftool-2 --recursive-unset /apps/compiz-1
```

Wait a while for compiz to reload and if it fails to display properly,run....
```
compiz --replace &
```

Now when you set compiz back to default the unity plugin is disabled.
So now you have no panel or launcher and sometimes no ctl+alt+t to launch a terminal.
So the thing is you need some other way of launching programs or starting a terminal.
I install easystroke (mouse gestures) and set gestures to run the commands
```
**compiz --replace &** 
and 
**gnome-terminal**
``` and set easystroke to auto start.I also have kupfer (a launcher) installed.
You can install and configure easystroke in your 2d session if your 3d session isn't playing nice.Remember to set easystroke to autostart in it's preferences.

So the **compiz --replace &** mouse gesture will in most cases fix compiz when it fails to load properly.
If that doesn't work then you do as described earlier
# open a terminal with ctrl+alt+t or the mouse gesture.
# enter ccsm. 
# reset ccsm to defaults and wait 15-20 secs.
  you may get a popup to resolve conflicts.Answer yes, and click all the far right disable buttons as they come up. 
# If it doesn't load properly run the **compiz --replace &** mouse gesture.
# Re-enable the unity plugin in ccsm and wait 15-20 secs.
# If it doesn't load properly run the **compiz --replace &** mouse gesture.


In your case probably all you need to do is login, run ccsm, enable the unity plugin
and run **compiz --replace &** if needed.

When you have ccsm set up how you like save your settings in preferences.(export button)
Goodluck.

---

### Post by stinkeye on 2011-11-03
You may find this method easier.
I used gconf-editor to get a list of plugins enabled when ccsm is set to defaults.
I then added the unity plugin to the list and created a script to enable these plugins.
You will retain any customization you have done to the panel and launcher.

If you can't work effectively in your ubuntu session do this in another session.
Save this as  **re-enable_unity** and make executable.(right click properties > permissions and mark execute.
```
#!/bin/bash

sleep 20 &&
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell]
```
Open startup applications click the add button and use the browse button to
browse to where you saved the script.

Log out then into your ubuntu session and wait for the script to run.

When unity is up and running again disable the script in startup applications.Don't remove it...leave it there if needed again and you can just re-enable it.

---

