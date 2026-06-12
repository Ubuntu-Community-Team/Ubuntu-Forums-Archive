---
title: "Is it safe to do this?"
date: 2011-06-13
forum: General Help
---

### Post by CaptainMark on 2011-06-13
Ive just got my new netbook, yay, and ive just finished setting it all up just how i want it. Well to save on battery i thought id attach a few commands to keyboard shortcuts, one was `banshee --stop` i thought this would completely stop banshee running as nowadays banshee seems to stop whenever the main window is closed and nothing is playing, well this doesnt stop the process just stops playback but banshee is still running wasting resources.

Getting down to the main point, is it okay to attach this command to a keyboard shortcut```
banshee --stop &
sleep 5 && killall banshee
```I was worried the `killall banshee` may damage processes , it seems okay but my knowledge of this isnt great i dont want to harm my hdd or anything by regularly killing proceses

---

### Post by blind2314 on 2011-06-13
> **CaptainMark said:**
> Ive just got my new netbook, yay, and ive just finished setting it all up just how i want it. Well to save on battery i thought id attach a few commands to keyboard shortcuts, one was `banshee --stop` i thought this would completely stop banshee running as nowadays banshee seems to stop whenever the main window is closed and nothing is playing, well this doesnt stop the process just stops playback but banshee is still running wasting resources.
 
Getting down to the main point, is it okay to attach this command to a keyboard shortcut```
banshee --stop &
sleep 5 && killall banshee
```I was worried the `killall banshee` may damage processes , it seems okay but my knowledge of this isnt great i dont want to harm my hdd or anything by regularly killing proceses
 
You won't damage any part of your hardware by killing a media player. Since you're stopping it first, the chances of corruption of any data are extremely slim (they would be slim even if it's running, most well written applications are designed to have a certain amount of tolerance in "emergency" shutdown situations). I'd say you'll be fine.
 
That beind said, are you sure there's much to gain by terminating the (I'm assuming daemon) processes that continue to run after you stop it? You might want to research that first, just to make sure this is worth worrying about :)

---

### Post by Joe of loath on 2011-06-13
What's wrong with right-click quit?

---

### Post by CaptainMark on 2011-06-14
> **Joe of loath said:**
> What's wrong with right-click quit?nothing, im just a fan of keyboard shortcuts, much quicker

---

### Post by Habitual on 2011-06-14
```
killall -9 banshee
```

Killing banshee shouldn't "damage" any audio files.

---

### Post by CaptainMark on 2011-06-14
whats the -9 for, im assuming by the killall man page its something to do with a particular type of kill signal but theyre not listed there

---

### Post by blueridgedog on 2011-06-14
See:

[http://aplawrence.com/SCOFAQ/FAQ_scotec6killminus9.html](http://aplawrence.com/SCOFAQ/FAQ_scotec6killminus9.html)

The word kill is a bit off in this instance as the real kill is the 9 signal.

---

