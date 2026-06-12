---
title: "Battery Meter Problems 10.10 Maverick Meerkat"
date: 2010-10-26
forum: General Help
---

### Post by omaralqady on 2010-10-26
I have a problem with the battery meter in the panel which happens after the battery is fully charged and I remove the charger, the battery meter would not detect the charger's removal unless I wait for a while until the battery has discharged a little, then when I plug in the charger and the battery starts charging again the meter would detect that it's charging and move its status from charged to charging. 

This problem only happens with the battery meter in the panel, when I run 'acpi 1' or 'cat /proc/acpi/battery/BAT1/state' the output is correct. Also if I'm running Windows XP in Virtual Box, it detects the removal of the charger normally, but Ubuntu still does not detect it!

I'd appreciate any help because this is really annoying :)

---

### Post by togume on 2011-04-21
Confirming this issue. The battery indicator seems to be unresponsive to changes in charger connection. This started happening recently. As mentioned above, guest OS (Win 7 in this case) does pick up the power status correctly and quickly.

The other strange behavior is that the battery meter is unresponsive when left-clicked and then select the status (i.e. "Laptop battery is charged").

---

