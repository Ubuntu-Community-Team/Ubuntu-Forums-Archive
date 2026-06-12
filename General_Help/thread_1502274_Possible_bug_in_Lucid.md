---
title: "Possible bug in Lucid?"
date: 2010-06-05
forum: General Help
---

### Post by blur xc on 2010-06-05
I've noticed this happening for a bit now, pretty consistently.  If I have an app running in full screen mode when the screen saver activates- and then I come back and start using the computer again, the app that was in full screen no longer accepts keyboard inputs.  Sometimes taking it out of full screen fixes it, but just 5 mins ago I had to close and re-open the app to get it to accept keyboard inputs again.  Has anyone else noticed this?

I first noticed it w/ VBox, as I run Vista when I need to in full screen mode.  I don't like how seamless mode works w/ Gnome... But I thought this was a VBox problem, but I don't run a lot of programs in full screen mode that often.  So, today it was Bibble. I had it running full screen, and when I returned to the pc to continue working, keyboard commands did nothing.

Is this worthy of filing a bug report?

Thanks,
BM

---

### Post by sanderd17 on 2010-06-05
I sometimes have this with skype. I don't put the skype chat window in full screen but I always put it on top of other screens. I thought it was a skype problem, aperantly not.

I almost always have firefox in full screen and coming out of hybernate mode doesn't affect firefox.

So I don't know what could be causing the problem.

---

### Post by Barafu Albino Cheetah on 2010-06-05
What screensaver subsystem are you both using? The all-buggy gnome screensaver, or normal xsaver? The first one is default. 
To switch, remove gnome-screensaver related packages, install xscreensaver, add ```
xscreensaver
```
to autorun applications.

---

### Post by blur xc on 2010-06-07
> **Barafu Albino Cheetah said:**
> What screensaver subsystem are you both using? The all-buggy gnome screensaver, or normal xsaver? The first one is default. 
To switch, remove gnome-screensaver related packages, install xscreensaver, add ```
xscreensaver
```to autorun applications.

Interesting- I'll check into that...

Thanks,
BM

---

