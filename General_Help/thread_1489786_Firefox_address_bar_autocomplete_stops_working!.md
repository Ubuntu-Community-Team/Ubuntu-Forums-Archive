---
title: "Firefox address bar autocomplete stops working!"
date: 2010-05-21
forum: General Help
---

### Post by meldroc on 2010-05-21
Just from searching around, this seems to be a bug that occurs after waking up from the screensaver.

After that happens, the autocomplete feature of Firefox's address "awesome bar" stops working, which forces me to type URLs in full, which is obnoxious.  I'm very used to hitting Ctrl-T to start a new tab, typing two letters, watching the suggestions come up, then arrowing to my choice, with a total of three or four keystrokes needed in total.

The only way to get autocomplete working again once it stops working is to kill and restart Firefox.

Anyone have a solution to this problem?

---

### Post by hvbakel on 2010-05-21
You're probably suffering from this bug (like me):

[https://bugs.launchpad.net/firefox/+bug/438868](https://bugs.launchpad.net/firefox/+bug/438868)

Apparently this is caused by compiz drawing the drop-down menu behind the main firefox window. There are a few tricks mentioned in the comments to the bug that can be used to get the autocomplete working again without having to restart firefox.

---

### Post by impact on 2010-05-21
Just minimize and then maximize Firefox or Alt-tab to another window and back. No need to kill the application.

---

### Post by meldroc on 2010-05-24
Alt-tabbing or minimizing/restoring seems to work - causes Compiz to reset its widget-stacking and works as a workaround!

Thanks!

---

