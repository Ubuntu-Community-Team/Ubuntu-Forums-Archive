---
title: "Icons in Firefox's menus have gone missing."
date: 2010-05-05
forum: General Help
---

### Post by qorron on 2010-05-05
ubuntu 10.04, ff 3.6.3 with some addons installed.

how to reproduce:
open firefox, download and install some plugins/addons that generate menu entries with an icon in front of them.
e.g. "downthemall" (down them all)
restart firefox
open a webpage
rightclick somewhere in an empty space of the webpage
you will see new menu entries:
"DownThemAll!..."
"dTa OneClick!..."
both of them have no icons in front of them.

back in 8.04 and 8.10 with ff 3.0
and on windows XP with ff 3.6.3
there are icons in front of these menu items.
looks much like this:
[http://www.downthemall.net/images/ss/ubuntu/context-sensitive-menus.png](http://www.downthemall.net/images/ss/ubuntu/context-sensitive-menus.png)

there is however space for these icons in the menu.
and I can see icons in the bookmark and history menus. (web page favicons)

these icons improve the usability greatly because they offer a visual guide to the menu not only to the item they belong to but also to other items because I know that the item I want is e.g. one above the green triangle.

I have a slightly impaired vision so this a far greater issue to me than you well sighted folks may think. Just put on some glasses with lots of fingerprints on them and you will see the difference.

---

### Post by WorMzy on 2010-05-05
Run gconf-editor and browse to: /Desktop/Gnome/Interface/, in there set menus_have_icons to true, then restart Firefox. :)

---

### Post by qorron on 2010-05-05
thank you very much, worked like a charm.

so, and how do I mark this thread as [solved]?

never mind.. just found it in "thread tools"

---

