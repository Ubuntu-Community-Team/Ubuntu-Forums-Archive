---
title: "Need to change  &quot;xorg.conf&quot; settings, How? ..."
date: 2012-04-26
forum: General Help
---

### Post by rreyes3713 on 2012-04-26
I need to make some changes on xorg.conf file. My Nvidia GeForce FxGe5200 video card is not running at optimum peformance.

During an "Update Manager", a Nvidia update was installed[?] so the setting of the xorg.conf file was changed. I do have a copy of the original xorg.conf setting that did work for my Nvidia GeForce FxGe5200 card. I need to make those changes.

Note, yes this is an obsolete video card and yes, I'm running on 2004 Dell laptop Ubuntu 10.04.

So how do I edit the xorg.conf file with gedit? I want to use gedit Text Editor since I'm rust using vi editor.

So at the terminal, what do I type?


%sudo gedit pathname/xorg.conf     ?

Thanks!

---

### Post by wojox on 2012-04-26
You would use:
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by rreyes3713 on 2012-04-26
Thanks, wish me luck on the 'new' settings.

---

