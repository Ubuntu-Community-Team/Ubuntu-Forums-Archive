---
title: "Re: Oneiric compiz problem and ccsm"
date: 2011-10-16
forum: General Help
---

### Post by clegends on 2011-10-16
Found a bug with compiz-fusion & ccsm. If I set the scale & expo plugins to be activated by hitting the edge of the screen with my mouse cursor (top right edge and bottom right edge), then on the next login or reboot I need to enable them again. They have either been disabled, or don't work properly.

I have yet to find a good workaround,though currently I can open up ccsm on login and change the settings again. Other settings seem to be fine. Anyone come up with something better?

---

### Post by fantab on 2011-10-16
> **clegends said:**
> Found a bug with compiz-fusion & ccsm. If I set the scale & expo plugins to be activated by hitting the edge of the screen with my mouse cursor (top right edge and bottom right edge), then on the next login or reboot I need to enable them again. They have either been disabled, or don't work properly.

I have yet to find a good workaround,though currently I can open up ccsm on login and change the settings again. Other settings seem to be fine. Anyone come up with something better?

Yes, I am also facing the same problem with Expo edge, and looking for a workaround.

---

### Post by DMJ on 2011-10-17
This bug has been reported and it looks there's fix available in the proposed repos. Hopefully it will be in the stable repos soon.

The easiest way to fix it, without having to reset it in CCSM, is to do an ALT-F2 and then unity --replace. I've had the same problem with expo edge for the scale plugin as well, but this fixes it, albeit temporarily. 

Ever since Unity came out Canonical seems to have dealt with a lot of the conflicts it created by deactivating many of Compiz's best features. Reactivate at your own risk. It's ironic that by integrating the Ubuntu desktop with Compiz, Ubuntu has now become much less Compiz friendly. Hopefully this will change in the LTS release. I'd like to see a simple effects setting dialog as part of the default install.

---

