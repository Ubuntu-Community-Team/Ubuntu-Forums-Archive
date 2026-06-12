---
title: "How to disable shortcut &quot;Alt + ` &quot; in compiz manager?"
date: 2012-04-27
forum: General Help
---

### Post by kwanylongy on 2012-04-27
Hi all,

I wish to disable keybinding "Alt + `", whose command name is "Switch windows of current application" according to the new Shortcut Hints, so it would not clash with my keybinding for Guake, but I could not find "Switch  windows of current application" in "Unity Plugin" of compiz manager, anyone know where I can find it?

Thanks in advance!

---

### Post by kwanylongy on 2012-04-28
anyone know? :confused:

---

### Post by xyzzyman on 2012-04-28
I personally use ` for guake, and just realized it's impossible to type `. lol

On topic though, you can't change it, not even in the shortcut editor in settings->keyboard->shortcuts. It's basically the same as this bug that alot of the unity key bindings can't be changed.

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/871931](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/871931)

---

### Post by kwanylongy on 2012-04-28
Cheers for the reply

OK, at least I know it can't be done. I will patiently wait for the bug fix by Canonical

---

### Post by mc4man on 2012-04-28
If you are referring to Alt+grave then you can reassign

(I always suggest creating a new user for exploring keyboard bindings, that way if things get borked ...

Anyway you need to unset the switch_group key in metacity thru gconf-editor.
shown unset in screenshot

Then you can use the binding in System Settings > keyboard >  Custom shortcuts

Edit - for reference  screen 2 shows the key before being unset

---

### Post by kwanylongy on 2012-04-28
Thanks for your reply mc4man! Your solution worked!

EDIT: Your solution worked at first, but 'Alt+Grave' went back to binding to 'Switch windows of current application' after restarting...

---

