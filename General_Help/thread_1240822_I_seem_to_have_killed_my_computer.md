---
title: "I seem to have killed my computer"
date: 2009-08-15
forum: General Help
---

### Post by noffle on 2009-08-15
I was fiddling around with trying to get xmonad to work in the gnome configuration thing and now nothing works. From memory I think I changed the default window manager to xmonad and also included xmonad in startup. When I start up I get all the panels but I can't do anything to change it back, and when I open a console with Alt+Shift+Return it opens behind the panel. If I start in fail-safe gnome it starts without xmonad, but seeing as I changed the default window manager it doesn't open anything else. I think I may have to do a reinstall. Is there anything else I could do? And secondly, is there an easier tiled windows application than xmonad? Thank you.

---

### Post by sigixv on 2009-08-15
Try to log in in text mode. There you should be able to either remove or disable xmonad and reconfigure metacity. Or you can reinstall the gdm as a whole.

---

### Post by wfp on 2009-08-15
If you installed through synaptic just boot into safe mode and remove it. Edit boot into ubuntu recoverey mode.

---

### Post by noffle on 2009-08-15
Hmm, the reinstall gdm option looked like the easiest so I went
sudo apt-get remove ubuntu-desktop
sudo apt-get remove gdm
And then
sudo apt-get install ubuntu-desktop (which included gdm)
But now when I boot gnome, even in failsafe, I get a black screen with my cursor.

---

### Post by wojox on 2009-08-15
Blank screen as in I don't even have the ability to log in?

---

### Post by noffle on 2009-08-15
Oh, sorry, it logs on and then the blank screen.

Edit: Now I uninstalled xmonad too and the black screen is gone; but I don't have the toolbar things.

---

### Post by wojox on 2009-08-15
So you have a GUI desktop just no panels?

---

### Post by noffle on 2009-08-15
Yes, I got the GUI back. There are two vertical black lines going down the sides and one going horizontally across the top. And there are no panels.

---

### Post by wojox on 2009-08-15
Ok

CTRL + ALT + F1 gets you a terminal then:

```
sudo rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

Get back to your GUI desktop by hitting CTRL + ALT + F7

---

### Post by noffle on 2009-08-15
Many thank yous kind sir.

---

### Post by wojox on 2009-08-15
Your Welcome :P

---

