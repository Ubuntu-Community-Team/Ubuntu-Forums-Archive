---
title: "Re-enable mouse after unchecking &quot;Enable this device&quot; in Settings &gt; Mouse menu"
date: 2012-06-06
forum: General Help
---

### Post by chipmunk02115 on 2012-06-06
In Ubuntu 12.04 Applications Menu > Settings > Mouse and Touchpad > Devices (Mouse)  I accidentally unchecked the "Enable this device" button - which caused my mouse to stop working.

To solve this problem, I first went into terminal mode **CTRL-ALT-F1**, and from there I re-installed "xserver-xorg-input-mouse" 

[B]sudo apt-get remove xserver-xorg-input-mouse
sudo apt-get install xserver-xorg-input-mouse[/B]

Now the mouse is working again.

I looked everywhere on Ubuntu forums for this problem / solution - but found nothing - so I thought someone else might find this solution useful.

Personally I don't see the logic of having "Enable this device" button in the first place in the Settings menu. This button is not in Ubuntu versions before 12.04.

---

