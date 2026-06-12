---
title: "Where do the menu items in Preferences come from?"
date: 2010-11-06
forum: General Help
---

### Post by ngagun on 2010-11-06
When I choose System --> Preferences --> Screensaver, it runs x-screensaver instead of gnome-screensaver, BUT, in /usr/share/applications, I have the file:

gnome-screensaver-preferences.desktop 

And the contents are:

[Desktop Entry]
Name=Screensaver
Comment=Set your screensaver preferences
Icon=preferences-desktop-screensaver
Exec=gnome-screensaver-preferences
Terminal=false
Type=Application
Categories=GTK;GNOME;Settings;DesktopSettings;
OnlyShowIn=GNOME;
StartupNotify=true
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-screensaver
X-GNOME-Bugzilla-Component=general
X-Ubuntu-Gettext-Domain=gnome-screensaver

So it should be launching gnome-screensaver, not x-scrensaver. Where on earth is x-screensaver getting launched from? I thought the menu was determined by /usr/share/applications. (By the way, I did previously have x-screensaver instead of gnome, I am trying to put it back how it was. I have more-or-less succeeded, except this Menu item which is puzzling me.)

Thanks!

---

### Post by wojox on 2010-11-06
This may help in your hacking around [Filelist of package gnome-screensaver]("http://packages.ubuntu.com/lucid/i386/gnome-screensaver/filelist")

---

### Post by ngagun on 2010-11-06
Fixed this myself. Apparently besides /usr/share/applications, there are also relevant files in:

~/.local/share/applications

Once I got rid of those, the menu launches the gnome screensaver preferences as expected.

---

