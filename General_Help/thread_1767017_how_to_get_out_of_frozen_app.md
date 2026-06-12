---
title: "how to get out of frozen app"
date: 2011-05-25
forum: General Help
---

### Post by brunobliss on 2011-05-25
I'm using Doxbox for old games and all of the times the mouse and keyboard get stuck in it.
 Whenever there's a freeze i just can't get out. 
On windows i can use CTRL+ALT+DEL and it gets me out immediately, 

how do i do this in ubuntu?

---

### Post by alenis on 2011-05-25
Add to the panel the "Force quit" applet. It forces an application to quit. Using it is very easy. Otherwise, try to kill the frozen application through the temrinal. This is more difficult.

---

### Post by webofunni on 2011-05-25
cntrl+alt+del is also works in UBuntu and that will give you the option to shutdown/restart etc. Are you able to switch the windiws using alt+tab when it freezes ? Try ctrl+alt+f1 to get a console, if everything freezes.

---

### Post by Haur on 2011-05-25
I've had the same problem a couple of times and nothing has really worked for me.
The force quit applet on the panel won't work if you can not alt-tab and thats usually the case for me. Opening a virtual panel (CTRL+ALT F#) works most of the time but when i get there i'm such a "noob" that i don't know what i can do to fix the problem, usually i don't know the appname i want to kill and/or can't restart the GUI.

So in the end i do the rseiub thing and that always works. But a method that works everytime on the frozen app would be great :)

---

### Post by seawolf167 on 2011-05-25
My preferred way (if I don't have the Force Quit panel icon), is to just hit my terminal shortcut keystroke to open a terminal, enter *htop*, find the offending program and kill it.

By far the easier way though (IMO) is to simply use the force quit applet as Haur suggested.

---

### Post by webofunni on 2011-05-25
In the console 

```

ps aux | grep frozen-app-name | grep -v grep | awk '{ print $2}' | xargs kill -9

```

Will do 4 u ?

---

### Post by seawolf167 on 2011-05-25
> **webofunni said:**
> In the console 

```

ps aux | grep frozen-app-name | grep -v grep | awk '{ print $2}' | xargs kill -9

```Will do 4 u ?


Ohhh, nice, thanks!

---

### Post by aeiah on 2011-05-25
i usually just:

-ctrl+alt+F1
-log in if necessary
- issue ```
killall name-of-app
```
- get back to my graphical session with alt+ctrl+F7 )or F8, whatever

---

### Post by Cpierce on 2011-05-25
I added "system monitor" to my top panel. It shows your CPU load in a nice little graph. I click on it every now and then to see how much RAM I am pulling. But if I get a frozen app, just click on it, go to processes, then right click and kill it. Very much like windows' task manager.

---

### Post by aeiah on 2011-05-25
> **Cpierce said:**
> I added "system monitor" to my top panel. It shows your CPU load in a nice little graph. I click on it every now and then to see how much RAM I am pulling. But if I get a frozen app, just click on it, go to processes, then right click and kill it. Very much like windows' task manager.

yea i use htop for those purposes. but sometimes, you just cant click around your desktop any more.

incidentally, htop runs in a terminal, so you can also use it in your ctrl+alt+F1 window.

---

### Post by Habitual on 2011-05-27
Alt+F2 > xkill > click on dosbox = gone.

---

