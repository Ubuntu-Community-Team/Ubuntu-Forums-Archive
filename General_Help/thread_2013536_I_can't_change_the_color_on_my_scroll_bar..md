---
title: "I can't change the color on my scroll bar."
date: 2012-07-01
forum: General Help
---

### Post by davidwillis on 2012-07-01
I am running 12.04 with gnome shell, and I would really like to change the color of my scroll bar.  I have removed the overlay, but now I want to change the color so I can see it. I have tried modifying my /usr/share/themes/Ambiance/gtk-2.0/gtkrc file (which seems to do nothing). I tried using gnome color changer (I couldn't find anything for the scroll bar. And I used dconf-editor to adde bg_color:#f0f1f2;selected_bg_color:#dd4814 to the gtk-color-scheme.

by doing that, it changed the scroll bar on some of my windows (like in firefox, libre office, etc).  But it did not change on many windows.  How do I change this on all the scroll bars?

See picture:

---

### Post by vasa1 on 2012-07-01
Some apps are gtk-2 others are gtk-3. Gnome color chooser and gtkrc affect only gtk-2 apps.
To change scrollbars for gtk-3 apps please see [http://ubuntuforums.org/showpost.php?p=11387332&postcount=9](http://ubuntuforums.org/showpost.php?p=11387332&postcount=9)

---

### Post by davidwillis on 2012-07-01
Thanks.  That did it.  I had played with settings in all those files, but didn't realize I had to log out and back in for them to take effect.  Just changing the theme back and forth does not work.

It would be nice if they made it a little easier to change.  But at least it is working now.

Thanks

---

### Post by davidwillis on 2012-07-01
I just noticed it has now changed everything but chromeium.  I have chromeium set to use GTK+ theme.  But the scroll is still the same color.

---

