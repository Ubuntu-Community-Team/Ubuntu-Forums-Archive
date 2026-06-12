---
title: "kde/konqueror - how to configure middle mouse button?"
date: 2006-03-15
forum: General Help
---

### Post by zi99y on 2006-03-15
There's loads of choice for keyboard shortcuts but I can't find how I can reconfigure the middle mouse button (mousewheel button) to close a tab in konqueror - just like firefox does. 

Anyone have any ideas on this?

ta

---

### Post by Jucato on 2006-03-15
From:[http://wiki.kdenews.org/tiki-print.php?page=Secret+Config+Settings#id762410]("http://wiki.kdenews.org/tiki-print.php?page=Secret+Config+Settings#id762410")

> Middle Click on Tab to Close in Konqueror (KDE 3.4)

Add the following text to your ~/.kde/share/config/konquerorrc and clicking on a tab with the middle mouse button will close it.
 
[FMSettings]
MouseMiddleClickClosesTab=true
 
That link has tons of KDE goodies. :D

---

### Post by zi99y on 2006-03-15
you beeee-outay!

thanks for the link, there's a few juicy nuggets there :D

---

### Post by Parkotron on 2006-03-16
Thanks Fenyx. This had been driving me nuts for a while. I'm kind of surprised it doesn't have a widget in the setting interface, though.

---

