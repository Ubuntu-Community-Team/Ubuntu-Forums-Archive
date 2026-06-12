---
title: "Mouse control modified by Sugar"
date: 2010-05-09
forum: General Help
---

### Post by HughJarse on 2010-05-09
Installed the Sugar emulator. After closing it down, it seems to have modified the mouse behaviour permanently - single click with the left (primary) button grabs instead of selecting.

After a reboot the behaviour is retained making it difficult to do anything. Tried using the web without left click?

Tried the mouse control but no settings there.

Presumably a setting / file has been modified somewhere?

I have a second user account with a working mouse. I guess if there was a way to copy the settings from this user it would work?

How do I do this?

---

### Post by P4man on 2010-05-09
that must be mildly annoying indeed :)
I have no idea what sugar changed, but perhaps trying copying this (hidden) folder from your new to your old account:

.gconf/desktop/gnome/accessibility/

after copying make sure you change the permissions so the old user is the owner.

---

### Post by HughJarse on 2010-05-09
Still not working. Any ideas how to reset this annoying behaviour?

---

### Post by P4man on 2010-05-09
you can try renaming the .gconf folder in your old users homefolder. You will lost all your gnome settings, but see if that helps.

---

### Post by HughJarse on 2010-05-10
Didn't try that but [found this thread]("https://bugs.launchpad.net/ubuntu/+source/sugar/+bug/479179")

Tried the System > Preferences > Window  and (removed super key)

That seems to have cured it!

---

### Post by BarakNaveh on 2010-05-29
Thanks many -- it saved me :)

---

