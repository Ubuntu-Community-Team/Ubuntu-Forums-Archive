---
title: "Evolution 2.30 will no longer load"
date: 2011-01-27
forum: General Help
---

### Post by xenall on 2011-01-27
Evolution has been working fine, then it just will not load.  I typed evolution it in the terminal and received the following errors.

evolution: /usr/local/lib/libxml2.so.2: no version information available (required by evolution)
evolution: /usr/local/lib/libxml2.so.2: no version information available (required by /usr/lib/evolution/2.30/libeshell.so.0)
evolution: /usr/local/lib/libxml2.so.2: no version information available (required by /usr/lib/evolution/2.30/libmenus.so.0)
evolution: /usr/local/lib/libxml2.so.2: no version information available (required by /usr/lib/evolution/2.30/libeutil.so.0)
evolution: /usr/local/lib/libxml2.so.2: no version information available (required by /usr/lib/evolution/2.30/libeutil.so.0)
evolution: /usr/local/lib/libxml2.so.2: no version information available (required by /usr/lib/evolution/2.30/libfilter.so.0)
evolution: /usr/local/lib/libxml2.so.2: no version information available (required by /usr/lib/libebook-1.2.so.9)
evolution: /usr/local/lib/libxml2.so.2: no version information available (required by /usr/lib/libedataserver-1.2.so.13)
evolution: /usr/local/lib/libxml2.so.2: no version information available (required by /usr/lib/libsoup-2.4.so.1)
evolution: /usr/local/lib/libxml2.so.2: no version information available (required by /usr/lib/libgdata-1.2.so.1)
evolution: /usr/local/lib/libxml2.so.2: no version information available (required by /usr/lib/libgdata-1.2.so.1)
evolution: /usr/local/lib/libxml2.so.2: no version information available (required by /usr/lib/evolution/2.30/libetable.so.0)

[COLOR=black]
[/COLOR] [COLOR=black](evolution:27614): e-utils-WARNING **: Lock file creation failed: No such file or directory

(evolution:27614): e-utils-WARNING **: /usr/lib/evolution/2.30/modules/libevolution-module-mail.so: symbol xmlFirstElementChild, version LIBXML2_2.7.3 not defined in file libxml2.so.2 with link time reference
Failed to load module: /usr/lib/evolution/2.30/modules/libevolution-module-mail.so
evolution: relocation error: /usr/lib/evolution/2.30/libeutil.so.0: symbol xmlFirstElementChild, version LIBXML2_2.7.3 not defined in file libxml2.so.2 with link time reference[/COLOR]



I'm on Ubuntu 10.10, and have tried to update, un-install (and purge), reinstall - same errors.  Then I un-installed (purged) and deleted all evolution folders and files (re-installed gnome-panel - it was deleted when I manually removed the evolution files), then reinstalled.  same errors..:(

I've tried to install and un-install through the terminal, synaptic package manager and through the software center, with no luck.

If someone could please give me some direction, or ideas on what to try next, I would greatly appreciate it.


Thank you

Samantha

---

### Post by xenall on 2011-01-27
I figured it out.  Reloaded the libxml files.

[http://packages.ubuntu.com/maverick-updates/i386/libxml2/download](http://packages.ubuntu.com/maverick-updates/i386/libxml2/download)

:P

---

