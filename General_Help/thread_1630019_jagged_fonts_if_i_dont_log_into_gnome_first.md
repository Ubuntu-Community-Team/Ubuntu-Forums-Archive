---
title: "jagged fonts if i dont log into gnome first"
date: 2010-11-24
forum: General Help
---

### Post by aeiah on 2010-11-24
if i start up my computer normally it boots into my gnome session, via GDM. I've been tinkering with openbox (which ive used for a few years on my netbook) and if i log out of my gnome session and select openbox from the GDM menu, everything is fine.

if i boot straight into openbox (via GDM but without first going into gnome), or if i go into openbox via a TTY/startx then fonts look like this:

[img]http://img44.imageshack.us/img44/6536/screenshotkd.png[/img]

so, there's something that gnome does which smooths out all of my fonts. as it stands, some fonts (eg, the window title in the screenshot) are fine whilst others have aliasing.

has anyone come across this before?

ubuntu 10.04

---

### Post by aeiah on 2010-11-24
nevermind im just an idiot. i had someone elses settings in my .Xdefaults which were causing problems. changed the offending area to:
```

Xft*dpi:                96
Xft*antialias:          true
Xft*hinting:            slight
Xft*rgba: 		rgb

```

it isnt quite perfect but it's where the problem lies

---

