---
title: "Display is &quot;stretched&quot;"
date: 2011-05-06
forum: General Help
---

### Post by picard137 on 2011-05-06
The image below shows how the top of my screen is "stretched" and the left side is wrapped to the right side. Also, the pointer position does not seem to know about the stretching (in the picture the pointer is on the calculator, but the tooltip shows the computer things the pointer is on character map).

The problem is fixed when I change the resolution with the ubuntu gui monitor tool. Anytime the screensaver goes on or after I restart, the problem is back and I have to do the resolution change "fix".

Im using ubuntu 11.04 with the no effects gnome option. If it helps, lspci gives me:
...
VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)
...
Any help would be appreciated. Thanks.

[http://postimage.org/image/4mf38lac](http://postimage.org/image/4mf38lac)

---

### Post by AlphaLexman on 2011-05-06
The default setup in ubuntu is for 'nautilus' to manage the desktop in gnome.

Check your nautilus commands: see ```
man nautilus
``` and look for items such as:

[LIST]
[*]--geometry
[*]--no_default_window
[*]--no_desktop
[/LIST]
You may need to remove one or more of these settings.

---

