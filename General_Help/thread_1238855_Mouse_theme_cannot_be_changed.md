---
title: "Mouse theme cannot be changed"
date: 2009-08-12
forum: General Help
---

### Post by sigixv on 2009-08-12
i installed a GTK theme and apparently it came preloaded with a mouse theme (could have been a deb package too, don't remember).

Anyways, it changed my mouse theme and i'm not able to change it back to anything else if desktop effects are enabled. When compiz is disabled, it changes without any problems. Compiz enabled it "keeps" some elements of the previous mouse theme: the idle icon on desktop remains the one of the recently installed theme. Other cursors show fine (selecting, resize busy,...) and also inside firefox is fine. As already said, with desktop effects disabled, the full theme shows correctly.
Changing or installing a new GTK or mouse theme does not affect anything, the idle icon remains the same...

Any ideas?

*EDIT: I'm not sure anymore that its compiz related. I disabled desktop effects, set mouse theme to default, rebooted. During log in the cursor showed the recently installed "standby-cursor", even though after login it went back to the cursor theme set in preferences...

---

### Post by fooman on 2009-08-12
open your home folder and in the toolbar,  click view....put a check next to "show hidden files"

scroll down and open the .icons folder.

see if there is a folder in there with the name of the offending cursor theme.

if its there,  right click on it and choose "move to trash".

see if that fixes things (may have to log out and back in again to see the change).

---

### Post by sigixv on 2009-08-12
the folder contains only the iconthemes i installed myself.
I just noticed that my "human" GTK theme has disappeared too...

Presuming that it was a .deb installer package, i think it simply hijacked my pc... (or at least accidentally messed it up)

Thanks for the reply

---

