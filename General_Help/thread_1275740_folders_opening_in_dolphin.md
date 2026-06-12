---
title: "folders opening in dolphin"
date: 2009-09-26
forum: General Help
---

### Post by Zeroangel on 2009-09-26
I recently installed the kubuntu-desktop package and am having some problems with folders and URLs opening with dolphin. I do not like this behavior and prefer they open using the normal gnome method of opening files.

I already have the 'preferred applications' options set to open folders with nautilus and URLs with firefox. And while clicking on the 'home' folder on the desktop for example opens in nautilus, clicking on a folder in the 'places' menu wants to open it in dolphin.

In addition
```
david@icarus /etc/gnome $ cat defaults.list | grep directory
inode/directory=nautilus-folder-handler.desktop
x-directory/normal=nautilus-folder-handler.desktop
``````
david@icarus / $ locate nautilus-folder-handler.desktop
/usr/share/applications/nautilus-folder-handler.desktop
david@icarus / $ cat /usr/share/applications/nautilus-folder-handler.desktop
[Desktop Entry]
Encoding=UTF-8
Name=Open Folder
TryExec=nautilus
Exec=nautilus --no-desktop %U
NoDisplay=true
Terminal=false
Icon=folder-open
StartupNotify=true
Type=Application
MimeType=x-directory/gnome-default-handler;x-directory/normal;inode/directory;application/x-gnome-saved-search;
OnlyShowIn=GNOME;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.26.2
X-Ubuntu-Gettext-Domain=nautilus
```I'm puzzled.

---

### Post by Zeroangel on 2009-09-26
I changed my search query to "dolphin places gnome" and came up with this URL

[http://www.ignition-project.com/articles/2009/01/08/fix-dolphin-hijacks-the-gnome-places-menu](http://www.ignition-project.com/articles/2009/01/08/fix-dolphin-hijacks-the-gnome-places-menu)

Which worked.

---

