---
title: "How do I hide my linux drive from Windows?"
date: 2010-10-22
forum: General Help
---

### Post by princedugan on 2010-10-22
Each OS has its own drive. When I boot windows, I want windows to operate as if my Linux drive is unplugged.

---

### Post by mike555 on 2010-10-22
if you formatted it EXT4 a person shouldn't be able to get into Ubuntu from Windows .......... or are you just trying to hide Ubuntu?

---

### Post by JustinR on 2010-10-22
> **mike555 said:**
> if you formatted it EXT4 a person shouldn't be able to get into Ubuntu from Windows .......... or are you just trying to hide Ubuntu?

It's most likely because if someone were to click the drive when in Windows, Windows would ask you to reformat it - because it doesn't recognize Linux filesystems.

---

### Post by Schrute Farms on 2010-10-22
There is a setting in windows, I think in the device manager, that you can tell Windows to not use the drive at all.
Once it's set, the only place you see the drive is in the device manager with a red X next to it.
Right click on My Computer; select Properties then the Hardware tab.  Click on Device Manager.  When it opens, right click on your Linux drive and select properties.  In the drop down list at the bottom, select "Do not use this device (disable)".  Click OK and you're don.

---

