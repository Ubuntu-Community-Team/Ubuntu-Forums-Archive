---
title: "changing the login window"
date: 2010-08-21
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2010-08-21
so i got some themes
following these instructions
[http://www.ubuntugeek.com/nice-themes-for-ubuntu-10-04-lucid-lynx-users.html](http://www.ubuntugeek.com/nice-themes-for-ubuntu-10-04-lucid-lynx-users.html)
is there a way i can get my login window (not the background image)
to look like it does in one of these images
[http://www.ubuntugeek.com/wp-content/uploads/2009/06/exotic.jpg](http://www.ubuntugeek.com/wp-content/uploads/2009/06/exotic.jpg)
[http://www.ubuntugeek.com/wp-content/uploads/2009/06/tropical-prsentation.jpg](http://www.ubuntugeek.com/wp-content/uploads/2009/06/tropical-prsentation.jpg)

---

### Post by Pollox on 2010-08-22
(a copy paste of my answer from elsewhere) > Changing the login theme
Source: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/449198](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/449198)

Press Alt+F2, and run "gksudo -u gdm dbus-launch gnome-appearance-properties".  Use the "Theme" tab to customize the login theme, and the "Background" tab to customize the background image of the login screen.  After doing this, you might notice some new blue icons in your notification area.  Go to System >> Preferences >> Keyboard, click the "Accessiblity" tab, and uncheck "Accessibility features can be toggled with keyboard shortcuts" to get rid of one of them, and then reboot to get rid of the other.

---

### Post by pqwoerituytrueiwoq on 2010-08-22
i have already set the theme but the login window design does not change

---

### Post by Pollox on 2010-08-22
You sure you set the theme as the gdm user and not yourself?  I would think the particular aspect of the theme that changes the window should appear under the "window border" tab when you go to customize the theme, so check there to make sure the window border is set to the one from your theme.

---

### Post by pqwoerituytrueiwoq on 2010-08-22
currently i have a customized metacity theme on it
i think i need to use emerald as the window manager but i have no idea how to do that on the log in screen
i did it by putting a desktop file to open the appearance manager in */usr/share/gdm/autostart/LoginWindow/*
i cant use that trick to open a terminal to run emerald --replace
i can get the configuration editor though

---

### Post by Pollox on 2010-08-22
Hmm, well if you run gconf-editor as the gdm user, I think we can do it from there.  I see the key:
/apps/compiz/plugins/decoration/allscreens/options/command
with value
gtk-window-decorator --replace
so that *might* be a good spot to put emerald --replace

You might have to change some gconf values so gdm is using compiz too.  I am guessing at the moment, so if someone else has a better idea feel free to chime in.  These do look like some neat themes.

---

### Post by pqwoerituytrueiwoq on 2010-08-22
still no emerald i cant even get compiz to stick
compiz was set via gnome-appearance-properties

---

