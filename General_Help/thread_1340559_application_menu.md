---
title: "application menu"
date: 2009-11-28
forum: General Help
---

### Post by spezticle on 2009-11-28
So i somehow broke my ubuntu's main menu. the menu that appears as the following: "Applications Places System" which is found on the top menu bar to the left. Clicking Applications returns nothing, and clicking 'main menu' found in system/preferences does nothing, as does right clicking on the menu itself and clicking 'edit menus'

is there a location in the system files or something somewhere where I can manually edit via text editor the menu entries, or is it complicated to just write my own menu?
or is there a way to reset the menu back to a default setting?

i've attached a few pictures of my menu problem. as you can see, 'places' and 'system' work properly, whereas 'applications' does not.


Thanks in advance,



Benjamin

---

### Post by SuaSwe on 2009-11-28
This might be of use:

[http://howtoxyz.blogspot.com/2008/07/applications-menu-not-working-in-ubuntu.html](http://howtoxyz.blogspot.com/2008/07/applications-menu-not-working-in-ubuntu.html)

In general, you could have a look at the settings in the config files under /home/<username>/.config/menus . :)

---

### Post by spezticle on 2009-11-28
> **SuaSwe said:**
> This might be of use:

[http://howtoxyz.blogspot.com/2008/07/applications-menu-not-working-in-ubuntu.html](http://howtoxyz.blogspot.com/2008/07/applications-menu-not-working-in-ubuntu.html)

In general, you could have a look at the settings in the config files under /home/<username>/.config/menus . :)

removing applications.menu in /home/<username>/.config/menus/ worked perfectly. Thank you very much

---

### Post by Rebelli0us on 2009-11-28
It's very easy to just add a new one, then delete the corrupted one.

---

