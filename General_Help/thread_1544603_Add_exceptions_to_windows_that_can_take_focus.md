---
title: "Add exceptions to windows that can take focus"
date: 2010-08-02
forum: General Help
---

### Post by cfalzone on 2010-08-02
Is there a way to prevent specific windows or applications from taking focus?

I'm using CoverGloobus and I have it at startup but I would like for that particular window (covergloobus.py) to not ever take focus.  The reason is purely aesthetic because I am trying the gnome-global-panel applet on my netbook and it is annoying to not have the desktop menu when I'm on the desktop.

---

### Post by TheWeakSleep on 2010-08-04
Are you using compiz? try the plugin "Window Rules" under window management. There is an option for no focus, maybe this would work?

EDIT: I tried it out, though if you're using a covergloobus theme with the controls on it, I'm not sure if you'll be able to use them if it's not focused, at least it didnt seem like i could (didnt try it with music playing..) heres what you have to do if you're using compiz. First of all, if you haven't already, install compizconfig settings manager
```
sudo apt-get install ccsm
```
after that go down to the very bottom of the screen, there should be a plugin called "window rules", click on it and you'll see the very last option is called "no focus"
in the box, just put "name=covergloobus.py" and that should keep it from taking focus.

---

### Post by cfalzone on 2010-08-04
It worked!  Thanks for the careful steps... I didn't know that compiz was so functional as it is beautiful.

---

