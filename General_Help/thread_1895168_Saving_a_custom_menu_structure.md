---
title: "Saving a custom menu structure"
date: 2011-12-14
forum: General Help
---

### Post by millerthegorilla on 2011-12-14
Hi, I am wanting to do a clean install to ubuntu studio 11.10 without Unity.  I am using studio 10.04 at the moment, and have spent some time creating a menu structure that I am happy with so that all of my audio programs are easily accessible.

Is there a way of saving the existing menu structure so that I don't have to rebuild it.
Where is it's location?  I am a developer, so parsing xml, json or whatever structure it is to replace the program command locations won't be a problem.  I may even develop a gui to do it automatically, if I can.

Any help would be appreciated.

Thanks in advance.

:guitar:

---

### Post by lechien73 on 2011-12-14
Hi and welcome to the forums :)

The applications menu (and other menus) are stored between the following two locations:

```
/etc/xdg/menus
~/.config/menus

```
The menus at /etc/xdg/menus are global, whereas the other location reflects changes applicable to the local user. They're stored in xml format, and should be fairly self-explanatory when you look at them.

---

