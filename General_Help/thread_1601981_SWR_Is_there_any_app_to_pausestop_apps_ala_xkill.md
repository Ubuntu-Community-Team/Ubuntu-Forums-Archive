---
title: "SWR: Is there any app to pause/stop apps ala xkill?"
date: 2010-10-20
forum: General Help
---

### Post by SnappyU on 2010-10-20
Is there any app that allows the user to pause/stop apps in a way like xkill?

**Background**
My notebook cpu is a crappy CeleronM from 3 years back.  So sometimes I want to just devote all my attention to one app or want to stop some apps from sucking up juices.  I don't want to tweak with the nice level manually nor go through sys mon.

**XKill**
I have configured xkill with a hotkey.  That way, I press the hotkey, and the cursor turns to a 'X' cross, and I click on the app that I want to kill (usually a hung app).  This means I can avoid the console and the system monitor app.

**XStop / XPause?**
Can I do the same for pausing or stopping apps?  Bind it to a hotkey and a 'X' cross appear for the cursor, and I can pause apps?  Ideally, I should be able to unpause it in similar way.

Suggestions?

---

### Post by SnappyU on 2010-10-21
[https://answers.launchpad.net/ubuntu/+source/xkill](https://answers.launchpad.net/ubuntu/+source/xkill)

Gonna see if I can request for an update to xkill ... or I will submit a patch *yikes* ... time to get my hands greasy ... ^_^

---

### Post by wojox on 2010-10-21
What about Click +Add to Panel and use Force Quit?

---

### Post by SnappyU on 2010-10-21
> **wojox said:**
> What about Click +Add to Panel and use Force Quit?
@wojox, thanks for your suggestion.  
I'm currently using xkill bound to a key for that.  Just tried your suggestion 'Force Quit' works as advertised. :)

What I am trying to do is have something like Force Quit and xkill, only diff is that instead of killing an app, it pauses/resumes an app.  That way, I can dynamically stop apps, thereby allowing the app I am using to have full access to the cpu resources. :)

---

### Post by wojox on 2010-10-21
Hmmm, never tried that. There is a pause function. Open your terminal and try

```
man pause
```

You might be able to hack something together.

---

### Post by SnappyU on 2010-10-28
> **wojox said:**
> Hmmm, never tried that. There is a pause function. Open your terminal and try

```
man pause
```

You might be able to hack something together.
Thanks for the tip.  :)

---

