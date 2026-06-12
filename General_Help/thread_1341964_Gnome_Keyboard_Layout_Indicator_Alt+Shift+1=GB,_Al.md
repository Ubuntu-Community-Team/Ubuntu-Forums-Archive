---
title: "Gnome Keyboard Layout Indicator: Alt+Shift+1=GB, Alt+SHift+3=RU"
date: 2009-11-30
forum: General Help
---

### Post by dawnloader on 2009-11-30
I am running Ubuntu (9.10 Karmic) with 3 different keyboard layouts.

Having configured required layouts through "Keyboard Preferences" option of Keyboard Indicator applet I am trying to figure out how can I switch between layouts using dedicated key combination for each layout.

It looks like I can only toggle/cycle through configured layouts but I would like to use combinations like
**<Alt>+<Shift>+1**=en_GB
**<Alt>+<Shift>+2**=en_US
**<Alt>+<Shift>+3**=ru_RU
to specify the exact layout.

For the moment I have configured layout switch using above mentioned shortcuts through gconf-editor: apps/metacity/global_keybindings using
**setxkbmap gb** - to switch to English UK
**setxkbmap ru** - to switch to RU

However this method kills Keyboard Indicator applet settings and if I switch to RU then no other global shortcuts (ex: Ctrl+C, Ctrl+V) work until I switch back to US or GB layout.

So basically I am looking for an option to switch layouts using dedicated shortcut (1 per layout, no cycling or toggling) without killing global shortcuts if my current layout is not English.

Any Ideas?

---

### Post by dawnloader on 2009-12-07
bump.

---

### Post by dawnloader on 2009-12-16
anyone?

---

### Post by aleq on 2011-07-12
> **dawnloader said:**
> I am running Ubuntu (9.10 Karmic) with 3 different keyboard layouts.

Having configured required layouts through "Keyboard Preferences" option of Keyboard Indicator applet I am trying to figure out how can I switch between layouts using dedicated key combination for each layout.

It looks like I can only toggle/cycle through configured layouts but I would like to use combinations like
**<Alt>+<Shift>+1**=en_GB
**<Alt>+<Shift>+2**=en_US
**<Alt>+<Shift>+3**=ru_RU
to specify the exact layout.

For the moment I have configured layout switch using above mentioned shortcuts through gconf-editor: apps/metacity/global_keybindings using
**setxkbmap gb** - to switch to English UK
**setxkbmap ru** - to switch to RU

However this method kills Keyboard Indicator applet settings and if I switch to RU then no other global shortcuts (ex: Ctrl+C, Ctrl+V) work until I switch back to US or GB layout.

So basically I am looking for an option to switch layouts using dedicated shortcut (1 per layout, no cycling or toggling) without killing global shortcuts if my current layout is not English.

Any Ideas?

I've got a very similar problem. I'm running Ubuntu 11.04. I need to switch between RU, UA, US and FR in the way you have described. But I can't find a solution anywhere. Is it possible at all?
I would appreciate any help. Thanks in advance.

---

### Post by alexkvak on 2012-02-23
The same question. I try to use XBindKeys tomorrow

---

