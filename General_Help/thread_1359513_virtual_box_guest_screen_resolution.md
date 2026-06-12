---
title: "virtual box guest screen resolution"
date: 2009-12-19
forum: General Help
---

### Post by Falc7 on 2009-12-19
I have windows 7 running in a virtual box in karmic. However i am having trouble with the screen resolution, my resolution in ubuntu is 1200X800. When i make the screen resolution of windows higher than 800X600 the whole windows desktop dosen't fit into my screen and i have to scroll up and down to see the whole desktop, which is quite annoying as i have to re-capture the mouse for ubuntu when i want to do that. Is there a way to make the windows resolution a good size and have the whole thing fit on my screen well.

---

### Post by bear24rw on 2009-12-19
Install guest additions and you can just adjust the window to any size

---

### Post by Dennis N on 2009-12-19
As stated in the reply above, install the guest additions:

In the VirtualBox window menu:

```
Devices > Install Guest Additions
```

After the installation process ends, you will need to restart the guest os. Then you can resize the window as desired or run full screen (Rt-Ctrl + F). You also have seamless mouse integration - it won't be captured in the VB window.

---

### Post by Falc7 on 2009-12-20
Working great thanks!

---

