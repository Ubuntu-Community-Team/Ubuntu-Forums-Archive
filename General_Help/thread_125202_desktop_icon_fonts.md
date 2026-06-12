---
title: "desktop icon fonts"
date: 2006-02-03
forum: General Help
---

### Post by sphere02 on 2006-02-03
how do I enable "outline" fonts for desktop icons that i have seen in some screenshots (white text with black boarder)

---

### Post by asimon on 2006-02-03
Sadly there is no easy GUI way to do this.

Edit the file /usr/share/kubuntu-default-settings/kde-profile/default/share/config/kdesktoprc
You need to use sudo to edit this file, it's not writable by a normal user.

Then move the line
```
ShadowParameters=1,1,128,255,3,4,0
```
from the FMSettings section to somewhere in the Desktop0 section.

You need to restart the desktop to take effect.

To change the colors of the font and it's outline, right click on the desktop, choose "configure desktop", then "advanced settings".

EDIT:
Thanks for this hack goes to Sebastian Kügler and Jonathan Riddell who posted it to kubuntu development mailinglist where I just found it. :-)

---

### Post by sphere02 on 2006-02-03
ah ok! can try it out, but this "feature" is enabled by default in Suse then? (seen screens of suse at osdir.com)

---

### Post by sphere02 on 2007-11-04
how about doing that outline thing in Gnome

---

