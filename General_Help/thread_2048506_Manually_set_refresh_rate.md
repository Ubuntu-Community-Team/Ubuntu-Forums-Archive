---
title: "Manually set refresh rate"
date: 2012-08-26
forum: General Help
---

### Post by DaveyG on 2012-08-26
Hi everyone. My onboard graphics controller (an Intel 82946GZ/GL) doesn't seem to let me set the display's refresh rate to 70Hz on 1280x1024, just 60Hz and 75Hz.

I used xrandr as below, to manually set 70Hz, but it doesn't seem to "stick"...

```

xrandr --newmode "1280x1024@70"  120.84  1280 1368 1504 1728  960 961 964 999  -HSync +Vsync
xrandr --addmode VGA1 "1280x1024@70"
xrandr --output VGA1 --mode "1280x1024@70"

```

When I reboot, it goes back to just allowing 60Hz and 75Hz

Any help would be greatly appreciated?

---

### Post by Toz on 2012-08-26
Version 11.10 or 12.04? If you've got lightdm, then try this:

Create a script with that content. 
```
gksu leafpad /usr/local/bin/setup_xrandr
```

Copy/paste the following content:
```
#!/bin/bash
xrandr --newmode "1280x1024@70"  120.84  1280 1368 1504 1728  960 961 964 999  -HSync +Vsync
xrandr --addmode VGA1 "1280x1024@70"
xrandr --output VGA1 --mode "1280x1024@70"
```

Save the file.

Make the file executable:
```
sudo chmod +x /usr/local/bin/setup_xrandr
```

Edit the lightdm configuration file:
```
gksu leafpad /etc/lightdm/lightdm.conf
```

Append the following to the end of the file:
```
display-setup-script=/usr/local/bin/setup_xrandr
```

Save the file and reboot.

---

### Post by DaveyG on 2012-08-28
Hi Toz, thanks for your reply.

Version 11.10, lightdm. Sorry for the delay in reply, creating the script seems to have fixed it.

Thank you, and thanks again for your reply.

---

