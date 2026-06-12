---
title: "Delete Panel"
date: 2010-11-15
forum: General Help
---

### Post by TNT1 on 2010-11-15
Why would the "delete this panel" option be greyed out? I really want to delete it.

---

### Post by a-user on 2010-11-15
because it's the main one. you have to remove gnome panel (the program) to get rid of it. search for this. it has been discussed several times how to do it.

---

### Post by TNT1 on 2010-11-15
> **a-user said:**
> because it's the main one. you have to remove gnome panel (the program) to get rid of it. search for this. it has been discussed several times how to do it.

Yeah, I did search, and couldn't fine anything that works.

---

### Post by a-user on 2010-11-15
just the first hit on google with "remove gnome panal" (you know google?):
[http://ubuntuforums.org/showthread.php?t=405721](http://ubuntuforums.org/showthread.php?t=405721)

the first 3 posts or so are not usefull. but read till the end of the page.

---

### Post by Verbeck on 2010-11-15
open gconf-editor then navigate to desktop>gnome>session>required_components >panel and replace &#8220;gnome-panel&#8221; with an empty space

should be able able to delete it now it think

---

### Post by TNT1 on 2010-11-15
> **a-user said:**
> just the first hit on google with "remove gnome panal" (you know google?):
[http://ubuntuforums.org/showthread.php?t=405721](http://ubuntuforums.org/showthread.php?t=405721)

the first 3 posts or so are not usefull. but read till the end of the page.

Yeah, I used the wrong words, as in delete not remove. Anyway, thanks for the sarcasm and the help.

---

### Post by TNT1 on 2010-11-15
> **Verbeck said:**
> open gconf-editor then navigate to desktop>gnome>session>required_components >panel and replace “gnome-panel” with an empty space

should be able able to delete it now it think

Yeah, one of the many answers I found here... My "panel" entry is not writable, and has no "gnome-panel" anyway... for panel, my entry is " that's it, just " that I can't edit.

---

### Post by a-user on 2010-11-15
@verbeck: the better way to do this is to remove gnome-panel from the session. e.g.:
in terminal: gnome-session-remove gnome-panel
or > 
You can disable the gnome panel by going to Sessions-->Current  Session and remove gnome panel from the list of running applications.

Then go to Session Options and click on the Remember button..

@TNT1: if you use "delete gnome panel" on google you stil get the same first hit that i found with "remove". don't take my sarcasm to serious, but yes, it was intentional ;)

---

