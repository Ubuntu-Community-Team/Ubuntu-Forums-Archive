---
title: "How do I Open a Window in a Particular Workspace?"
date: 2010-05-09
forum: General Help
---

### Post by Penguin Guy on 2010-05-09
I want to run Evolution at starup, but want to place it out of the way on the opposite side of the Compiz cube. In KDE, you can run a command like this:
```
kstart --desktop 3 evolution
```

Is there an equivalent for GNOME/Compiz? I would preferably like to avoid using anything like Devilspie.

Thanks.

---

### Post by timgood on 2010-05-09
Install compizconfig-settings-manager:

```
sudo apt-get install compizconfig-settings-manager
```

Run it from System/Preferences

Go to Window Management/Place Windows and click on the Fixed Window Placement tab. Then, under Windows with fixed viewport click on New and then the + button. Start Evolution and then click grab - click on the Evolution window and then allocate a viewport (if you have 4 desktops and you want Evolution to start on desktop 4, then use 4 on the X viewport position). 

Apply, and Robert should be your father's brother. Hope this helps.

---

### Post by Penguin Guy on 2010-05-09
Thanks timgood, not exactly what I was looking for but it works okay. [SOLVED]

---

