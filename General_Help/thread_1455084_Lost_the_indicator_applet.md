---
title: "Lost the indicator applet"
date: 2010-04-15
forum: General Help
---

### Post by davepoth on 2010-04-15
Not quite sure how this happened. I upgraded from Jaunty to Karmic earlier in the week, in preparation to go for lucid when it goes gold, but when I did so, the button in the top right hand corner, which has the shutdown options on it, as well as my user name, disappeared. The options are now at the bottom of the system menu.

I went into the panel options, and attempted to add the indicator-session applet back to the menu but it didn't do anything. I tried reinstalling the indicator-applet packages but it didn't make any difference. 

Being a rash kind of person I tried upgrading to Lucid Beta 2 to see if it would help. It made no difference at all. Anyone got any ideas?

---

### Post by drs305 on 2010-04-15
If you didn't have many customizations to your panels (or if you did but don't mind losing them) you can rename your $HOME/.gconf/apps/panel folder. Then log out and log back in. A new "panel" folder will be created with the default settings. If it's just the panel settings, and not the governing apps, that are a problem, the default panel will be restored.

If you don't like it, remove it and rename the old folder back to "panel".

---

### Post by davepoth on 2010-04-15
Well that got me back to the default, but the default doesn't have the button in it. Somewhat flummoxed.

-edit-

Apport just popped up; indicator-applet threw an assert.

gnome-panel ../../src/xcb_io.c:385:_XallocID: Assertion 'ret !=inval_id' failed.

---

### Post by davepoth on 2010-04-15
Now on Launchpad.

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/564090](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/564090)

---

