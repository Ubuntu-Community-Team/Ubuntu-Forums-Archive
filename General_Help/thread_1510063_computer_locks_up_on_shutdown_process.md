---
title: "computer locks up on shutdown process"
date: 2010-06-15
forum: General Help
---

### Post by rifak on 2010-06-15
hey everyone,
so i just bought a new Sony Vaio laptop and things are seeming to run great. However, there is one issue: when i go to restart or shutdown the computer, the graphical interface goes away like it should, it goes to CLI and does it's shutdown routine....the problem occurs about 2 seconds into the routine, when it just stops. it doesnt shutdown or restart, but stays in the CLI with a blinking cursor. if i allow it to set for a couple of minutes, a message pops up that says something like this, "BUG: soft lock up CPU0 CPU1 stuck, blah blah". any ideas on what this is or what is causing this? the laptop has the i5 processor in it, just in case that matters. hope someone can help.

---

### Post by xsandz on 2010-06-15
Have u installed the Ubuntu 10.04 Lucid Lynx  Intelx86 or AMD64 version? As u r using i5 processor i reckon Intel-x86 may not work properly and your prob seems to me something related to relinquishing hardware prob and that is very much architecture dependent prob

---

### Post by philinux on 2010-06-15
> **ego-sum-deus said:**
> hey everyone,
so i just bought a new Sony Vaio laptop and things are seeming to run great. However, there is one issue: when i go to restart or shutdown the computer, the graphical interface goes away like it should, it goes to CLI and does it's shutdown routine....the problem occurs about 2 seconds into the routine, when it just stops. it doesnt shutdown or restart, but stays in the CLI with a blinking cursor. if i allow it to set for a couple of minutes, a message pops up that says something like this, "BUG: soft lock up CPU0 CPU1 stuck, blah blah". any ideas on what this is or what is causing this? the laptop has the i5 processor in it, just in case that matters. hope someone can help.

Have you done an update since installing?

System>admin>update manager. Click the check button. 

Also see if logging off then shutdown works.

---

### Post by rifak on 2010-06-15
i have done all the updates, and keep up with them. as for logging off before hand, i will start doing that and keeping tabs on whether or not or how often the lock-up occurs. also, what do you think about using 64bit instead of 32bit? will that be more stable on the i5 processor?

---

### Post by cuberts on 2010-06-15
> **ego-sum-deus said:**
> hey everyone,
so i just bought a new Sony Vaio laptop and things are seeming to run great. However, there is one issue: when i go to restart or shutdown the computer, the graphical interface goes away like it should, it goes to CLI and does it's shutdown routine....the problem occurs about 2 seconds into the routine, when it just stops. it doesnt shutdown or restart, but stays in the CLI with a blinking cursor. if i allow it to set for a couple of minutes, a message pops up that says something like this, "BUG: soft lock up CPU0 CPU1 stuck, blah blah". any ideas on what this is or what is causing this? the laptop has the i5 processor in it, just in case that matters. hope someone can help.I will ask you two things.
1. Does it say something about a broken pipeline?
2. What else does it say something about killing a bug?

The easiest way would to just let it do it, and then restart it by doing Ctrl+ALT+Del.
i hope that this will help.

---

### Post by rifak on 2010-06-15
> **cuberts said:**
> I will ask you two things.
1. Does it say something about a broken pipeline?
2. What else does it say something about killing a bug?

The easiest way would to just let it do it, and then restart it by doing Ctrl+ALT+Del.
i hope that this will help.

no, it doesn't say anything about a pipeline. also, i dont think it says anything about killing a bug. finally, i tried to do ctrl+alt+del but it doesnt allow me to do anything...i think this is because when i try to type anything, it is not registering my keyboard (probably because it's going through the shutdown sequence).

---

### Post by rifak on 2010-06-16
so i installed 64bit 10.04 instead, and the problem seems to have went away. i also am getting some smoother start-up and shutdown processes (with regards to graphics).

---

