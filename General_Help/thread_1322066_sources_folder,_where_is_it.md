---
title: "sources folder, where is it?"
date: 2009-11-10
forum: General Help
---

### Post by sereneicyrain on 2009-11-10
where is the sources folder in ubuntu?
See this link to get an idea of what I mean:

[http://ubuntulinuxhelp.com/linux-driver-for-quickcam-usb-cameras-logitech-quickcam-fusion/](http://ubuntulinuxhelp.com/linux-driver-for-quickcam-usb-cameras-logitech-quickcam-fusion/)

It says:
"
To get a driver go here: [http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/](http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/) and save each file to your sources folder. (Mine is .../root/sources/linux-uvc). The following should be saved:[LEFT][COLOR=#000000]
Read more: [http://ubuntulinuxhelp.com/linux-driver-for-quickcam-usb-cameras-logitech-quickcam-fusion/#ixzz0WUc64dSd](http://ubuntulinuxhelp.com/linux-driver-for-quickcam-usb-cameras-logitech-quickcam-fusion/#ixzz0WUc64dSd)
"
[/COLOR][/LEFT]

---

### Post by falconindy on 2009-11-10
Your "sources" folder is /usr/src/. However, know that building from source as a privileged user is an outdated and conceivably dangerous thing to do. In the end, it really doesn't matter where you build from (symlinks can fix everything), so you may as well just use your home directory.

---

