---
title: "Is it possible to make the side menu solid?"
date: 2012-03-14
forum: General Help
---

### Post by Mark Lyons on 2012-03-14
Is it possible to make the menu bar stay put in its outward form instead of reverting outside whenever you move a window in place of it? I would like to use it as a border and disable it from moving, if that makes any sense yet. It sure is annoying and I would really appreciate some help with this. :)

If I didn't explain what I'm looking for well enough, please let me know and I'll provide additional details.

---

### Post by rg4w on 2012-03-14
Mark, I have the same preference and fortunately there's a setting for that.  It's not in the System Setttings panel yet, though it will be in 12.04. In the meantime, you can find it in Compiz Config Settings Manager (available in the Ubuntu Software Center), in the Unity Plugin.

---

### Post by Mark Lyons on 2012-03-15
> **rg4w said:**
> Mark, I have the same preference and fortunately there's a setting for that.  It's not in the System Setttings panel yet, though it will be in 12.04. In the meantime, you can find it in Compiz Config Settings Manager (available in the Ubuntu Software Center), in the Unity Plugin.

I'm in the Unity Plugin section, but I can't find anything that seems to be changing anything.

---

### Post by Frogs Hair on 2012-03-15
Open the Unity Plug-in > Behavior > Hide Launcher and select never from the drop down menu . It is set to doge windows by default.

---

### Post by Mark Lyons on 2012-03-15
> **Frogs Hair said:**
> Open the Unity Plug-in > Behavior > Hide Launcher and select never from the drop down menu . It is set to doge windows by default.

That's what I tried originally, and it's not working. In fact, when I returned to the settings it was still set to never from that and it still dodges windows. Do I have to like apply changes somewhere or something?

---

### Post by tbrminsanity on 2012-03-16
I've tried using the Compiz Config Manager to stop my Launcher from hiding away.  But the settings don't seem to do anything.  The Launcher still hides after I set the Unity Plugin to never.  Any thoughts?

---

### Post by Frogs Hair on 2012-03-16
> **Mark Lyons said:**
> That's what I tried originally, and it's not working. In fact, when I returned to the settings it was still set to never from that and it still dodges windows. Do I have to like apply changes somewhere or something?

Changes should be applied right away. Have you tried to reset Unity via the terminal ?```
unity --reset
```

---

### Post by Mark Lyons on 2012-03-16
> **Frogs Hair said:**
> Changes should be applied right away. Have you tried to reset Unity via the terminal ?```
unity --reset
```

Resetting it did the trick. Thanks! Works exactly as I wanted it to.

---

### Post by Frogs Hair on 2012-03-16
Glad it worked !

---

### Post by tbrminsanity on 2012-03-17
Yay!  It is fixed for me as well.  Thank you everyone.

---

### Post by tbrminsanity on 2012-03-31
The settings keep reverting.

---

### Post by tbrminsanity on 2012-04-03
Ok I had to reinstall Unity but I got it to finally keep the settings for more then one session.

---

