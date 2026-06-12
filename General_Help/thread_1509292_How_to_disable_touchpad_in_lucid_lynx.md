---
title: "How to disable touchpad in lucid lynx"
date: 2010-06-13
forum: General Help
---

### Post by Bladtman242 on 2010-06-13
Hi, I don't know how many has had this problem, but I understand I am  not the only one:grin:

The problem is that after using synclient to disable the touchpad in 10.04 it would enable itself, seemingly, at random.

Well, what I found was that unchecking  the "Disable touchpad while  typing" feature in "System->Preferences->Mouse->Touchpad" will  fix the problem.

Apparently the system does not recognize that the user has deliberately  disabled the touchpad. And so it will reenable it when the user is "done  typing".


I Hope someone will find this useful :smile:

---

### Post by bobcollard on 2010-06-14
> **Bladtman242 said:**
> Hi, I don't know how many has had this problem, but I understand I am  not the only one:grin:

The problem is that after using synclient to disable the touchpad in 10.04 it would enable itself, seemingly, at random.

Well, what I found was that unchecking  the "Disable touchpad while  typing" feature in "System->Preferences->Mouse->Touchpad" will  fix the problem.

Apparently the system does not recognize that the user has deliberately  disabled the touchpad. And so it will reenable it when the user is "done  typing".


I Hope someone will find this useful :smile:
Try gpointing-device-settings  applet in Synaptic Package Manager. add it to your startup applications and have a choice at restart or bootup.

---

### Post by nsales1 on 2010-07-23
This was tremendously helpful! I wanted a way to turn off when the mouse is plugged in, but this is an excellent solution!

---

### Post by texla on 2010-09-05
You have to unclick the "disable touchpad while typing" option in the mouse settings for this fix or the program "touchfreeze" to work

I prefer touchfreeze because it has a nice icon in the corner that makes it easy to disable or enable the touchpad and you can autostart it so it's ready to go.   It's in synaptic.  

It is strange that typing-disable functions don't really  fix the cursor from jumping around a lot when typing for me (in windows either).  Would be nice to at least see it disable whenever an external mouse is added for ubuntu.  But touchfreeze does the job for me for now....

---

### Post by Tootler on 2010-10-23
> **bobcollard said:**
> Try gpointing-device-settings  applet in Synaptic Package Manager. add it to your startup applications and have a choice at restart or bootup.

I tried both this and the gsynaptics applet (they are mutually exclusive) and in both cases the touchpad would re-enabled itself after a time. 

Eventually I found that you needed to disable the touch pad in the gconf editor

Select Alt+F2 or open a terminal and Type

```
gconf-editor
```

This will open the gconf editor. In the left panel, open up desktop>gnome>peripherals>touchpad. In the right panel uncheck the entry "touchpad_enabled". This will disable the touchpad for you. At least it did for me. 

I suspect you may not need gsynaptics or gpointing-device-settings, but I have left them installed just in case.

---

### Post by Marco7 on 2010-11-15
Thank you!

I love these counter intuitive little pieces of computer logic.

---

