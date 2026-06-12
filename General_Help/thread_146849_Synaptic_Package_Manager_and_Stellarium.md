---
title: "Synaptic Package Manager and Stellarium"
date: 2006-03-19
forum: General Help
---

### Post by spearfish on 2006-03-19
Hi,

I admit that I'm kind of new to Ubuntu linux.  So, yesterday I used Synaptic Package Manager to install two programs:

Stellarium and Gnome Lunar Clock (glunarclock)

My problem is:  I can't find them!  Where the heck did they go?

I attempted the following command:

~$sudo apt-get install stellarium
 Password:
 Reading package lists... Done
 Building dependency tree... Done
 stellarium is already the newest version.
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So my system seems to think that stellarium is installed... but it hasn't yet appeared in the applications menu.  Also, I have done a Places->Search For Files attempt, but nothing comes up.  Find doesn't come up with anything for glunarclock either.

Thanks to anyone who can help a poor CS student down on his luck. :)

-spearfish

---

### Post by dermotti on 2006-03-19
sudo updatedb
locate glunarclock
locate stellarium

---

### Post by chuckyp on 2006-03-19
Well the applicaiton may not have installed a link in the menus.  To find the location of the binarary file or (executable) you could type in a terminal "which stellarium"  that will show you the path to the binarary.  Most likely you could launch either one from a terminal just by typing their name.  To add them to the menu you can use the menu editor and just create a link to them.

---

### Post by spearfish on 2006-03-19
Thanks!  I tried:

sudo updatedb
locate stellarium

it came up with: /usr/bin/stellarium
and I was able to run the application with ./stellarium from that directory

however, when I tried:  locate glunarclock

I got a whole mess of stuff, and I don't know where to start:

~$ locate glunarclock
/etc/gconf/schemas/glunarclock.schemas
/etc/gconf/gconf.xml.defaults/schemas/apps/glunarclock_applet
/etc/gconf/gconf.xml.defaults/schemas/apps/glunarclock_applet/prefs
/etc/gconf/gconf.xml.defaults/schemas/apps/glunarclock_applet/prefs/%gconf.xml
/etc/gconf/gconf.xml.defaults/schemas/apps/glunarclock_applet/%gconf.xml
/var/lib/dpkg/info/glunarclock.postinst
/var/lib/dpkg/info/glunarclock.list
/var/lib/dpkg/info/glunarclock.postrm
/var/lib/dpkg/info/glunarclock.conffiles
/var/lib/dpkg/info/glunarclock.md5sums
/var/cache/apt/archives/glunarclock_1%3a0.32.1-2ubuntu1_i386.deb
/usr/share/doc/glunarclock
/usr/share/doc/glunarclock/copyright
/usr/share/doc/glunarclock/NEWS.gz
/usr/share/doc/glunarclock/AUTHORS
/usr/share/doc/glunarclock/README
/usr/share/doc/glunarclock/changelog.Debian.gz
/usr/share/doc/glunarclock/ABOUT-NLS.gz
/usr/share/locale/da/LC_MESSAGES/glunarclock-0.32.mo
/usr/share/locale/de/LC_MESSAGES/glunarclock-0.32.mo
/usr/share/locale/es/LC_MESSAGES/glunarclock-0.32.mo
/usr/share/locale/fi/LC_MESSAGES/glunarclock-0.32.mo
/usr/share/locale/fr/LC_MESSAGES/glunarclock-0.32.mo
/usr/share/locale/ga/LC_MESSAGES/glunarclock-0.32.mo
/usr/share/locale/gl/LC_MESSAGES/glunarclock-0.32.mo
/usr/share/locale/hu/LC_MESSAGES/glunarclock-0.32.mo
/usr/share/locale/ja/LC_MESSAGES/glunarclock-0.32.mo
/usr/share/locale/ms/LC_MESSAGES/glunarclock-0.32.mo
/usr/share/locale/nl/LC_MESSAGES/glunarclock-0.32.mo
/usr/share/locale/no/LC_MESSAGES/glunarclock-0.32.mo
/usr/share/locale/ru/LC_MESSAGES/glunarclock-0.32.mo
/usr/share/locale/sv/LC_MESSAGES/glunarclock-0.32.mo
/usr/share/locale/ro/LC_MESSAGES/glunarclock-0.32.mo
/usr/share/locale/vi/LC_MESSAGES/glunarclock-0.32.mo
/usr/share/locale/sr/LC_MESSAGES/glunarclock-0.32.mo
/usr/share/locale/wa/LC_MESSAGES/glunarclock-0.32.mo
/usr/share/locale/az/LC_MESSAGES/glunarclock-0.32.mo
/usr/share/locale/ast_ES/LC_MESSAGES/glunarclock-0.32.mo
/usr/share/pixmaps/glunarclock-logo.png
/usr/share/pixmaps/glunarclock
/usr/share/pixmaps/glunarclock/cartoonmoon_12frames.png
/usr/share/pixmaps/glunarclock/moon_56frames.png
/usr/share/omf/glunarclock
/usr/share/omf/glunarclock/glunarclock-applet-2-C.omf
/usr/share/gnome/help/glunarclock-applet-2
/usr/share/gnome/help/glunarclock-applet-2/C
/usr/share/gnome/help/glunarclock-applet-2/C/legal.xml
/usr/share/gnome/help/glunarclock-applet-2/C/figures
/usr/share/gnome/help/glunarclock-applet-2/C/figures/glunarclock_applet.png
/usr/share/gnome/help/glunarclock-applet-2/C/glunarclock-applet-2.xml
/usr/share/glunarclock
/usr/share/glunarclock/glunarclock.glade
/usr/lib/gnome-panel/glunarclock-applet-2

ho hum.  thanks :???:

---

### Post by dermotti on 2006-03-19
Hmm, its a gnome applet? Just right click your gnome panel and select "add applet". it should be in that list of applets.

---

### Post by chuckyp on 2006-03-19
For stellarium you shouldn't need to change to /usr/bin and ./stellarium that should be in your users path.  You should be able to launch it from any directory in terminal by typing stellarium.  Or by hitting alt+f2 and running it from there.

---

