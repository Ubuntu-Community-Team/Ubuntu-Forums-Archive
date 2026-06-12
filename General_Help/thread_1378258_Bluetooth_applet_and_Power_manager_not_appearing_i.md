---
title: "Bluetooth applet and Power manager not appearing in Panel"
date: 2010-01-11
forum: General Help
---

### Post by jamorod on 2010-01-11
This may be a little silly question for some, but for some reason, I just don't manage to fix this issue.

While trying to fix other problem, a few days ago suddenly I stopped seeing at least two icons in the panel which I used to find quite useful. One was the Bluetooth icon and the other a power manager.

When clicking on the bluetooth I would get a drop down showing me options for sending files or browsing, etc.

The power manager icon would show graphs and other functions.

However, now I cannot get those icons back and I cannot get those applications anywhere else... I hope somebody can understand my problem and give me a hand.

Thank you!

---

### Post by SecretCode on 2010-01-11
If you're on a notebook, or anything with a battery, unplug the power. The power manager icon should reappear (then you could edit its preferences for when to display the icon).

Similarly if you have a bluetooth or radio on/off switch, switch it on. The bluetooth icon on my machine is hidden when bluetooth is off. (Radio means things like bluetooth, wifi and 3G wireless WAN ... not music.)

If these don't apply to you, I think we'll need to look for gconf settings.

---

### Post by jamorod on 2010-01-11
Hey SecretCode... yes, I'm in a notebook: Dell Vostro 1014.

I've done what you told me... remove the power and switch off the radio, plug it in back and switch it ON again respectively, but the icons do not reappear.

I have gone to the gconf-editor, then I went to the bluetooth manager within the apps folder. The "icon_policy" says always... I changed it to never and brought it back to always... but still not reappearing... What should I do here?

Which folder would store the one for the power?

---

### Post by colsandurz on 2010-01-12
First see if the program is running at all, do this

```
ps -ef|grep gnome-power-manager
```

if you see the program in printed list, then it's running.  If it's not there start it by doing:

```
sudo gnome-power-manager
```

That will start the program if hasn't doesn't start when you boot, if you want it to start when you boot do this

click system -> prefs -> startup apps 
then check power manager

The process is similar for bluetooth, I just don't know the name of the application.  If that doesn't work post the output of each step to this thread and someone should be able to help.

---

### Post by SecretCode on 2010-01-12
For bluetooth, I have the following processes:
bluetooth
bluetoothd
bluetooth-applet

I'd guess the icon is managed by bluetooth-applet.

You do have the Notification Area applet visible in your panel, don't you?

---

### Post by jamorod on 2010-01-12
> **SecretCode said:**
> 

You do have the Notification Area applet visible in your panel, don't you?

This was the problem! I didn't have the Notification Area applet visible in my Panel... I didn't know that this was it.

Thank you!

---

### Post by SecretCode on 2010-01-12
Sometimes it's the simple things ... :)

---

