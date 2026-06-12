---
title: "UNR 9.04 and FF toolbar"
date: 2009-09-30
forum: General Help
---

### Post by mmmmna on 2009-09-30
Not on the machine (Eee PC 900A) right now, but the issue I'm seeking to resolve is that the favorites icon in the FF toolbar seems to return every time I restart FF. Before I close FF, I remove the icon, and surf for a bit; then I close Firefox. When restarting FF I have the icon once again. Referring to the little heart icon. I want it to obey my user preferences, to never reappear.

I searched for 'favorites', reviewed [http://ubuntuforums.org/showthread.php?t=1193567&highlight=firefox+toolbar](http://ubuntuforums.org/showthread.php?t=1193567&highlight=firefox+toolbar) but not sure if editing the rdf file will make the needed changes and am unsure of the proper syntax (I do not normally make random edits).

As a side comment about this matter: I use 2 Linux systems; this automatic toolbar restoration only occurs in the current Ubuntu UNR 9.04 version of Firefox; FF 3.5.3 in PCLinuxOS doesn't do this, no other version of FF I know of has ever done this. If this 'feature' is the brainchild of Ubuntu, be forewarned that I'm not happy with UI tweaks which work around normal user controls. So, my statement here is that when you add something to the original toolbar, please be sure to have it exactly follow the same rules as the icons beside it.

---

### Post by mmmmna on 2009-10-05
The "About Mozilla Firefox" dialog reads as follows:

"Firefox Version 3.0.14
Mozilla Firefox for Ubuntu canonical - 1.0"

Which is from UNR repos.

Any ideas how I can permanently un-edit the perpetually reappearing favorites icon out of my toolbar?

---

### Post by mikewhatever on 2009-10-05
Whatever it is you are trying to explain. I don't understand. I am on a Dell mini 10 with UNR right now, typing these very words, and till, no clue. Perhaps a screenshot will help.
Most forum members and visitors are simple Ubuntu users and not the developers, so that being forewarned will have little effect.

---

### Post by fluffman86 on 2009-10-05
Remove the webfav extension from tools > addons in firefox, and uninstall webfav from synaptic.  

Or:
sudo apt-get remove webfav

^ be careful that that doesn't go and uninstall a bunch of necessary stuff (like firefox) on you...

---

