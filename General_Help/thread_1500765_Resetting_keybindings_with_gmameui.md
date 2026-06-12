---
title: "Resetting keybindings with gmameui"
date: 2010-06-03
forum: General Help
---

### Post by warnec on 2010-06-03
Hi. I enjoying playing older arcade games, mostly Metal Slug series. I have an xbox wireless controller which I used to play with. 

There is one problem, though - when changing the key bindings, by mistake I cleared the field which said "UI Enter", so there is no key bound to it! I cannot enter any menus or fields to bind any key. I am stuck. I tried reinstalling gmameui and sdlmame, but to no avail. The key configuration didn't get reset :mad: 

Even stranger, when running sdlmame through /usr/bin, the key configuration is the default one - but I'd prefer to play with a GUI. 


Do you have any ideas how to reset the gmameui's bindings?

EDIT:

I can't believe I haven't seen it before! I googled for 2 days, and then I lost my faith in finding the answer. I found it now in Google. Looks like it's just a matter of a right keyword.

Simply delete contents of ~/.config/mame/cfg. In my case, deleting "default.cfg" did the trick, because it is responsible for general MAME settings like UI.

---

### Post by koza linux on 2012-01-07
sir, how to configure control key on gmimeui ???

---

