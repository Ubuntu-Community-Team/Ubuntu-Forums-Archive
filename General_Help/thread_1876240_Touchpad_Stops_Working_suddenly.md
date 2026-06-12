---
title: "Touchpad Stops Working suddenly"
date: 2011-11-05
forum: General Help
---

### Post by rushikesh988 on 2011-11-05
Hello friends I am using Acer Aspire One D257 Netbook and installed ubuntu 11.10 
Touchpad problem is occuring to me from last 2 days...It stops working suddenly ... but everytime is happened I was using firefox...
I tried to uncheck mouse and touchpad setting ->disable touchpad while typing ...but still no effect...
touchpad doesn't work back evenif I exit firefox ...
the only way to get it work back is to restart ubuntu..

please help me ....

---

### Post by charlesopondo on 2011-11-06
I'm also experiencing the same problem today. My machine has been perfect until now. HP Probook 4330s running Ubuntu 11.10

---

### Post by charlesopondo on 2011-11-06
And as quickly as I experienced the problem I found at ubuntuforums.org/showthread.php?t=1852081&page=3 that:

```
synclient TouchpadOff=0
```

fixes it for me!

---

### Post by tjeremiah on 2011-11-07
> **charlesopondo said:**
> And as quickly as I experienced the problem I found at ubuntuforums.org/showthread.php?t=1852081&page=3 that:

```
synclient TouchpadOff=0
```

fixes it for me!

this appears to work :)

---

### Post by sledhead45 on 2011-11-21
I experience this also on my dell m1330. doing a ctrl+alt+t and:
```
synclient TouchpadOff=0
```
fixes it. Is there an official bug ticket for this issue? Slightly annoying.

---

### Post by furnace on 2011-11-22
Sorry to "me too" this but really, this is probably the most frustrating bug  as far as simply using my computer is concerned!

I suspect there is some gesture or way to tap the pad or something to turn the touchpad off which I'm doing accidentally?

---

### Post by sup on 2011-11-23
The bug is here: [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/868400](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/868400)

---

### Post by CryptKeeper777 on 2011-11-30
> **charlesopondo said:**
> And as quickly as I experienced the problem I found at ubuntuforums.org/showthread.php?t=1852081&page=3 that:

```
synclient TouchpadOff=0
```fixes it for me!
Made my day! :) (which won't last for more than ten more minutes, but whatever... :) )

These are the most annoying bugs: The system still runs perfectly, but you have to restart anyway... Same as when gnome shell crashes.

---

### Post by fgimelli on 2011-12-21
I'm wondering if I'm experiencing the same bug...

I am running 11.10 on an Asus EeePc, and so far I've had no problems (around 3 months) with the trackpad. This morning I turned on the machine, and the trackpad worked fine until I logged in to my user account, after which the trackpad seemed to stop responding completely.

I tried logging in to the guest account and in here the trackpad works without any trouble. Restarting the machine has no effect, so I could use your help, please. :)

---

### Post by CryptKeeper777 on 2011-12-22
Have you tried typing "synclient TouchPadOff=0" in a terminal (or with Alt-F2)? That fixes the problem in my case (though of course, it only fixes the symptom of the actual problem, not the problem - the bug - itself, but that's enough for me since it doesn't happen that frequently).

---

### Post by Saladin1 on 2011-12-25
```
synclient TouchpadOff=0 
```
worked for me , thanks alot.

---

### Post by skullriot on 2011-12-27
Is there an actual fix for this or do we just need to keep using the work around? Can anyone report on how long this stays fixed? My touchpad has been consistently freezing after executing a command in gnome do, right after launch. I don't want to keep having to use my windows partition just because of this.

---

### Post by mattgif on 2012-04-17
Still looking for an actual fix for this. Touchpad shuts off suddenly a few minutes after boot. It used to occur daily, recently it's once every other week or so (maybe once every 20 boots). I've been using the Synclient TouchpadOff=0 fix as a temporary fix, but I'd like to know if anyone found a more permanent solution.

---

### Post by cortman on 2012-04-17
> **mattgif said:**
> Still looking for an actual fix for this. Touchpad shuts off suddenly a few minutes after boot. It used to occur daily, recently it's once every other week or so (maybe once every 20 boots). I've been using the Synclient TouchpadOff=0 fix as a temporary fix, but I'd like to know if anyone found a more permanent solution.

It would be better to start a new thread on this subject...
Have you tried making a script with the necessary synclient commands and having it run at startup?
I'm using Fedora 16 LXDE spin on my netbook, and I had the problem of tap to click and scrolling being turned off. Writing a startup script fixed it beautifully.

---

