---
title: "I don't know where to start... Many problems!!!"
date: 2010-11-08
forum: General Help
---

### Post by krtica on 2010-11-08
I have Ubuntu 10.04 installed on my laptop. It worked flawlessly since April til maybe an hour ago. Suddenly, many things starts to happen at once.

First thing I noticed was ***Places*** menu issue. Whatever I click ClamTk is opening and scanning. But when I double click on folder on Desktop, Nautilus is opening with no problems.
When I run Nautilus from comand prompt, I have this:
```
**user@Ubuntu:~$ nautilus**
** Message: Initializing gksu extension...
Initializing nautilus-clamscan extension
Initializing nautilus-gdu extension
Initializing nautilus-image-converter extension
sys:1: GtkWarning: Undo: missing action Undo
sys:1: GtkWarning: Redo: missing action Redo
sys:1: GtkWarning: Reset to Defaults: missing action Reset to Defaults
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

sys:1: GtkWarning: Icon size name 'GTK_ICON_SIZE_STATUSBAR' already exists
sys:1: GtkWarning: Icon size name 'GTK_ICON_SIZE_CELLRENDERER' already exists

```

I used Ambience theme. I changed it to Elementary, and I have run Nautilus again, and it was even worse:
```
** (nautilus:4361): WARNING **: Pixbuf theme: Cannot load pixmap file /usr/share/themes/elementary/gtk-2.0/Apps: Image file '/usr/share/themes/elementary/gtk-2.0/Apps' contains no data

sys:1: GtkWarning: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed
sys:1: GtkWarning: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (nautilus:4361): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/elementary/gtk-2.0/Apps,
borders don't fit within the image
sys:1: GtkWarning: gdk_pixbuf_get_n_channels: assertion `GDK_IS_PIXBUF (pixbuf)' failed
sys:1: GtkWarning: gdk_pixbuf_get_pixels: assertion `GDK_IS_PIXBUF (pixbuf)' failed
sys:1: GtkWarning: gdk_pixbuf_get_rowstride: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (nautilus:4361): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/elementary/gtk-2.0/Apps,
borders don't fit within the image
```

I decided to restart computer.

After that, all my window borders are gone and my pointer was black X.
I opened terminal and typed:
```
**user@Ubuntu:~$ compiz --replace**
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Starting gtk-window-decorator
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
```

As soon as I close terminal, window manager is dead again.

I *googled* and I tried many things, but it's like I'm running in circles, always at beginning, at same spot.

Any advices, please? :confused:

---

### Post by krtica on 2010-11-08
Places menu fixed by issuing:

```
gconftool-2 -s /desktop/gnome/url-handlers/file/command -t string "nautilus \"%s\""
gconftool-2 -s /desktop/gnome/url-handlers/file/enabled -t bool true
```

---

### Post by blazemore on 2010-11-08
Sounds like a driver issue.

Hit Ctrl + Alt + F1 to enter a terminal away from X.

Log in with your normal username and password

Then do
```

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by krtica on 2010-11-08
Unfortunately, didn't help.
:(

I also made two scripts.

First to remove:
```
#!/bin/bash
sudo apt-get --purge remove alacarte
sudo apt-get --purge remove app-install-data-commercial
sudo apt-get --purge remove apport-gtk
sudo apt-get --purge remove apturl
sudo apt-get --purge remove at-spi
sudo apt-get --purge remove binfmt-support
sudo apt-get --purge remove bluez-gnome
sudo apt-get --purge remove brasero
sudo apt-get --purge remove brltty-x11
sudo apt-get --purge remove capplets-data
sudo apt-get --purge remove cli-common
sudo apt-get --purge remove compiz
sudo apt-get --purge remove compiz-core
sudo apt-get --purge remove compiz-fusion-plugins-extra
sudo apt-get --purge remove compiz-fusion-plugins-main
sudo apt-get --purge remove compiz-gnome
sudo apt-get --purge remove compiz-plugins
sudo apt-get --purge remove compizconfig-backend-gconf
sudo apt-get --purge remove contact-lookup-applet
sudo apt-get --purge remove dcraw
sudo apt-get --purge remove deskbar-applet
sudo apt-get --purge remove desktop-file-utils
sudo apt-get --purge remove dmz-cursor-theme
sudo apt-get --purge remove doc-base
sudo apt-get --purge remove docbook-xml
sudo apt-get --purge remove ekiga
sudo apt-get --purge remove eog
sudo apt-get --purge remove espeak
sudo apt-get --purge remove espeak-data
sudo apt-get --purge remove evince
sudo apt-get --purge remove evolution
sudo apt-get --purge remove evolution-common
sudo apt-get --purge remove evolution-data-server
sudo apt-get --purge remove evolution-data-server-common
sudo apt-get --purge remove evolution-exchange
sudo apt-get --purge remove evolution-plugins
sudo apt-get --purge remove evolution-webcal
sudo apt-get --purge remove example-content
sudo apt-get --purge remove f-spot
sudo apt-get --purge remove fast-user-switch-applet
sudo apt-get --purge remove file-roller
sudo apt-get --purge remove firefox
sudo apt-get --purge remove firefox-3.0
sudo apt-get --purge remove firefox-3.0-branding
sudo apt-get --purge remove firefox-3.0-gnome-support
sudo apt-get --purge remove firefox-gnome-support
sudo apt-get --purge remove gamin
sudo apt-get --purge remove gcalctool
sudo apt-get --purge remove gconf-editor
sudo apt-get --purge remove gconf2
sudo apt-get --purge remove gconf2-common
sudo apt-get --purge remove gdebi
sudo apt-get --purge remove gdm
sudo apt-get --purge remove gdm-guest-session
sudo apt-get --purge remove gedit
sudo apt-get --purge remove gedit-common
sudo apt-get --purge remove ggzcore-bin
sudo apt-get --purge remove gimp
sudo apt-get --purge remove gimp-data
sudo apt-get --purge remove gksu
sudo apt-get --purge remove gnome-about
sudo apt-get --purge remove gnome-accessibility-themes
sudo apt-get --purge remove gnome-app-install
sudo apt-get --purge remove gnome-applets
sudo apt-get --purge remove gnome-applets-data
sudo apt-get --purge remove gnome-cards-data
sudo apt-get --purge remove gnome-control-center
sudo apt-get --purge remove gnome-desktop-data
sudo apt-get --purge remove gnome-doc-utils
sudo apt-get --purge remove gnome-games
sudo apt-get --purge remove gnome-games-data
sudo apt-get --purge remove gnome-icon-theme
sudo apt-get --purge remove gnome-keyring
sudo apt-get --purge remove gnome-mag
sudo apt-get --purge remove gnome-media
sudo apt-get --purge remove gnome-media-common
sudo apt-get --purge remove gnome-menus
sudo apt-get --purge remove gnome-mime-data
sudo apt-get --purge remove gnome-mount
sudo apt-get --purge remove gnome-netstatus-applet
sudo apt-get --purge remove gnome-nettool
sudo apt-get --purge remove gnome-orca
sudo apt-get --purge remove gnome-panel
sudo apt-get --purge remove gnome-panel-data
sudo apt-get --purge remove gnome-pilot
sudo apt-get --purge remove gnome-pilot-conduits
sudo apt-get --purge remove gnome-power-manager
sudo apt-get --purge remove gnome-screensaver
sudo apt-get --purge remove gnome-session
sudo apt-get --purge remove gnome-settings-daemon
sudo apt-get --purge remove gnome-spell
sudo apt-get --purge remove gnome-system-monitor
sudo apt-get --purge remove gnome-system-tools
sudo apt-get --purge remove gnome-terminal
sudo apt-get --purge remove gnome-terminal-data
sudo apt-get --purge remove gnome-themes
sudo apt-get --purge remove gnome-user-guide
sudo apt-get --purge remove gnome-utils
sudo apt-get --purge remove gstreamer0.10-alsa
sudo apt-get --purge remove gstreamer0.10-gnomevfs
sudo apt-get --purge remove gstreamer0.10-plugins-base
sudo apt-get --purge remove gstreamer0.10-plugins-base-apps
sudo apt-get --purge remove gstreamer0.10-plugins-good
sudo apt-get --purge remove gstreamer0.10-pulseaudio
sudo apt-get --purge remove gstreamer0.10-schroedinger
sudo apt-get --purge remove gstreamer0.10-tools
sudo apt-get --purge remove gstreamer0.10-x
sudo apt-get --purge remove gtk2-engines
sudo apt-get --purge remove gtk2-engines-murrine
sudo apt-get --purge remove gtk2-engines-pixbuf
sudo apt-get --purge remove gucharmap
sudo apt-get --purge remove guile-1.8-libs
sudo apt-get --purge remove gvfs
sudo apt-get --purge remove gvfs-backends
sudo apt-get --purge remove gvfs-bin
sudo apt-get --purge remove gvfs-fuse

```

than issued: ```
sudo apt-get autoremove
``` to clean

and second do install again:

```
#!/bin/bash
sudo apt-get -y install alacarte
sudo apt-get -y install app-install-data-commercial
sudo apt-get -y install apport-gtk
sudo apt-get -y install apturl
sudo apt-get -y install at-spi
sudo apt-get -y install binfmt-support
sudo apt-get -y install bluez-gnome
sudo apt-get -y install brasero
sudo apt-get -y install brltty-x11
sudo apt-get -y install capplets-data
sudo apt-get -y install cli-common
sudo apt-get -y install compiz
sudo apt-get -y install compiz-core
sudo apt-get -y install compiz-fusion-plugins-extra
sudo apt-get -y install compiz-fusion-plugins-main
sudo apt-get -y install compiz-gnome
sudo apt-get -y install compiz-plugins
sudo apt-get -y install compizconfig-backend-gconf
sudo apt-get -y install contact-lookup-applet
sudo apt-get -y install dcraw
sudo apt-get -y install deskbar-applet
sudo apt-get -y install desktop-file-utils
sudo apt-get -y install dmz-cursor-theme
sudo apt-get -y install doc-base
sudo apt-get -y install docbook-xml
sudo apt-get -y install ekiga
sudo apt-get -y install eog
sudo apt-get -y install espeak
sudo apt-get -y install espeak-data
sudo apt-get -y install evince
sudo apt-get -y install evolution
sudo apt-get -y install evolution-common
sudo apt-get -y install evolution-data-server
sudo apt-get -y install evolution-data-server-common
sudo apt-get -y install evolution-exchange
sudo apt-get -y install evolution-plugins
sudo apt-get -y install evolution-webcal
sudo apt-get -y install example-content
sudo apt-get -y install f-spot
sudo apt-get -y install fast-user-switch-applet
sudo apt-get -y install file-roller
sudo apt-get -y install firefox
sudo apt-get -y install firefox-3.0
sudo apt-get -y install firefox-3.0-branding
sudo apt-get -y install firefox-3.0-gnome-support
sudo apt-get -y install firefox-gnome-support
sudo apt-get -y install gamin
sudo apt-get -y install gcalctool
sudo apt-get -y install gconf-editor
sudo apt-get -y install gconf2
sudo apt-get -y install gconf2-common
sudo apt-get -y install gdebi
sudo apt-get -y install gdm
sudo apt-get -y install gdm-guest-session
sudo apt-get -y install gedit
sudo apt-get -y install gedit-common
sudo apt-get -y install ggzcore-bin
sudo apt-get -y install gimp
sudo apt-get -y install gimp-data
sudo apt-get -y install gksu
sudo apt-get -y install gnome-about
sudo apt-get -y install gnome-accessibility-themes
sudo apt-get -y install gnome-app-install
sudo apt-get -y install gnome-applets
sudo apt-get -y install gnome-applets-data
sudo apt-get -y install gnome-cards-data
sudo apt-get -y install gnome-control-center
sudo apt-get -y install gnome-desktop-data
sudo apt-get -y install gnome-doc-utils
sudo apt-get -y install gnome-games
sudo apt-get -y install gnome-games-data
sudo apt-get -y install gnome-icon-theme
sudo apt-get -y install gnome-keyring
sudo apt-get -y install gnome-mag
sudo apt-get -y install gnome-media
sudo apt-get -y install gnome-media-common
sudo apt-get -y install gnome-menus
sudo apt-get -y install gnome-mime-data
sudo apt-get -y install gnome-mount
sudo apt-get -y install gnome-netstatus-applet
sudo apt-get -y install gnome-nettool
sudo apt-get -y install gnome-orca
sudo apt-get -y install gnome-panel
sudo apt-get -y install gnome-panel-data
sudo apt-get -y install gnome-pilot
sudo apt-get -y install gnome-pilot-conduits
sudo apt-get -y install gnome-power-manager
sudo apt-get -y install gnome-screensaver
sudo apt-get -y install gnome-session
sudo apt-get -y install gnome-settings-daemon
sudo apt-get -y install gnome-spell
sudo apt-get -y install gnome-system-monitor
sudo apt-get -y install gnome-system-tools
sudo apt-get -y install gnome-terminal
sudo apt-get -y install gnome-terminal-data
sudo apt-get -y install gnome-themes
sudo apt-get -y install gnome-user-guide
sudo apt-get -y install gnome-utils
sudo apt-get -y install gstreamer0.10-alsa
sudo apt-get -y install gstreamer0.10-gnomevfs
sudo apt-get -y install gstreamer0.10-plugins-base
sudo apt-get -y install gstreamer0.10-plugins-base-apps
sudo apt-get -y install gstreamer0.10-plugins-good
sudo apt-get -y install gstreamer0.10-pulseaudio
sudo apt-get -y install gstreamer0.10-schroedinger
sudo apt-get -y install gstreamer0.10-tools
sudo apt-get -y install gstreamer0.10-x
sudo apt-get -y install gtk2-engines
sudo apt-get -y install gtk2-engines-murrine
sudo apt-get -y install gtk2-engines-pixbuf
sudo apt-get -y install gucharmap
sudo apt-get -y install guile-1.8-libs
sudo apt-get -y install gvfs
sudo apt-get -y install gvfs-backends
sudo apt-get -y install gvfs-bin
sudo apt-get -y install gvfs-fuse

```

But the only thing i have done is that I manage to lose applets in uper right corner - user and power.

Stupid. Very stupid of me. :D

---

### Post by krtica on 2010-11-08
Ok. The applet is Indicator-Applet-Session. Good to know. :D
Can be easily installed trough Ubuntu Software Center.
The best learning process is by making mistakes. But painful too. :D

Any more ideas for my broken window manager? :confused:

---

### Post by wojox on 2010-11-08
Did you enable the window decorator in CCSM?

---

### Post by krtica on 2010-11-08
I assume CCSM is CompizConfig Settings Manager? :confused:
If it is, than Window Decoration is checked.

I'm 66% sure it's about Compiz. :/
But I just don't know how to repair it.

First of all, I'm not even sure how did I broke it.
The last app. I installed was Sweet Home 3D from GetDeb, but I never even run it.

Usually, when I broke something, I know where to start, becouse I know what I have done.
(And I manage to broke many things since Ubuntu 5.10 :D )

But this time, - I really don't know what caused this...


PS: I tried to clean/delete ~/.config/gnome-session/saved-session
No luck. :/

---

### Post by krtica on 2010-11-08
```
**$ compiz --debug**
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libcore.so : No such file or directory
compiz (core) - Debug: Could not stat() file /usr/lib/compiz/libcore.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libccp.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libmove.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libresize.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libplace.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libdecoration.so : No such file or directory
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Starting gtk-window-decorator
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libdbus.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libmousepoll.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libgnomecompat.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libpng.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libsvg.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libimgjpeg.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libtext.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libcommands.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libneg.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libwall.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libsnap.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libanimation.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libscale.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libscaleaddon.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libexpo.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libstaticswitcher.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libregex.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libresizeinfo.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libworkarounds.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libezoom.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libvpswitch.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libfade.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/alen/.compiz/plugins/libsession.so : No such file or directory
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
```

:confused:
I checked my last rsync backup - I never had plugins directory...

---

### Post by krtica on 2010-11-08
Well... Nothing I tried helps.
It smells as Clean Install Spirit... :)

During intensive *googling* I found that many people had same issue. But I didn't find any solution for 10.04 Lucid. Most off them are simply reinstall Ubuntu.
All my brain usage was hopeless as well, but it's not a surprise. I'm not quite expert on Linux. :D

Anyway, I wont give up for some time, yet. My temporary solution is startup script:

```
#!/bin/bash
compiz --replace
```

which is far from solution, but at least I have my window decorations (min, max, close buttons, borders etc.)

If anyone can suggest anything, I'll gladly try.

Thank you.

---

