---
title: "Docky problem!"
date: 2011-03-17
forum: General Help
---

### Post by Sina_RJ on 2011-03-17
my docky was working for all the time so good,with all visuals correct
but suddenly a notification appears and tell me that docky requires compositing and bottom of my screen went black and i don't have any effects on my desktop!
is there a problem with docky or something else is going wrong,please help me :(
i really need docky as it was with all my effects :(

---

### Post by Sina_RJ on 2011-03-17
!!!!!!!!!!!
after a restart it just suddenly got fixed!!!
but I really don't wanna this happens again,cause not even my screen was like that,my voice wasn't working!!!
I'm going on a vacation and i have a lot to do with my laptop,i just don't wanna get in trouble where i have no internet access,please somebody help me :(

---

### Post by flipper T on 2011-03-17
your graphics driver crashed.

reboot restarted it.

---

### Post by antaios256 on 2011-03-17
i have the same issue periodically, reboot always fixes it.

---

### Post by Sina_RJ on 2011-03-17
> **flipper T said:**
> your graphics driver crashed.

thanks,but what about the sound system as well!!
all my drivers crashed?
and what is that compositing which docky talks about?
you have any idea?

---

### Post by Sina_RJ on 2011-03-17
I'll be so glad to have some answers :(
please help me people,really what is this error related to?

---

### Post by flipper T on 2011-03-18
your graphics driver crashed

did a sound driver crash at the same time ? apparently so...

i understand that its working ok now ?

---

### Post by Krytarik on 2011-03-18
Hi Sina_RJ.

Did this happen only once so far?

Concluding from your screenshot it happened within a running session, is that correct? Or at startup?

Also, after this happened, did you still have desktop effects?

---

### Post by Sina_RJ on 2011-03-28
I'm back from my vacation with this trouble all the time during this vacation :((((
here's another screenshot
please,please,please someone help me :(((

---

### Post by Krytarik on 2011-03-28
> **Sina_RJ said:**
> I'm back from my vacation with this trouble all the time during this vacation :((((

I'm so sorry! But I said before that I really don't like it! Because it has a number of deficiencies. It's the only dock (out of 3, the others were AWN and Cairo) which survived only a few minutes at my system. Try AWN instead:
[http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html](http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html)
[https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)

---

### Post by Sina_RJ on 2011-03-29
> **Krytarik said:**
> Try AWN instead
thanks but I've tried that once,but i really didn't like appearance of that.
I hope someone else would help me on this topic :(
this is becoming a real problem with applications on 10.10 :(
waiting for the others who may have some advices...

---

### Post by stinkeye on 2011-03-29
This can be caused by compiz crashing or failing to load and reverting to metacity as the window manager

By default compositing isn't enabled in metacity.
You can enable compositing in metacity, so at least you won't get the black bar when compiz crashes, by running in the terminal..
```
metacity -c
```

Installing and using fusion-icon can help in making sure compiz loads.
```
sudo apt-get install fusion-icon
```

Add it to startup applications using 
```
fusion-icon
```
in the command box.

fusion-icon sits in the notification area and gives you a right click menu to reload
your window manager.

---

### Post by Sina_RJ on 2011-03-29
```
:~$ fusion-icon
 * Detected Session: gnome
 * Searching for installed applications...
 * Intel detected, exporting: INTEL_BATCH=1
 * Using the GTK Interface
 * Starting Compiz
 ... executing: compiz --replace --sm-disable --ignore-desktop-hints ccp
inotify_add_watch: No such file or directory
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png


```

this is what it says and do nothing after that!
should i do something!?!

---

### Post by stinkeye on 2011-03-29
Goto menu > preferences > startup applications
Click on the add button 
and add an entry as shown in pic. Hit the save button.
Log out then in and fusion-icon will be in the notification area as 
shown in pic from previous post.

Metacity is the window manager that runs when you have chosen **no** visual effects (or if compiz fails to load)
in **Appearance > visual effects**.

Compiz is the window manager that runs when you have chosen **normal or extra** visual effects
in **Appearance > visual effects**.

---

### Post by Habitual on 2011-03-29
Graphics driver crashed? Crash/smash. What a bunch of hooey.

Open the GNOME Configuration Editor; press Alt-F2 to open the Run Application dialog and type gconf-editor. Click Run. Navigate to Apps->metacity->general. Check the compositing_manager box, and Metacity will immediately restart with compositing!

---

### Post by stinkeye on 2011-03-29
> **Habitual said:**
> Graphics driver crashed? Crash/smash. What a bunch of hooey.

Open the GNOME Configuration Editor; press Alt-F2 to open the Run Application dialog and type gconf-editor. Click Run. Navigate to Apps->metacity->general. Check the compositing_manager box, and Metacity will immediately restart with compositing!
```
metacity -c
```
will achieve the same thing which he has already done, hopefully.
At the moment we're installing fusion-icon so he can easily switch to compiz if it reverts to metacity.

---

### Post by Sina_RJ on 2011-03-29
hey guys I think there is a problem you all didn't get it!
this is not just my graphic!
i don't have sound after this happens!!
even if i do ```
fusion-icon
```
my graphic will be fixed but what should I do with sound!!!
i don't have it right now!!!

---

