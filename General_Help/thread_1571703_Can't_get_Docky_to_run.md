---
title: "Can't get Docky to run"
date: 2010-09-10
forum: General Help
---

### Post by Prominence on 2010-09-10
here's the terminal output...and I kinda need docky to work seeing as its my taskbar-ish thing. 


grayson@Providence:~$ docky

** (/usr/local/lib/docky/Docky.exe:16315): WARNING **: The following assembly referenced from /usr/local/lib/docky/Docky.exe could not be loaded:
     Assembly:   gio-sharp    (assemblyref_index=10)
     Version:    2.14.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/local/lib/docky/).


** (/usr/local/lib/docky/Docky.exe:16315): WARNING **: Could not load file or assembly 'gio-sharp, Version=2.14.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

Unhandled Exception: System.TypeLoadException: A type load exception has occurred.
grayson@Providence:~$

---

### Post by kerry_s on 2010-09-10
uninstall it & then reinstall it.

make sure you have a composting manager(compiz, metacity, xcompmgr)
the ppa version is more up to date.

---

### Post by Prominence on 2010-09-10
I've tried, no luck

---

