---
title: "Gnome 3 &amp; Compiz"
date: 2011-09-13
forum: General Help
---

### Post by stallvalds on 2011-09-13
Hello Ubuntu world,
Is compiz compatible with Gnome 3 (Gnome Shell)? I have done some googling and can't find a definitive answer. I'm guessing no, because the effects that I have chosen (wobbly windows is a favorite of mine) do not work in Gnome 3. Of course I could be just missing a setting somewhere. I dunno. Could somebody please clarify?
Regards,
Stallvalds

---

### Post by Sef on 2011-09-14
What are you looking to do? They are two different desktop environments.

---

### Post by stallvalds on 2011-09-14
I would just like to enable the extra window animations that I used before installing Gnome 3. Unfortunately my Gnome 3 install borked my unity. Im running 11.04.

---

### Post by stallvalds on 2011-09-14
By Compiz, I mean the CompizConfig settings manager. I used it before gnome 3 to have wobbly windows and the like.

---

### Post by SpikeyB on 2011-09-25
If you want to use compiz with gnome3 you will first need to use the fallback mode as described here: [http://www.numango.com/5285_playing-gnome-3-fallback-mode.html](http://www.numango.com/5285_playing-gnome-3-fallback-mode.html)

Then using the alt key, while right clicking on the panel, set up the panel the way you really want it (the alt key gives access to the old panel right click menus).  So you can add/remove icons and change the look of the panel.

Then set up an autostart entry as described here: [http://linuxandfriends.com/2011/06/01/how-to-add-startup-programs-in-gnome-3/](http://linuxandfriends.com/2011/06/01/how-to-add-startup-programs-in-gnome-3/)

my file is called "fusion-icon.desktop" and the contents look like this:

[Desktop Entry]
Type=Application
Exec=fusion-icon
Hidden=false
X-GNOME-Autostart-enabled=true
Name[en_US]=compiz
Name=compiz
Comment[en_US]=compiz fusion icon
Comment=compiz fusion icon


Next time you log in you should be running compiz.

If you want to go back, remove the autostart entry and switch fallback mode off.

Hope this is what you were looking for.  It worked for me on my Sabayon box at least, YMMV.

---

### Post by vikramk.ibs on 2011-09-25
> **SpikeyB said:**
> If you want to use compiz with gnome3 you will first need to use the fallback mode as described here: [http://www.numango.com/5285_playing-gnome-3-fallback-mode.html](http://www.numango.com/5285_playing-gnome-3-fallback-mode.html)

Then using the alt key, while right clicking on the panel, set up the panel the way you really want it (the alt key gives access to the old panel right click menus).  So you can add/remove icons and change the look of the panel.

Then set up an autostart entry as described here: [http://linuxandfriends.com/2011/06/01/how-to-add-startup-programs-in-gnome-3/](http://linuxandfriends.com/2011/06/01/how-to-add-startup-programs-in-gnome-3/)

my file is called "fusion-icon.desktop" and the contents look like this:

[Desktop Entry]
Type=Application
Exec=fusion-icon
Hidden=false
X-GNOME-Autostart-enabled=true
Name[en_US]=compiz
Name=compiz
Comment[en_US]=compiz fusion icon
Comment=compiz fusion icon


Next time you log in you should be running compiz.

If you want to go back, remove the autostart entry and switch fallback mode off.

Hope this is what you were looking for.  It worked for me on my Sabayon box at least, YMMV.

Thanks I was looking for solution to the same problem!

You are :KS

---

### Post by epicwiki on 2012-01-02
[http://www.numango.com/5285_playing-gnome-3-fallback-mode.html](http://www.numango.com/5285_playing-gnome-3-fallback-mode.html)


that is one hard to read article, sort of like englishrussia

---

