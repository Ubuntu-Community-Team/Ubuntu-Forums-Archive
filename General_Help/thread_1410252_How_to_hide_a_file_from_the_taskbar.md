---
title: "How to hide a file from the taskbar?"
date: 2010-02-18
forum: General Help
---

### Post by six30two on 2010-02-18
I'm running Sun Virtualbox. I have it set up in seamless mode, and I have it always on top, so I have two function bars - one for Ubuntu, and one for XP (because I HAVE to have XP for school purposes, but frankly Ubuntu is better for everything).

Is it possible to hide the Virtualbox button on my Ubuntu function bar so that it's more seamless?

---

### Post by six30two on 2010-02-18
I thought a screenshot might help describe what I want to do.

---

### Post by six30two on 2010-02-23
Any help?

---

### Post by six30two on 2010-02-25
Could I please get some input on this? I'm not even sure it's possible, but I'd like to know.

---

### Post by PoHandle on 2010-02-25
You can use AllTray to place an icon in your systray rather than in your taskbar.
```
sudo apt-get install alltray
```

Then in a terminal
```
alltray
```

When the dialog appears, click on your running virtual machine.  It's a pain to do it each time, I know, but running ```
alltray VirtualBox
``` only puts the main VirtualBox OS chooser window in the tray.  Maybe someone else knows how help you hide it each time.

---

