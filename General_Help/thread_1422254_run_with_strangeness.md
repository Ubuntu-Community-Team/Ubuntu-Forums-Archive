---
title: "run with strangeness"
date: 2010-03-05
forum: General Help
---

### Post by CongoJim on 2010-03-05
My files in my home folder do not start with the default apps. First it would launch clamAV when I'd click on any file. I uninstalled clam and now I have to choose the program to open each file (including executables).
I can move the files to the desktop (gnome) and no problem. My permissions on the home folder are Read Write and Run for all.

Any idea what I've done?

---

### Post by ibuclaw on 2010-03-05
> **CongoJim said:**
> My files in my home folder do not start with the default apps. First it would launch clamAV when I'd click on any file. I uninstalled clam and now I have to choose the program to open each file (including executables).
I can move the files to the desktop (gnome) and no problem. My permissions on the home folder are Read Write and Run for all.

Any idea what I've done?

Looks like that antu virus software toyed with your "Open With" settings.

Open your Home folder, and show hidden files/folders (Ctrl+H). Then browse to the following directory path:
```
.local/share/applications
```
and rename the file
```
defaults.list
```
to
```
defaults.list.old
```
This will reset all file associations back to their system defaults.

You may need to logoff/login for the settings to take affect (that shouldn't be the case though).

Regards
Iain

---

### Post by CongoJim on 2010-03-05
No gold. It opens anything resembling a text file (.txt,.html,.pdf...) with gedit, the rest select aprogram with no suggestions.

---

