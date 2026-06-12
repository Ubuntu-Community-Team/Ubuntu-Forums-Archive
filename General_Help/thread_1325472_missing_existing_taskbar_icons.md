---
title: "missing existing taskbar icons"
date: 2009-11-13
forum: General Help
---

### Post by sgk111 on 2009-11-13
power icon, volume icon, networking icons are missing...
they were active when installed and used with ubuntu nearly 10 times... but not seen now at all...

somewhere i read that to go through System\Preferences and select... but exists only for that session... every time we are required to do it...

why icons are missing and how to get them back...

---

### Post by ajgreeny on 2009-11-13
Firstly, right click in an empty area of the panel/taskbar, well away from any other icon showing, and choose "Add to panel".  Now add the Notification area, and hopefully several icons will appear.

That will not, however, add the volume icon and you will need to repeat the right click and choose "Volume control".  It is called that in 9.04, but may be different in 9.10, I can't remember, so look for a similar item.  You can also look for any other panel applets that may be useful and add them as well.

As to why they disappeared in the first place, I can't imagine, but before you add any back you can look in the hidden **~/.gconf/apps/panel/applets** folder in your home (Ctrl+H to see them if they do not show) and open the xml file in each of the numbered applet folders in that.  Near the bottom of each xml text you will see text of the following format ```
OAFIID:GNOME_NotificationAreaApplet
``` which tells you what that applet is.  If they are for something that should be seen but does not appear on your panel, you can delete these applet_1 etc folders , and then add back the applet later with the right click procedure.

PS:  I only have one panel in spite of using gnome, so there may be two panel items in the .gconf/apps folder if you have the more usual two panels.  Look in both if there are two of them.

---

### Post by sgk111 on 2009-11-14
I tried these steps... but could get only Notification area space at top right corner. But icons were still missing.

How can I select Power Icon, Volume control, Network etc icons which were existing a few days back. I do not know how they are vanished.

---

### Post by poliltimmy on 2010-04-29
Same problem here on an upgrade from 9.10. No volume applet.  Seems like there should be a network icon of 2 computers, no access to those settings in the menu that I am aware of.

---

### Post by xtremo on 2010-04-30
> **poliltimmy said:**
> Same problem here on an upgrade from 9.10. No volume applet.  Seems like there should be a network icon of 2 computers, no access to those settings in the menu that I am aware of.

Same here....bit puzzled on this one.

---

### Post by dino99 on 2010-04-30
sudo dpkg-reconfigure gnome-control-center

---

### Post by poliltimmy on 2010-04-30
> **dino99 said:**
> sudo dpkg-reconfigure gnome-control-center

Thanks but this done nothing.

---

### Post by wenfuli on 2010-06-16
I have the same problem. My volume icon, battery icon, and the mail notification icon (that one that looks like an envelope) that turns green when new mail arrives are all gone and I can't figure out why.

---

