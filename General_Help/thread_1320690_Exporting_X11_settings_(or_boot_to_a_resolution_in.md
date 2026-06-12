---
title: "Exporting X11 settings (or boot to a resolution in a VM)"
date: 2009-11-09
forum: General Help
---

### Post by jimstapleton on 2009-11-09
I have Ubuntu running in a VM (VMWare). Currently it starts up with a 640x480 resolution. I prefer to run the VM at 1440x900. I have used the SettingsManager/Display app to set this resolution, but when the VM boots, and I log in, it still defaults to 640x480. As soon as I open the display settings app, it reconfigures to 1440x900, but I have to do that every login (and deal with rearranging the plasmids on my desktop).

I would *like* to export my xorg settings to an Xorg.conf file, and modify it to default to my desired resolution rather than 640x480. There isn't an Xorg.conf in /etc/X11 - I am aware that Xorg, some time during version 7, has switched to auto configuring each start up.

Does anyone know how to export x11 settings, or have another solution they would recommend for this issue?

---

### Post by jbrown96 on 2009-11-09
open a terminal when you first login (apps-->acc-->terminal) and try the following. ```
xrandr --fb 1440x900
``` If that works, then just create a script to run it automatically on login. 

Open the text editor and paste this in the file > #!/bin/bash
xrandr --fb 1440x900 Save the file as > .fix-resolution.sh In the terminal ```
chmod a+x .fix-resolution.sh
```Go into System-->preferences/admin-->Startup (or something similar) and add a new script and find this file (it will be hidden). Your resolution should automatically set when you login.

---

### Post by jimstapleton on 2009-11-09
No luck on 'xrandr --fb 1440x900'

---

