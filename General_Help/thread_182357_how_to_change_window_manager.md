---
title: "how to change window manager"
date: 2006-05-25
forum: General Help
---

### Post by jeisma on 2006-05-25
hello!

how do you change window manager without logging off and selecting session.

while on gnome, change the setting (where is it?) so that when i restart window manager, the wm is now changed.


thanks!

joey

---

### Post by Ian Maxwell on 2006-05-25
Do you mean the window manager within gnome? When I wanted to switch to Sawfish, I switched easily enough via ```
killall metacity; sawfish &
```

If you want to switch to a different desktop manager like KDE, I'd guess you could do something similar, but I'm not sure enough to recommend it.

---

### Post by jeisma on 2006-05-25
hi!

i want to switch to fluxbox from gnome, so using your pattern i tried:

sudo killall gnome; fluxbox &

i get series of "Failed to read: session.xxxxx.xxxx.xxx"  errors... 

at the bottoms it says:

BScreen::BScreeen: an error occured while querying the X server.
               Another window manager already running on display :0.0
Error: couldn't find screens to manage.
Make sure you don't have another window manager running.

what do you think?


thanks!

joey

---

### Post by confused57 on 2006-05-25
I'm just guessing, but would  "sudo killall gdm..." work, or "sudo killall gnome-panel...".   I don't really know, I haven't tried this.

---

