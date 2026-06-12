---
title: "Screen Resolution stuck at 640x480?"
date: 2006-02-13
forum: General Help
---

### Post by BongoBob on 2006-02-13
Hello everyone. I recently installed Ubuntu 5.10, and it's been working great. But today, when I went to login, the screen resolution had dropped from 1280x1024 to 640x480. When I go to System--Prefrences--Screen Resolution, all it has is 640x480.

Does anybody know how to fix this? Any help is appreciated :)

Edit: Nevermind, I found out how to fix it with sudo dpkg-reconfigure xserver-xorg.

But, does anyone know how this happened? Like, why it changed by itself?

---

### Post by Mr Frosti on 2006-02-13
I can tell you how to fix this, however it is probably important to know why this happened. Did you recently install / uninstall anything pertaining to your video card drivers? 

To fix this issue, click on "Applications" -> "Accessories" -> "Terminal". In the terminal, type in ```
sudo gedit /etc/X11/xorg.conf
``` and press enter. This will prompt for your password. Scroll down to the section that reads

Section "Screen"
   ...
```
   SubSection "Display"
          Depth           24
          Modes           "640x480"
   EndSubSection
```
...

and change this to 

```
   SubSection "Display"
          Depth           24
          Modes           "1280x1024""640x480"
   EndSubSection
```

--

Save this file, then restart your X server by pressing "Ctl" + "Alt" + "Backspace"

---

