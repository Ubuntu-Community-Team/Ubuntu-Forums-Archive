---
title: "Trouble Installing GTK+3"
date: 2011-05-23
forum: General Help
---

### Post by jesuisbenjamin on 2011-05-23
Hello,

I am trying to go through the [horrible process of installing Gtk+3 libraries]("http://developer.gnome.org/gtk3/3.0/gtk-building.html").

First I need to install dependencies and so far I installed Glib-2.29.4, Pango-1.21.5 and now I am trying to install Atk-1.30.0.

First I got the following issue after running the [FONT="Courier New"]configure[/FONT] script:
```

checking for GLIB - version >= 2.0.0...
*** 'pkg-config --modversion glib-2.0' returned 2.29.4, but GLIB (2.28.6)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.0.0 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/. If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.

```

Indeed I found out that the .pc file was located at [FONT="Courier New"]/usr/lib/i386-linux-gnu/pkgconfig/glib-2.0.pc[/FONT]. So I followed [guidelines]("http://www.linuxquestions.org/questions/linux-software-2/pkg_config_path-230545/") and did:
```

export PKG_CONFIG_PATH="/usr/lib/i386-linux-gnu/pkgconfig:$PKG_CONFIG_PATH"

```

This helped moving on.
**Question 1:** Why was the configuration file installed somewhere where it couldn't be found? I don't really understand why there is not _one_ configuration repository for all packages. Can someone explain to me what information I am missing to understand the processes behind this?

There is yet another problem installing Atk however. The [FONT="Courier New"]configuration[/FONT] script returned further errors, below are the last lines (full log in attachment):

```

...
...
./configure: line 12175: ./po/POTFILES.in: No such file or directory
checking for bind_textdomain_codeset... (cached) yes
checking for gobject-introspection... no
checking whether to build gtk-doc documentation... no
checking for gtkdoc-check... no
checking for gawk... (cached) gawk
checking for perl5... no
checking for perl... perl
configure: creating ./config.status
config.status: creating Makefile
config.status: creating po/Makefile.in
config.status: creating atk.pc
config.status: creating atk-uninstalled.pc
config.status: error: cannot find input file: `atk/Makefile.in'

```[B]

Question 2:[/B] Could anyone help me with this last big?
I'd like to learn from this and document the installation to make it easy for others, so help is welcome.

Cheers,
Benjamin

---

### Post by jesuisbenjamin on 2011-05-23
**Work around question 2:** I could install ATK from repository:

```

sudo apt-get install libatk1.0*

```

---

### Post by jesuisbenjamin on 2011-05-24
Installation was a pain, but it worked out well in the end. I added a [guideline]("http://gtk3lab.blogspot.com/2011/05/installing-gtk3-and-pygobject.html") for Gtk+3 and PyGI installation to complement the official documentation. It may not be perfect, let me know if i should add/correct info on that.

---

