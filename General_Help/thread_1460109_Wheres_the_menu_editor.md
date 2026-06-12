---
title: "Wheres the menu editor?"
date: 2010-04-22
forum: General Help
---

### Post by HHx66 on 2010-04-22
Wheres the menu editor at on Xubuntu 9.10? (With xfce 4.6.1)? I can't seem to find it.

---

### Post by SnickerSnack on 2010-04-22
Use the command line to search for menu.xml.

$ locate menu.xml

I used xfce a bit yesterday, and I think I right-clicked on the menu button, and I was able to find an option to either use the 'default' menu or a custom menu (pointed at menu.xml) by default.

If you do a google search for 'xfce menu editor', you'll find at least one program (on sourceforge, I think) that has a decent gui for editing the right-click menu, which is separate from the main menu.

---

### Post by Brandon Williams on 2010-04-22
Unfortunately, the menu editor for the version of XFCE in 9.04 and later is called "the command line and a text editor". [Here are some details.](http://ubuntuforums.org/showpost.php?p=7240572&postcount=5)

---

### Post by HHx66 on 2010-04-22
well I don't have a problem with that, a bit annoying, but worth it for the speed of xfce. Is there any news on if they're going to include on or make one soon for xfce?

---

### Post by Brandon Williams on 2010-04-22
They're doing a lot of work on menus for xfce-4.8 ([more info here](http://wiki.xfce.org/releng/4.8/roadmap/garcon)). It looks like they see creating the necessary menu editing APIs (not to mention a real menu editor) as optional for 4.8, and no work appears to have been done on it yet. I would not expect a functional menu item to appear any time soon.

---

### Post by HHx66 on 2010-04-23
Thats odd, but oh well. I can deal with it for speed.

---

