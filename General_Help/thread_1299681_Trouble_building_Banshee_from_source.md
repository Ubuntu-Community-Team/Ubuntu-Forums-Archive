---
title: "Trouble building Banshee from source"
date: 2009-10-24
forum: General Help
---

### Post by exutable on 2009-10-24
Hey guys,

I'm trying to build banshee from source but can't seem to get it working.  It wants ipod-sharp but libipod-cil is already installed.

This is what I get when I run ./configure --disable-docs

```
checking for GTKSHARP... yes
checking for GLIBSHARP... yes
checking for SQLITE... yes
checking for GCONFSHARP... yes
checking for GNOMESHARP... yes
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for LIBMTP... yes
checking for struct LIBMTP_track_struct.modificationdate... no
checking for IPODSHARP... no
configure: error: ipod-sharp was not found or is not up to date. Please install ipod-sharp of at least version 0.8.1, or disable iPod support by passing --disable-ipod

```

---

### Post by yermandu on 2010-01-12
Same here.

---

