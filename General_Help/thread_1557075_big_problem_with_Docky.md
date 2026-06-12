---
title: "big problem with Docky"
date: 2010-08-20
forum: General Help
---

### Post by squidpotion on 2010-08-20
Ok, so I'm using Docky and every time I restart I get a notice saying that I need to enable compositing, which I thought I did when I first installed it, but since I keep getting a notice I figured that maybe I didn't. So I google'd around and read that just enabling "normal" effects under Appearance will enable it. So it installs, I restart, and my resolution is now HUGE and everything's super slow, including Docky. So I uninstall Compiz (which I'm assuming is what installs to enable effects, right?), restart, and everything is still the same. I can't adjust the resolution of my monitor either. When I do, I get a pop-up saying "It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver cendor's tool instead?"

Does anyone have any idea what I can do to get back to normal (ie, what I need to uninstall) and maybe a better way of enabling compositing? My graphics card is an Nvidia GEForce 8200, if that's relevant. Thanks in advance!

---

### Post by squidpotion on 2010-08-20
Bump.

Ok, so I uninstalled all the Nvidia stuff, hoping one of those was the problem. When I shut down and restarted, I was stuck at the splash screen. Now I'm running in low graphics mode, but everything is somewhat back to normal? Docky is still running slightly sluggish still. Help?

---

### Post by stinkeye on 2010-08-21
If you are using Metacity as your window manager you can enable compositing by...
Alt+F2 and run
```
gconf-editor
```
navigate to /apps/metacity/general/compositing_manager
tick to enable.

Compiz is an OpenGL compositing manager so nothing to be done there
if that's your window manager.

---

### Post by squidpotion on 2010-08-21
> **stinkeye said:**
> If you are using Metacity as your window manager you can enable compositing by...
Alt+F2 and run
```
gconf-editor
```navigate to /apps/metacity/general/compositing_manager
tick to enable.

Compiz is an OpenGL compositing manager so nothing to be done there
if that's your window manager.
Yea, that's what I did the first time, but I kept getting the pop-up from Docky saying that I needed to enable compositing. When I enabled it, my terminal was kinda transparent, which I'm guessing is what compositing is? (window effects, etc.) I'm using Metacity, since I haven't changed anything AND it's running in the System Monitor. 

And Docky (for some unknown reason) is still acting a little sluggish. I'll reinstall it and see what happens. For a while, before I uninstalled all the Nvidia stuff, Ubuntu wasn't even recognizing my external hard drive. Weird.

---

### Post by JugglinPhil on 2010-10-16
I get the same pop-up every time I boot up, is there a solution by now?

---

### Post by stinkeye on 2010-10-17
> **JugglinPhil said:**
> I get the same pop-up every time I boot up, is there a solution by now?
If your using compiz your problem may be docky is starting before compiz.

I use this to start conky after compiz.
Should work for docky.

[COLOR="Red"]**[SIZE="3"]Enable the dbus plugin in CCSM[/SIZE]**[/COLOR]


Save as **start_docky** and mark as executable.(Right click > properties > permissions) 
```
#! /bin/bash
until [ "$done" = "true" ]
do
	if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
	then
                #DISPLAY=:0.0 [COLOR="Magenta"]docky[/COLOR] >/dev/null 2>&1 &
          
		done="true";
	else
		echo "Waiting for compiz"
		done="false"
		sleep 5;
	fi
done
exit 0
```
I don't use docky, so check that "[COLOR="#ff00ff"]docky[/COLOR]" is the startup command in startup applications.
Once checked, delete the startup entry for docky and/or the setting in docky preferences.
Now add an entry in startup applications and browse to where you saved **start_docky**.
Should now load after compiz with no compositing message.

---

### Post by JugglinPhil on 2010-10-19
Thanks I tried it, however executing the file does not do anything.

---

### Post by stinkeye on 2010-10-21
> **JugglinPhil said:**
> Thanks I tried it, however executing the file does not do anything.
Try this [**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=10003045&postcount=2[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10003045&postcount=2")

---

### Post by JugglinPhil on 2010-10-23
For some reason it is working fine now, no pop-up message anymore. :)

---

