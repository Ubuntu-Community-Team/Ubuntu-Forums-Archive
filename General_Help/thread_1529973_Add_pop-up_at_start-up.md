---
title: "Add pop-up at start-up"
date: 2010-07-12
forum: General Help
---

### Post by Axel-P on 2010-07-12
Hey!

I would want to know, is there any way to pop-up a custom message window at start-up for every user?

Technically I want to let the users know that in a couple of days I'll be upgrading the system so I want that all the users from a specific machine to be aware of that.

Thanks!

---

### Post by Brandon Williams on 2010-07-13
You could add a *.desktop file to /etc/xdg/autostart that will launch the app the provides the dialog. If you aren't sure about an app to use, consider zenity. For example,
```
zenity --info --title "System Upgrade Info" --text "A system upgrade is scheduled for ..."
```

---

### Post by Axel-P on 2010-07-13
Well zenity certainly does what I need but my scrip wont launch. I placed it in: /etc/xdg/autostart/

---

### Post by Brandon Williams on 2010-07-14
The script won't go in that directory. A *.desktop file goes in that directory. Is that what you mean by script?

If you post the content of the *.desktop file you created, we might be better able to help.

---

### Post by Axel-P on 2010-07-16
> **Brandon Williams said:**
> The script won't go in that directory. A *.desktop file goes in that directory. Is that what you mean by script?

If you post the content of the *.desktop file you created, we might be better able to help.

Same as yours. I just copied/pasted your zenity command to test. I wrote it in a mssg.desktop that is placed in /etc/xdg/autostart/

And yeah, I was talking about the .desktop when I said "script"

---

### Post by Brandon Williams on 2010-07-16
Not sure what you mean by "same as yours". I didn't post a sample *.desktop file. Did you look at any of the other files in that directory to use as a template?

Here is what /etc/xdg/autostart/nm-applet.desktop looks like:
```
[Desktop Entry]
Name=Network Manager
Comment=Control your network connections
Icon=nm-device-wireless
Exec=nm-applet --sm-disable
Terminal=false
Type=Application
OnlyShowIn=GNOME;XFCE;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-enabled=true
X-Ubuntu-Gettext-Domain=nm-applet
```
Using that as a template, the *.desktop file for your dialog might look like this:
```
[Desktop Entry]
Name=System Upgrade Notification
Comment=Display system upgrade notification dialog
Exec=zenity --info --title "System Upgrade Info" --text "A system upgrade is scheduled for ..."
Terminal=false
Type=Application
OnlyShowIn=GNOME;XFCE;
```

---

### Post by Axel-P on 2010-07-16
OH!

Sorry I should have checked some .desktop before posting the last post. What I did was just simply put this:

```
zenity --info --title "System Upgrade Info" --text "A system upgrade is scheduled for ..."
```

into a .desktop file.

I'll try to create a more complete .desktop based in what you just gave me.

Thanks!

---

