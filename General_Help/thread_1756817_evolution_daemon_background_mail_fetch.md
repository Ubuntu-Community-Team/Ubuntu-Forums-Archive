---
title: "evolution daemon background mail fetch?"
date: 2011-05-12
forum: General Help
---

### Post by boblizar on 2011-05-12
is there a way to do this so i can set mail notification to alert me when evolution finds a new piece of email from syncing at my sync rate defined in evolution and not have evolution be in my face @ boot, and not have to have evolution open to keep mail notification from freaking out?

---

### Post by trozamon on 2011-05-12
What I have done is use a daemon called devilspie. What it does it force evolution to be in a different workspace when it starts. Open software center and download gDevilsPie.

Then, just run gDevilsPie, check the checkbox saying, "Start devilspie automatically at boot" and then create and appropriate rule for evolution. I have mine set up so that any window name containg "Evolution" has the following actions defined: maximize, set_viewport 2.

If you need any clearing up of these directions, just ask.

---

### Post by boblizar on 2011-05-12
"and not have to have evolution open to keep mail notification from freaking out?"  for now my solution is to point mail notification directly at gmail and use evolution as the mail client.  im kinda :confused: about empathy not doing the function of mail notification.

---

