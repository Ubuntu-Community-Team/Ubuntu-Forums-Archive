---
title: "How to change slider color in Oneiric Gnome Classic"
date: 2012-03-26
forum: General Help
---

### Post by Ralph L on 2012-03-26
Recently installed Oneiric with gnome-session-fallback (gnome-classic). I removed (using Synaptic) overlay-scrollbar, liboverlay-scrollbar-0.2-0, and liboverlay3-0.2-0, thus changing the scrollbar back to its classic form.  Using Advanced Settings (gnome-tweak-tools) I selected a Windows theme=Simple, and GTK+theme=Ambiance.  I like the looks of everything except for the individual window's menubar (which is too black), and the slider on the scrollbar (which is a very light gray, and doesn't show up on the gray scrollbar).  I can't seem to find a theme that I like that fixes these problems.

Can anybody tell me how to change the color of the individual window's menubar (not the top panel), and the slider on the scrollbar (not the scrollbar itself)?

Thank you
Ralph

---

### Post by Ralph L on 2012-03-30
Come on!!!  Somebody on this great forum must know how to change the color on a couple windows items.  My eyes aren't so great and I have trouble reading the black menu bar, and detecting the slider on the gray scrollbar.

I know you will come thru!!!

Thanks
Ralph

---

### Post by Ralph L on 2012-04-01
In lucid I could change various window features using gnome-appearance-properties.  However, when I can't find it under Oneiric.  Does anybody know if it can be installed under Oneiric?

---

### Post by Ralph L on 2012-05-24
I moved to Precise and installed the Clearwaita theme from [http://gnome-look.org/content/show.php?content=145210](http://gnome-look.org/content/show.php?content=145210) .  This solved a rash of problems with the themes.  I also got back the scrollbars by following:  [http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 

```
sudo apt-get purge liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0 overlay-scrollbar
```

It may be necessary to get back the scrollbar stepper arrows by following [http://ubuntuforums.org/showthread.php?t=1965929](http://ubuntuforums.org/showthread.php?t=1965929) .

---

