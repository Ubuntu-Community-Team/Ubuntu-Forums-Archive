---
title: "gnome-panles missing"
date: 2010-10-31
forum: General Help
---

### Post by lemmy999 on 2010-10-31
Stupidly I followed  [this](http://www.omgubuntu.co.uk/2010/09/how-to-fully-replace-your-gnome-panels-with-awn/) guide to installing Awn- not noticing that the instructions for removing the panels would bork my system. I have tried the recommended fix
> If it doesn’t work for you, you can always go back by opening up a terminal (Ctrl + Alt + T) and lauching gconf-editor then changing the value above back to gnome-panel. Log out and back in again by using the command sudo service gdm restart in a terminal. but that didn't work. 

In the end I decided to re-install but I still have the same problem. Therefore the problem is somewhere in my config files in /home.

Any thoughts as to how I get this one sorted?

---

### Post by wojox on 2010-10-31
Run these two commands in the terminal

```
gconftool-2 --recursive-unset /apps/panel
killall gnome-panel
```

---

### Post by lemmy999 on 2010-10-31
Ah- thats the other problem- the changes I made also disabled alt-f2 so I can't get a terminal:(

---

### Post by wojox on 2010-10-31
What about Ctrl+Alt+F1 ?

---

### Post by Jechem on 2010-10-31
You could try these:
[http://ubuntuforums.org/showthread.php?t=1205741](http://ubuntuforums.org/showthread.php?t=1205741)
[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

---

### Post by lemmy999 on 2010-10-31
> What about Ctrl+Alt+F1 ?

Looks like that should work. I'm in the middle of an upgrade so I'll wait until that finishes and try your suggestion out.

---

### Post by lemmy999 on 2010-10-31
> killall gnome-panel

gives me```
gnome-panel: no process found
```

---

### Post by lemmy999 on 2010-10-31
Sorted!! I had to modify the gconf file in /home from "avant-window-manager" back to "gnome-panel"

Thanks for your suggestions.

---

