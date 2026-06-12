---
title: "How to restore single line scroll capability under Gnome 3 Classic"
date: 2012-04-26
forum: General Help
---

### Post by Ralph L on 2012-04-26
I recently installed oneiric, gnome-session-fallback, and am using Gnome Classic (no effects).  With Gnome Classic there are no scrollbars.  To restore them I followed instructions to uninstall overlay-scrollbar, liboverlay-scrollbar-0.2-0, and liboverlay-scrollbar3-0.2-0.  This got me (almost) the classic scrollbars, but the arrows at the end of the scrollbars are missing.  This means I can't scroll up and down a line at a time on many things (like Nautilus), and I really miss this feature.

Can anybody tell me how to get back, under Gnome 3 Classic, a single line scroll capability using the scrollbars?  Many applications,such as LibreOffice still have the single line scroll (arrows at ends of scrollbars), but Linux utilities like Nautilus don't allow single line scroll.  I haven't tried Precise.  Does it have single line scroll capability, when using Gnome 3 Classic?  I would sure appreciate any help.

Ralph

---

### Post by Ralph L on 2012-05-23
I found 2 solutions for getting the scrollbar stepper arrows back under Precise Pengolin.  The easiest one was to install the Clearwaita theme from [http://gnome-look.org/content/show.php?content=145210](http://gnome-look.org/content/show.php?content=145210) .  I found this referenced at [http://ubuntuforums.org/showthread.php?t=1917567](http://ubuntuforums.org/showthread.php?t=1917567) .  Although I have installed so much garbage trying to solve this problem that I am not sure about what caused what to happen, it appears that Clearwaita will automatically install the stepper arrows.  The other solution I found was at [http://askubuntu.com/questions/34214/how-do-i-disable-overlay-scrollbars](http://askubuntu.com/questions/34214/how-do-i-disable-overlay-scrollbars) .  This solution seemed to install stepper arrows on themes that didn't have them built in, such as Radiance.  See excerpt below:

Just disabling or removing the overlay-scrollbars as described by the other answers will get you back the scroll bars, but they will be missing the stepper buttons at the end of the bars because they have been disabled in the Ambiance theme. To re-enable them, put the following in the ~/.gtkrc-2.0 file:

style "default" {
  engine "murrine" {
    stepperstyle = 0
  }
}

and the following into the file ~/.config/gtk-3.0/gtk.css:

.scrollbar {
  -GtkScrollbar-has-backward-stepper: 1;
  -GtkScrollbar-has-forward-stepper: 1;
}

I needed to at least log out and log in to get the steppers to appear.  Once I had to do a complete reboot.

Hope this helps somebody.
Ralph

---

### Post by cbl016 on 2012-05-26
Thanks Ralph L. This is exactly what I needed.

---

### Post by Ralph L on 2012-10-01
Note that Clearwaita theme has now become Clearlooks-Phenix.  You can google it.

---

### Post by Ralph L on 2012-10-14
Here are two additional (and probably better) ways to disable overlay scrollbars.  I discovered these later:

1.  Install dconf Editor using Synaptic or Ubuntu Software Center to install "dconf-tools".  Go to Main menu>Applications>System Tools>dconf Editor.  In dconf Editor go to org>gnome>desktop>interfaces and uncheck ubuntu-overlay-scrollbars.

2.  In Terminal enter “gsettings set org.gnome.desktop.interface ubuntu-overlay-scrollbars false”.

---

