---
title: "&quot;Home&quot; Folders Appearing on &quot;Desktop&quot;"
date: 2011-01-10
forum: General Help
---

### Post by JustinChuTw on 2011-01-10
Hello All ...

Need your kind assistance to resolve a frustrating problem as described below:

Problem:
The contents of my "Home" folder ('Documents', 'Downloads', 'Music', 'Pictures', 'Public', 'Templates' and 'Videos') are appearing on my "Desktop".

Actions that I have taken to try to resolve the above problem:
1. Use "gconf-editor" to check and ensure that '>/>apps>nautilus>preference>desktop_is_home_dir' is disabled (unchecked).
2. My "/home/(my user name)/.config/user-dirs-dir" is showing XDG_DESKTOP_DIR="$HOME/", XDG_DOWNLOAD_DIR="$HOME/" and XDG_TEMPLATES_DIR="$HOME/" so I manually edited the above lines to XDG_DESKTOP_DIR="$HOME/Desktop", XDG_DOWNLOAD_DIR="$HOME/Downloads" and XDG_TEMPLATES_DIR="$HOME/Templates".
3. Since the folders 'Desktop', 'Downloads' and 'Templates' are missing in my "/home/(my user name)" directory, I use "Create Folder" to create 'Desktop', 'Downloads' and 'Templates' folders.
4. Re-started my computer and the "Home" folder no longer appear on my "Desktop".

The above basically are the instructions/procedures that I found in the various posts on this particular subject, but unfortunately, in my case, it seems like a temporary solution/workaround. After using my computer during the day, creating and storing and/or editing and re-storing various files, this problem will re-appear again the next day when I turn my computer on. While it is really no big deal to repeat the above procedures to get rid of my "Home" folder from my "Desktop" but having to repeat these procedures every morning when I first start my computer is getting to be a pain.

In addition to the above, I have also disable 'User Folders Update' from "System>Preferences>Startup Applications" so that 'xdg-user-dirs-gtk-update' will not run during the boot (startup) process but it does not seem to resolve the problem.

Now, the questions that I have are:
1. What application or process is assessing my 'user-dirs-dir' and repeatedly changing XDG_DESKTOP_DIR="$HOME/Desktop", XDG_DOWNLOAD_DIR="$HOME/Downloads" and XDG_TEMPLATES_DIR="$HOME/Templates" to XDG_DESKTOP_DIR="$HOME/", XDG_DOWNLOAD_DIR="$HOME/" and XDG_TEMPLATES_DIR="$HOME/".
2. Is there any way to prevent such application or process from changing the contents of my 'user-dirs-dir'?
3. As a last desperate resort, I am thinking of removing (uninstalling) both 'xdg-user-dirs-gtk-update' and 'xdg-user-dirs-update'. Will that prevent my 'user-dirs-dir' from being changed and will it affect the normal operation of my system?

I will appreciate it very much if someone can help me resolve this frustrating problem.

Justin

---

