---
title: "Automatic window placement with Compiz"
date: 2010-03-03
forum: General Help
---

### Post by scoon1329 on 2010-03-03
I'm having trouble automatically placing a window to a specific workspace on startup. I found [this discussion]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=969424") and it's pointed me in the right direction.

Problem is, the window I want to create a placement rule for is a Google Chrome application shortcut for my Gmail account. I.e. ```
/opt/google/chrome/google-chrome --app="<URL HERE>"
```.

I can create a rule to move all Google Chrome windows to a specific workspace by using the 'Place Windows' section of the compiz config settings manager, but not just this application shortcut. I've tried adding a rule to only move chrome windows with title=Google Mail, but this doesn't work as when the window first loads it is Untitled, as are all google chrome windows. I'm guessing compiz only checks a window against rules when the window loads.

Any suggestions would be much appreciated.

/Joe Bell

---

