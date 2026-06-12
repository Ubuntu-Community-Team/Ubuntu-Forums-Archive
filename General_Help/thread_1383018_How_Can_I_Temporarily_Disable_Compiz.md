---
title: "How Can I Temporarily Disable Compiz?"
date: 2010-01-16
forum: General Help
---

### Post by Joseph Schwenker on 2010-01-16
I have always been told, in fact, as often as I've been told to eat my vegetables, to disable Compiz before playing games in Ubuntu.  I found that after doing so and playing Half-Life 2: Episode 1, I had better performance, even with higher settings available.  I disabled Compiz by typing ```
metacity --replace
```

However, when I do this, and log out and log in again, Compiz is not enabled.  I have to either manually type ```
compiz --replace
``` or go into "Effects", click on normal, then disable the effects that I do not want.  The normal effect level keeps adding effects that I do not want!  This is very annoying, as either way, I still have to do some manual work.  Is there any way to get Compiz to start at startup even if it was disabled by metacity --replace in the previous session?  That is, besides putting compiz --replace into Startup Applications.  I want my computer to start with Compiz, not start with Metacity, then replace Metacity, then start Compiz.  I am using Ubuntu 9.04 32 bit.

---

### Post by Bonster on 2010-01-16
I use fusion-icon to toggle between compiz and metacity. Also save your current compiz settings profile then u can load it in again if it mess up.

---

### Post by hawthornso23 on 2010-01-17
My solution was to create custom keyboard shortcuts 
to switch between metacity and compiz.

ctl alt home  =>   compiz  --replace 
ctl alt end    =>   metacity --replace

You can do this in system-preferences-keyboard shortcuts

---

### Post by jwbrase on 2010-01-17
I use compiz-switch myself.

I find that on this machine I don't need to use it as much as I do on my desktop back home. On that machine certain programs would glitch bigtime under Compiz. Here it's just Skype, Open Office, and maybe one or two others, and they glitch in an entirely different way.

---

