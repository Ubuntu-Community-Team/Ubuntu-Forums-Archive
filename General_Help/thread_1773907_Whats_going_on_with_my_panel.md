---
title: "Whats going on with my panel?"
date: 2011-06-02
forum: General Help
---

### Post by oxf on 2011-06-02
OK this all started earlier when I booted up and found that the Sound Preferences icon on the upper panel had disapeared. Then I had some strange stuff happen with the Wifi icon where it would move to the lower panel without me doing it.

Anyway now this strange blue bar thing has appeared on the upper panel, See screenshot.
I've tried reloading the theme and messing around but I can't get rid of it. In particular the irregular color streaks in the dark area bother me. This doesnt look good.

Any ideas what might be going on and how to start to fix it?

Thanks

---

### Post by pqwoerituytrueiwoq on 2011-06-02
logout then in again or
[FONT=Courier New]killall gnome-panel[/FONT] or
or you can just resize the panel then change it back

---

### Post by oxf on 2011-06-02
> **pqwoerituytrueiwoq said:**
> logout then in again or
[FONT=Courier New]killall gnome-panel[/FONT] or
or you can just resize the panel then change it back

Thanks..

I've logged out/rebooted many  times. 
Tried "killall...."

Neither change anything. FWIW the "glitch" for lack of a better word, seems to stretch/taper down most the lengh of the upper panel although various icons applets seem to hide the problem. I'm wondering if it's a video problem? It looks awful although things seem to be working OK

---

### Post by pqwoerituytrueiwoq on 2011-06-02
missing icons maybe
try marking ambiance for reinstallation in synaptic and apply it

---

### Post by zensawa on 2011-06-02
You could try creating a new user, then use that one instead... I had a similar problem with zenwalk linux and had to do that.

---

### Post by oxf on 2011-06-03
> **pqwoerituytrueiwoq said:**
> missing icons maybe
try marking ambiance for reinstallation in synaptic and apply it

Nope..
I reinstalled both abiance and ubuntu mono, both used in the theme. Neither had any effect.

> **zensawa said:**
> You could try creating a new user, then use that one instead... I had a similar problem with zenwalk linux and had to do that.

That's interesting. I have not created a new user yet, BUT, if I log in as a guest session the problem is not there. Which makes me wonder if it's some sort of profile issue???

---

### Post by oxf on 2011-06-03
I wondering if there's a "profile" somewhere that's corrupted and causing this? (a bit like the firfox one that causes problem occasionally) That migh explain why the problem doesn't exist when I log in as a guest user.
Any ideas?

---

### Post by pqwoerituytrueiwoq on 2011-06-04
maybe you or someone set a background image on the panel
right click panel->properties->background
for the ambiance theme it should be set to none

---

### Post by tredegar on 2011-06-04
[panel-restore]("http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/") is a very useful utility.

---

### Post by oxf on 2011-06-04
> **pqwoerituytrueiwoq said:**
> maybe you or someone set a background image on the panel
right click panel->properties->background
for the ambiance theme it should be set to none

You are correct!!
Somehow, and god only knows how this happened, some graphic file I messed with once got set as the background image. Anyway that resolved it. Thanks!

Katya

---

