---
title: "unity transparency broken"
date: 2012-06-05
forum: General Help
---

### Post by comradeluigi on 2012-06-05
for some reason the dash is no longer transparent and neither is the alt tab switcher

[img]http://img571.imageshack.us/img571/3721/screenshotfrom201206051.png[/img]

i recently installed some updates to unity

---

### Post by pieterk on 2012-06-08
I have exactly the same issue on one of the computers I am working with. It is an Asus eee pc. The other computer behaves normally. I hear other people having all kinds of trouble with transparency etc.
I can't understand Canonical releasing a new version of Unity that brings so much trouble only two weeks before the release of Precise Pangolin - the LTS. 
To be honest I think this was a ridiculous move.

---

### Post by Aearenda on 2012-06-08
I have seen this too. I suspect it is a consequence of playing with the launcher colour settings in MyUnity or a similar tool, but I have no confirmation of that yet. Setting the 'background colour' to default in the experimental tab of the Unity CCSM plugin seems to have fixed it for me.

Further observations - if you log out and log in again, things go back to normal until the next reboot. Having reset the default colour in the Unity plugin for CCSM, changing the colour again in MyUnity (or other tools too, perhaps) will bring this behaviour back.

And another update: If you click on the launcher colour setting in MyUnity, change nothing, and ok the colour dialogue, it sets a colour #000001 and opacity 255 instead of colour #000000 and opacity 0. This seems to cause the symptoms described. MyUnity has no way to return to the settings Unity understands. CompizConfig Settings Manager fixes it as decribed above.

---

### Post by comradeluigi on 2012-06-08
> **Aearenda said:**
> I have seen this too. I suspect it is a consequence of playing with the launcher colour settings in MyUnity or a similar tool, but I have no confirmation of that yet. Setting the 'background colour' to default in the experimental tab of the Unity CCSM plugin seems to have fixed it for me.
 
Further observations - if you log out and log in again, things go back to normal until the next reboot. Having reset the default colour in the Unity plugin for CCSM, changing the colour again in MyUnity (or other tools too, perhaps) will bring this behaviour back.
 
And another update: If you click on the launcher colour setting in MyUnity, change nothing, and ok the colour dialogue, it sets a colour #000001 and opacity 255 instead of colour #000000 and opacity 0. This seems to cause the symptoms described. MyUnity has no way to return to the settings Unity understands. CompizConfig Settings Manager fixes it as decribed above.
 yeah that fixed it

---

