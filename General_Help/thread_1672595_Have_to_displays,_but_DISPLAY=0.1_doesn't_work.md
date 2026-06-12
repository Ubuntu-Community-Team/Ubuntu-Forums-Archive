---
title: "Have to displays, but DISPLAY=:0.1 doesn't work?"
date: 2011-01-21
forum: General Help
---

### Post by Nathaniel on 2011-01-21
So, I've been tasked with setting up a rather specific demo kit at work. It's a piece of python script that is set to launch on a second monitor (a wall-mounted TV) and display some graphs and stuff. The problem is that, because I didn't get any good hardware specs before purchasing the laptop, the demo was built for nVidia chipsets while I'm using a HP 6450b with the new Intel Core chipset.

Now, I have a shell script that launches the python code depending on a few parameters. If $1 is "full", then it launches it on DISPLAY=:0.1, otherwise it uses :0.0. Here's the problem. :0.0 works fine, and I get the script running and it does what it's supposed to, but whenever I try to run in on :0.1, it complaints that this display doesn't exist. I've confirmed this by running "env DISPLAY=:0.1 gnome-terminal" and getting "Failed to parse arguments: Cannot open display:" back as the result.

Here's the shell script:

```
if [ "$1" = "full" ]; then
	env DISPLAY=:0.1 python pres.py full #display on external hdmi screen
	res=$?
    else
	env DISPLAY=:0.0 python pres.py  #display in laptop screen
	res=$?
    fi

```

I *have* a second display up and running (VGA, but still), using the "Monitor" option in Preferences, so why doesn't it respond to being called? Can I find out what it is called somewhere, so I can change the shell script? Is there a way to write an xorg.conf or something to force the displays to appear as I want them to? Now, it seems, Ubuntu mostly ignores whatever I put into xorg.conf. GDM handles it instead, together with xrandr.

Anyway, quick help would be much appreciated. I'm already way overdue on this thing, and this is the last obstacle I can't get past. Thanks!

---

### Post by earthmeLon on 2011-01-21
Sorry if this doesn't help, but whenever I successfully run a common on another screen/monitor, I issue the command this way:

```
DISPLAY=":0.1" chromium-browser
```

Try running the command without all the fancy scripting to see if you can simply get the program to run on the second screen:

```
DISPLAY=":0.1" python pres.py
```

Let me know what you get if you try that :D

---

