---
title: "Mouse grabs the wrong window"
date: 2010-07-07
forum: General Help
---

### Post by rocketnewton on 2010-07-07
I'm running Ubuntu 10.04 with dual monitors. A lot of times I will go to one monitor and grab a window to drag it some place else but the previously selected window will gain focus instead. Is this a known bug? Is there a setting I can tweak?

---

### Post by warfacegod on 2010-07-07
If you are running Compiz, try adjusting or disabling the Raise/Focus behaviors.

---

### Post by rocketnewton on 2010-07-07
Am I still running compiz if I have visual effects set to "None"?

---

### Post by warfacegod on 2010-07-07
> **rocketnewton said:**
> Am I still running compiz if I have visual effects set to "None"?

For the most part, no. But some of it's values *may* still be in effect because Ubuntu also has those behaviors.

---

### Post by rocketnewton on 2010-07-13
I changed the following: 
Auto-Raise delay = 200 (was 500)
Focus Prevention Level = off (was Low)

It's better, but still, sometimes the mouse grabs the wrong window or like just now, somehow I moved a window to the other screen without meaning to just by bringing my mouse over... 

Where is the setting to prevent a full screen'ed window from being moved? It seems like those are always the windows that act up.

---

### Post by warfacegod on 2010-07-14
> **rocketnewton said:**
> I changed the following: 
Auto-Raise delay = 200 (was 500)
Focus Prevention Level = off (was Low)

It's better, but still, sometimes the mouse grabs the wrong window or like just now, somehow I moved a window to the other screen without meaning to just by bringing my mouse over... 

Where is the setting to prevent a full screen'ed window from being moved? It seems like those are always the windows that act up.

That's called Edge Flipping. The setting for that should be in Desktop Wall. Try disabling flipping.

---

### Post by svaens on 2010-08-05
I have this problem as well; 

Same situation. dual screen. Don't have compiz (I have an ATI card). 

Not only that, I could have sworn just then, I clicked on the 'x' button (close button) of one window, and other wanted to close instead!

I am fairly certain of this because I clicked the close button on a window on my left-hand screen (a gedit window) 
but amazingly, up popped the close confirmation for eclipse, which was on my right-hand screen.

---

### Post by czz7661 on 2010-08-05
I believe it's a metacity issue. On the fedora bug reports I noticed that lots of distros were having this issue. There is a metacity update that was said to fix the issue. I don't think ubuntu has updated this yet.

---

### Post by svaens on 2010-08-05
I figured out how to consistently reproduce this; and so created a bug report:


[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/613775](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/613775)

---

