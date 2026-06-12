---
title: "Customising appearance of desktop pulldown menus"
date: 2010-08-07
forum: General Help
---

### Post by gabriella on 2010-08-07
Hi,

It's possible I've missed this, if so my apologies, but I dont think so.

System>Preferences>Appearance allows you to customise aspects of the desktop theme. The problem I'm having is customising the pull down menu colors in the default theme for Lucid. 

To give an example. If I pull down the Firefox bookmarks menu, then click on a folder within it, and then a sub-folder again, the contents of the sub-folder are the same color as the background of the original folder and a bit difficult to read. I'd like to set the background color of the sub-folder contents to a colour of its own. How do i do that?

Thanks

---

### Post by gabriella on 2010-08-08
anyone?

---

### Post by lovinglinux on 2010-08-08
See [http://www.mozilla.org/unix/customizing.html](http://www.mozilla.org/unix/customizing.html)

---

### Post by gabriella on 2010-08-09
> **lovinglinux said:**
> See [http://www.mozilla.org/unix/customizing.html](http://www.mozilla.org/unix/customizing.html)

Thanks for that. Not sure if it quite gives me what I'm looking for but looks like a start anyway

---

### Post by davemike on 2010-08-09
Lovinglinux.. the URL you posted will be useful for me as well..thanks a lot..I'm new to Ubuntu(Linux as well). Let it be a start.

---

### Post by pbrane on 2010-08-09
Theme files are found in **/usr/share/themes**, at least for GNOME. You can edit these text files, but I would recommend making copies and editing those. There is also a **~/.theme** folder in your home directory. You can create your own theme by copying one that you like and make the changes you want, saving it in your **~/.theme** directory. Then chose that theme in System->Preferences->Appearance.

In Lucid, can't remember in Karmic, there is a theme customize button in System->Preferences->Appearance and from there you can change *some* of the theme colors.

---

