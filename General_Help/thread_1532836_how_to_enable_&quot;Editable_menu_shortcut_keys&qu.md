---
title: "how to enable &quot;Editable menu shortcut keys&quot;"
date: 2010-07-17
forum: General Help
---

### Post by HamletDRC on 2010-07-17
I am reading the book Ubuntu Kung Fu and it says you can enable "Editable menu shortcut keys" and then hover over menu items and create shortcuts for them. 

The book's description of how to enable this feature is no longer correct in Lucid. How do I enable this feature?

---

### Post by edemeulle on 2010-08-10
The gnome folks decided to remove the tab. See [https://bugzilla.gnome.org/show_bug.cgi?id=592756](https://bugzilla.gnome.org/show_bug.cgi?id=592756)

Run gconf-editor from the terminal and go to /desktop/gnome/interface/ and check can_change_accels

-ED-

---

