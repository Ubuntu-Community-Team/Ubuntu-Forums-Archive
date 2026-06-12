---
title: "Disbaling or making Unity bar less sensitive?"
date: 2011-10-20
forum: General Help
---

### Post by pbateman on 2011-10-20
Hey guys
I installed 11.10 but the unity side bar is way too sensitive, i cannot browse a webpage with links on the lefthand side without the bar popping up and blocking them. It gets to be very annoying and makes me wish they had not done away with the Gnome 2 desktop as simple as it was. Is there any way to disable the bar popping up when I hover the left hand side of the screen and only do so when i click the windows button?
I tried going back to Gnome 2 by installing the files but the Gnome 2 interface in 11.10 looks poorly done or unfinished compared to the one available in 11.04...


Thanks!

---

### Post by roger_1960 on 2011-10-20
Hi

You can set the laucher to only appear when the mouse touches, say, the bottom left corner rather than anywhere on the left edge.

Install compiz config settings manager (ccsm) using software centre or synaptic if installed.  Run ccsm from the dash.  Go to the Unity plug in section where you can edit the "reveal mode" ie where the mouse goes to activate the launcher

You can set it to "none" so that you have to use the super button

Hope this helps

---

### Post by pbateman on 2011-10-20
Thanks, I will try that!!

---

### Post by kaldor on 2011-10-20
This is the reason I'm currently using GNOME Shell instead. I greatly recommend trying out the Shell UI; you might like it a lot once you get used to it.

Install the *gnome-shell* package in the Software Centre or by using:

```
sudo apt-get install gnome-shell
``` 

Log out, click the gear on the login screen. Change "Ubuntu" to "GNOME". I find GNOME Shell gets in my way much less.

---

### Post by pbateman on 2011-10-20
I installed Gnome shell earlier which installed some sort of Gnome 2 looking desktop option but somehow it looks almost unfinished and nothing like the more polished version in  11.04...but might have to use that if i cant get the side bar to behave in unity...

As far as installing ccsm the only thing i see when i type ccsm is something called "ComQat library of utility functions and classes", I installed that but when i try running ccsm from the dash nothing shows up, am I missing anything?

---

### Post by stinkeye on 2011-10-20
> **pbateman said:**
> I installed Gnome shell earlier which installed some sort of Gnome 2 looking desktop option but somehow it looks almost unfinished and nothing like the more polished version in  11.04...but might have to use that if i cant get the side bar to behave in unity...

As far as installing ccsm the only thing i see when i type ccsm is something called "ComQat library of utility functions and classes", I installed that but when i try running ccsm from the dash nothing shows up, am I missing anything?

```
compizconfig-settings-manager
```
Search in the software centre for compiz and find
**Open gl window and compositing manager**

After installing
it can be started in the terminal or located in the dash using
```
ccsm
```

In the unity plugin in ccsm you will see an option for **reveal mode**.

If you have the screen size I find it best to have the **hide launcher** set to "never".

---

### Post by Magick93 on 2011-10-20
> **pbateman said:**
> Hey guys
I installed 11.10 but the unity side bar is way too sensitive, i cannot browse a webpage with links on the lefthand side without the bar popping up and blocking them. It gets to be very annoying and makes me wish they had not done away with the Gnome 2 desktop as simple as it was. Is there any way to disable the bar popping up when I hover the left hand side of the screen and only do so when i click the windows button?
I tried going back to Gnome 2 by installing the files but the Gnome 2 interface in 11.10 looks poorly done or unfinished compared to the one available in 11.04...


Thanks!

Agree! I think the idea of putting Unity on the left, where most webpages have their menu, where the browser back button is, where the application close buttons are, was not well thought through. 

And to make Unity have to be on the left is a big step backwards. For years now in Windows you could move the task bar where ever you wanted. And Ubuntu had a reputation of being super customizable. But Unity seems not very customizable. But, I'm new to it, so maybe I just dont know how to use and customize it.

Im going to try for a few more days.

---

