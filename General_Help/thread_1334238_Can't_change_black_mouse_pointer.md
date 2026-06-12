---
title: "Can't change black mouse pointer"
date: 2009-11-22
forum: General Help
---

### Post by MacUntu on 2009-11-22
I don't know what caused it but my mouse pointer is black, even if set the pointer theme to "Human" (or any other pointer set) in the Appearance Preferences.

It's also black for a new test user so it's no setting in the home directory. Any ideas how I can get back to normal?

---

### Post by kerry_s on 2009-11-22
you got to click customize & pointer. see pics

---

### Post by MacUntu on 2009-11-22
Thanks, but I already did that. Selecting the Human theme alone should set back the pointer theme but it doesn't.

---

### Post by kerry_s on 2009-11-22
try running: **sudo update-alternatives --config x-cursor-theme**

might have to log out & back in to take effect.

---

### Post by Dennis N on 2009-11-22
If you start customizing themes, the pointer setting may revert to the default. You have to redo the setting.

---

### Post by MacUntu on 2009-11-22
> **kerry_s said:**
> try running: **sudo update-alternatives --config x-cursor-theme**

might have to log out & back in to take effect.

Thanks for pointing me there - purged and reinstalled the DMZ cursors and now the cursor is white but I still cannot change the theme via Appearance Preferences.

```
There are 6 choices for the alternative x-cursor-theme (providing /usr/share/icons/default/index.theme).

  Selection    Path                                     Priority   Status
------------------------------------------------------------
* 0            /usr/share/icons/DMZ-White/cursor.theme   50        auto mode
  1            /etc/X11/cursors/core.theme               30        manual mode
  2            /etc/X11/cursors/handhelds.theme          20        manual mode
  3            /etc/X11/cursors/redglass.theme           20        manual mode
  4            /etc/X11/cursors/whiteglass.theme         20        manual mode
  5            /usr/share/icons/DMZ-Black/cursor.theme   30        manual mode
  6            /usr/share/icons/DMZ-White/cursor.theme   50        manual mode
```

Maybe that's a Lucid thingy, will test it later.

**Edit:** Nope, works on a second Lucid machine with the same output as above.

---

### Post by kerry_s on 2009-11-22
> Maybe that's a Lucid thingy, will test it later. 

problems are to be expected. ;)

you can also manually edit **/usr/share/icons/default/index.theme** to set a default theme. i like to set it to the same as i'm using on the desktop, so i can have the same cursor on the login screen.

---

### Post by MacUntu on 2009-11-22
Seems I now can change themes, I just need to restart the session (as opposed to the second system).

> **kerry_s said:**
> problems are to be expected. ;)

"The system formerly known as Karmic Koala formerly known as Jaunty Jackalope formerly known as Intrepid Ibex formerly known as Hardy Heron formerly known as Gutsy Gibbon" - maybe I just should do a reinstall. :D

**Edit:** Seems to be influenced by Compiz. If I turn it off, theme changes apply instantly (the other system has Compiz turned off), while it takes a re-login with Compiz enabled.

---

### Post by MacUntu on 2009-11-22
Well, case closed (kinda): [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/356309](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/356309)

---

