---
title: "No display after adjustment"
date: 2006-03-21
forum: General Help
---

### Post by cfpole on 2006-03-21
I have a Compaq Armada 7800, 266Mhz, 6GB that I reformatted and installed Ubuntu on.  The resolution was stuck on 640 X 480 and wouldn't change.  Using a message on this forum, I added HorizSync 30-70 and VertRefresh 50-140 to the Monitor section in /etc/X11/xorg.conf. 

After reboot, I come up with a garbled background with the logon screen at a decent resolution.  If  log-on, I come up with a motley screen that I can do nothing on.  If I don't log on right away, the screen goes blank, not black, but bright.  

How can I get back to where I started, or at least to a command prompt.

Thank you for any help you can give me.

Chuck

---

### Post by halfvolle melk on 2006-03-21
Somewhere during a reboot it will say something about GRUB and count down from 3. At that point, press escape and choose the fail save mode. It should give you command line allowing you to edit xorg.conf.

---

### Post by henriquemaia on 2006-03-21
On a terminal, type:

```
sudo dpkg-reconfigure xserver-xorg
```

Adjust the settings to your liking. Then restrart X.

Try reading this thread for more info:

[http://ubuntuforums.org/showthread.php?t=83973&highlight=refresh+rate](http://ubuntuforums.org/showthread.php?t=83973&highlight=refresh+rate)

---

### Post by henriquemaia on 2006-03-21
[QUOTE=halfvolle melk]Somewhere during a reboot it will say something about GRUB and count down from 3. At that point, press escape and choose the fail save mode. It should give you command line allowing you to edit xorg.conf.[/QUOTE]

Probably you don't need to go that far. If your X is locked or unreadable, press
CTRL+ALT+F1 (or any F key till F6) to get to the terminal.

---

### Post by Ramses de Norre on 2006-03-21
Be very careful with refresh rates, you should use the ones from your monitor tech specs. Wrong values can physically damage your monitor!

---

### Post by cfpole on 2006-03-21
Thank you, that procedure took care of it.  My resolution is now correct, I have just made it over the first hurdle.

Chuck

---

