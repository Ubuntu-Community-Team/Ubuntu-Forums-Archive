---
title: "xorg.conf can I generate it?"
date: 2010-01-20
forum: General Help
---

### Post by gypsumwolf on 2010-01-20
Since the computer does not have xorg.conf, can I have the computer generate that file because I need to work on it and so I need to create it. That is why it would be useful to have a xorg.conf file still.

---

### Post by Barriehie on 2010-01-21
> **gypsumwolf said:**
> Since the computer does not have xorg.conf, can I have the computer generate that file because I need to work on it and so I need to create it. That is why it would be useful to have a xorg.conf file still.

**dexconf** will generate the file.

---

### Post by scouser73 on 2010-01-21
> **gypsumwolf said:**
> Since the computer does not have xorg.conf, can I have the computer generate that file because I need to work on it and so I need to create it. That is why it would be useful to have a xorg.conf file still.

Paste these commands into Terminal to create a new Xorg.conf, that should now have created a new xconfig file.


Step 1 runs the NVIDIA utility to generate a new xorg.conf file that the utility can actually read.
**> sudo nvidia-xconfig**

Step 2 runs the graphical NVIDIA setup tool as root, so you can actually save your changes.
**> sudo nvidia-settings**

If this does not work then after step 1, do **sudo rm /etc/X11/xorg.conf** to delete your current xorg.conf file. Then run **sudo nvidia-xconfig** and **sudo nvidia-settings**.

---

### Post by llawwehttam on 2010-01-21
If you don't have an nvidia card on the other hand then try ```
sudo -dpkg-reconfigure xserver-xorg
```

---

### Post by gypsumwolf on 2010-01-21
> **llawwehttam said:**
> If you don't have an nvidia card on the other hand then try ```
sudo -dpkg-reconfigure xserver-xorg
```

I have an ATI card. I tried your method and dexconf and it does not shows up in /etc/X11

---

### Post by Barriehie on 2010-01-21
Boot into recovery mode and run 'xfix' from the menu.

Edit: It's location isn't etched in stone. Try:
```

sudo find / -iname xorg.conf -print

```

Also, here's an online [[color="blue"]link[/color]](http://www.tkk.fi/Misc/Electronics/faq/vga2rgb/calc.html) for finding out about your monitor.

---

