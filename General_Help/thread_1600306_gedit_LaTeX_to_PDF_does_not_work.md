---
title: "gedit: LaTeX to PDF does not work"
date: 2010-10-18
forum: General Help
---

### Post by The Switch Blade on 2010-10-18
I am using the Gedit LaTeX Plugin 0.2 rc3 on ubuntu 10.04 with gedit 2.30.3.

The problem is that it will not make pdf files.

I do have rubber installed.

Thoughts?

[http://sourceforge.net/projects/gedit-latex/](http://sourceforge.net/projects/gedit-latex/)

---

### Post by The Switch Blade on 2010-10-19
bump

---

### Post by tachyon4 on 2011-05-15
bump

---

### Post by tachyon4 on 2011-08-27
I followed these instructions...

---

REQUIREMENTS

 - gedit >=2.15.2
 - Python >=2.6
 - PyGTK >=2.12
 - GTK+ >=2.10.14
 - PyEnchant (optional, needed for LaTeX spell checking)
 - Poppler Python Bindings (optional, needed for embedded PDF preview)

INSTALLATION

Just copy the contents of the archive (folder 'GeditLaTeXPlugin' and file 
'GeditLaTeXPlugin.gedit-plugin') to '~/.gnome2/gedit/plugins' where '~' 
is your home directory. You may have to create the folder 'plugins'.

Restart gedit and activate the plugin in the plugins configuration.

---

... and then installed rubber.  Everything works.

---

