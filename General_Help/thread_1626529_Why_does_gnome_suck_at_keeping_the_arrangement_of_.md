---
title: "Why does gnome suck at keeping the arrangement of my icons in the top panel?"
date: 2010-11-20
forum: General Help
---

### Post by Roasted on 2010-11-20
Just wondering... I find a sometimes when I boot up and my resolution wigs out (it always comes back to normal within a second or so as the rest of the login process takes over) my icons in the panel are messed up.

Would like to fix this. Mucho annoying. :(

---

### Post by Roasted on 2010-11-23
:popcorn::popcorn::popcorn:

---

### Post by charlescarroll1 on 2010-11-24
I'm having the same problem. Whenever I login, my bottom panel (the only panel I have) icon's shift, what seems to be, randomly. Using Ubuntu 10.10 on an HP Presario CQ60.

---

### Post by SecretCode on 2010-11-24
Same problem, whenever I run Ubuntu in a VM and change the window size, or whenever I connect my laptop to a data projector and it resizes the screen.

As to why ... I assume the GNOME developers just don't think it's important! Or they have some theory that any way of improving it would make the gnome environment "more complicated".

---

### Post by charlescarroll1 on 2010-11-24
I've been using Ubuntu for a a few years now, and I've had this same problem arise on multiple occasions on a few different machines throughout the years. I just recently started toying around with Ubuntu again and it's very disappointing that something like this still hasn't been fixed :-(

---

### Post by Hostie on 2010-11-24
have you tried locking the icons in place (right click on icon and select "lock to panel")?

---

### Post by robert shearer on 2010-11-24
O.K,  simple fix....get the panel icons as you want them, right click each and 'lock to panel'  Then...
System=>Preferences=>Startup applications.
Then open the 'Options" tab and put a check in the box for 'Automatically remember running applications when logging out'

As your panels are 'running applications' their layout will be remembered on startup.


(Do close all application windows on logout as any not closed will be opened on next boot. Or you might want some to open on boot ???. Your choice  ;))

---

### Post by dcstar on 2010-11-24
> **Roasted said:**
> Just wondering... I find a sometimes when I boot up and my resolution wigs out (it always comes back to normal within a second or so as the rest of the login process takes over) my icons in the panel are messed up.

Would like to fix this. Mucho annoying. :(

Your problem is** not** Gnome, it is doing the best it can to fit things onto the available resolution.

If you have a problem with unstable resolution that get that fixed and Gnome won't have to do what it is designed to do by displaying as many icons as it can in the available space.

XP also does exactly the same thing to its desktop when resolutions change, as it is designed to do.

---

### Post by SecretCode on 2010-11-24
The problem IS gnome. 

Sure, if you reduce the size of the screen, it does the best it can to fit all the icons in. But if you are forced to reduce it temporarily and then go back to the normal size, the icons are often placed quite differently from the original state (even in a different order), regardless of whether they are locked to the panel or not. "Messed up."

The OP may have an issue with "unstable" resolution, but that's not relevant - there are legitimate use cases of changing resolution.

---

### Post by charlescarroll1 on 2010-11-24
When my laptop boots up, I usually have a second screen attached which alters the resolution until I login. Are you saying this is the cause of the shifting panel icons?

---

### Post by Roasted on 2010-11-25
> **charlescarroll1 said:**
> When my laptop boots up, I usually have a second screen attached which alters the resolution until I login. Are you saying this is the cause of the shifting panel icons?

It could be. I do not exhibit this on my desktop, which is running Nvidia with a xorg file and never changes. My laptop is an Intel setup which bounces with resolution here and there since I sometimes have a 2nd monitor attached too.

Thing is, there are times I power off with my resolution set and 1 monitor. Then I power up, and it's wacked out of its mind @ 1024x768 (which is not right). Then if I log in, things are messed up and once I go to system - preferences - monitor, it resets to proper resolution, often times with wacked out icons.

---

### Post by Roasted on 2010-11-26
Just a thought - is there a way to generate a xorg file (even though I'm using an Intel card) and still be able to utilize the "Monitors" option in system - preferences to set up dual screen in the situations where I DO have a 2nd monitor handy? It'd be nice if with a single screen every SINGLE time it responded predictably, and it only respond differently in the presence of a 2nd monitor, which I would obviously be controlling anyway via "monitors" - assuming that's possible...

---

### Post by Statik on 2010-12-20
I randomly have this widget moving problem as well. I don't change resolutions and my panels are all locked into place. The main place I notice it is the top-left cluster which contains the following, normally:
Mail, Volume, Wifi, Weather, Time/Date, Profile, Power
Right now, its Wifi, Time/Date, Volume, Mail, Profile, Power. Why did it move? I don't know. To fix it, I have to use Ubuntu Tweak to allow the lock checkbox on the items, then unlock all of the items that need to be moved, move them, then relock them. It will stay stable for a while and then move again. Why do I not have the option to set the order of left-hand section and let it just fill them in, even if the resolution changes?

Statik

---

### Post by Roasted on 2010-12-20
Not to drop a "Wait till April" bomb, but I've had no luck with solidifying the location of these icons. That being said, I have high hopes that Unity will do a better job of it. At first I thought Unity would be a bomb, but the more I use it the more I see its potential.

Don't mean to get into a Unity vs Gnome discussion, or steal the line from the recent presidential election, but change is coming! Let's see how the cards are dealt come 11.04.

---

