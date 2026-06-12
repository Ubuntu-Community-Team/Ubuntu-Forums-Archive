---
title: "gnome-open has problem :("
date: 2011-01-14
forum: General Help
---

### Post by alycann on 2011-01-14
can't open any directory
when I wrote to terminal 

$ gnome-open /home
$ 
Gtk-ERROR **: GTK+ 3 symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported
aborting...


I need your help [IMG]http://forum.linuxmint.com/images/smilies/icon_sad.gif[/IMG]

I'M using Linux Mint Debian 64

---

### Post by TeoBigusGeekus on 2011-01-14
> **alycann said:**
> ...Using GTK+ 2.x and GTK+ 3 in the same process is not supported
It complaints about the existence of both gtk2 and 3. Have you installed both? Try removing gtk3.

---

### Post by josepaul on 2011-01-14
Have you tried googling it? It seems many people have this same problem.

---

### Post by alycann on 2011-01-14
I was using gnome3
I just added debian experimantel resporities
and I did apt-get upgrade

what must I do now ? 
am I using gnome2 now?How can I turn back ?

---

### Post by TeoBigusGeekus on 2011-01-14
Post us the output of
```
dpkg -l | grep gtk
```

---

### Post by alycann on 2011-01-14
sorry before I wasn't using gnome3, I was using gtk+3
here are results dpkg -l | grep gtk


:~$ dpkg -l | grep gtk
ii  compiz-gtk                           0.8.4-4                           OpenGL window and compositing manager - Gtk window decorator
rc  gir1.0-gtk-2.0                       0.6.5-7                           GObject introspection data for the GTK+ library
ii  gir1.2-gtk-2.0                       2.23.90-1                         The GTK+ graphical user interface library -- gir bindings
ii  gir1.2-gtk-3.0                       2.99.2-1                          The GTK+ graphical user interface library -- gir bindings
ii  google-gadgets-gtk                   0.11.2-3                          GTK+ Version of Google Gadgets
ii  gtk2-engines                         1:2.20.1-1                        theme engines for GTK+ 2.x
ii  gtk2-engines-aurora                  1.5.1~pablo1-1mint1               Aurora engine for GTK+ 2.x
ii  gtk2-engines-candido                 0.9.1-pablo4                      Candido engine for GTK+ 2.x
ii  gtk2-engines-murrine                 0.90.3+git20100323-0ubuntu3       cairo-based gtk+-2.0 theme engine
ii  gtk2-engines-pixbuf                  2.23.90-1                         Pixbuf-based theme for GTK+ 2.x
ii  gtk3-engines                         1:2.91.1-1+b1                     theme engines for GTK+ 3.x
ii  gtk3-engines-pixbuf                  2.99.2-1                          Pixbuf-based theme for GTK+ 3.x
ii  libcanberra-gtk-module               0.26-2                            translates Gtk+ widgets signals to event sounds
ii  libcanberra-gtk0                     0.26-2                            Gtk+ helper for playing widget event sounds with libcanberra
ii  libcanberra-gtk3-0                   0.26-2                            Gtk+ 3.0 helper for playing widget event sounds with libcanberra
ii  libcanberra-gtk3-module              0.26-2                            translates Gtk3 widgets signals to event sounds
ii  libclutter-gtk-0.10-0                0.10.8-1                          Open GL based interactive canvas library GTK+ widget
ii  libgdu-gtk0                          2.30.1-2                          GTK+ standard dialog library for libgdu
ii  libggadget-gtk-1.0-0b                0.11.2-3                          Google Gadgets GTK+ library
ii  libgtk2-perl                         2:1.222-1                         Perl interface to the 2.x series of the Gimp Toolkit library
ii  libgtk2.0-0                          2.23.90-1                         The GTK+ graphical user interface library
ii  libgtk2.0-bin                        2.23.90-1                         The programs for the GTK+ graphical user interface library
ii  libgtk2.0-cil                        2.12.10-1                         CLI binding for the GTK+ toolkit 2.12
ii  libgtk2.0-common                     2.23.90-1                         Common files for the GTK+ graphical user interface library
ii  libgtk3.0-0                          2.99.2-1                          The GTK+ graphical user interface library
ii  libgtk3.0-bin                        2.99.2-1                          The programs for the GTK+ graphical user interface library
ii  libgtk3.0-common                     2.99.2-1                          Common files for the GTK+ graphical user interface library
ii  libgtkhtml-editor-common             3.30.3-1                          HTML rendering/editing library - editor widget data
ii  libgtkhtml-editor0                   3.30.3-1                          HTML rendering/editing library - editor widget
ii  libgtkhtml3.14-19                    3.30.3-1                          HTML rendering/editing library - runtime files
ii  libgtkimageview0                     1.6.4-1                           image viewer widget for GTK+
ii  libgtkmm-2.4-1c2a                    1:2.20.3-1                        C++ wrappers for GTK+ (shared libraries)
ii  libgtksourceview2.0-0                2.10.4-1                          shared libraries for the GTK+ syntax highlighting widget
ii  libgtksourceview2.0-common           2.10.4-1                          common files for the GTK+ syntax highlighting widget
ii  libgtkspell0                         2.0.16-1                          a spell-checking addon for GTK's TextView widget
ii  libindicate-gtk2                     0.4.1-2                           library for raising indicators via DBus - GTK+ bindings
ii  libpolkit-gtk-1-0                    0.99-1                            PolicyKit GTK+ API
ii  libwxgtk2.8-0                        2.8.10.1-3+b1                     wxWidgets Cross-platform C++ GUI toolkit (GTK+ runtime)
ii  ndisgtk                              0.8.5-1                           graphical frontend for ndiswrapper (installation of Windows WiFi drivers)
ii  openoffice.org-gtk                   1:3.2.1-11                        office productivity suite -- GTK+ integration
ii  python-gtk2                          2.17.0-4                          Python bindings for the GTK+ widget set
ii  python-gtkmozembed                   2.25.3-6                          Python bindings for the GtkMozEmbed Gecko library
ii  python-gtksourceview2                2.10.1-1                          Python bindings for the GtkSourceView widget
ii  python-gtkspell                      2.25.3-6                          Python bindings for the GtkSpell library
ii  python-wxgtk2.8                      2.8.10.1-3+b1                     wxWidgets Cross-platform C++ GUI toolkit (wxPython binding)
ii  software-properties-gtk              0.70.debian-1                     manage the repositories that you install software from
ii  transmission-gtk                     2.11-1                  

I dont know what I did but now my all theme has changed it seems bad and I cant right click at my desktop

---

### Post by alycann on 2011-01-14
I think I deleted some gir when I was updating

---

### Post by alycann on 2011-01-14
I think I deleted some gir packages when I was updating

---

### Post by TeoBigusGeekus on 2011-01-14
Try this
```
sudo apt-get purge libgtk3.0-0 2.99.2-1
```
to remove gtk3
and then
```
sudo apt-get autoremove
```
to remove all its orphaned dependencies.

---

