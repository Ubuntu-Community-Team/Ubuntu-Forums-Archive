---
title: "Change evolution applet indicator to launch Thunderbird instead"
date: 2011-05-05
forum: General Help
---

### Post by Sir Rodness on 2011-05-05
Hello,

I was able to find information on how to add thunderbird to the indicator applet. However what I would prefer to do is change it so the mail indicator that is already there launches thunderbird instead of evolution. I could not find that in the forum if it exists. Does anyone know if that's possible?

---

### Post by Sir Rodness on 2011-05-06
After some more research figured it out what I needed to do.

Edit or add a file in usr/share/indicators/messages/applications/

I choose to edit a current file since I wanted evolution to not be there.

Opened file usr/share/indicators/messages/applications/evolution

Changed the line usr/share/applications/evolution.desktop to usr/share/applications/thunderbird.desktop (paths may vary depending on what you're trying to launch)

Save file and renamed it to thunderbird (remember I only renamed because I choose to edit the evolution file).

Logout or restart. ( I restarted, but I imagine logging out would give the same result)

The indicator dropdown should now only have what you want in it. 

Cheers.

---

