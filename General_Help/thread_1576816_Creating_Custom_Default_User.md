---
title: "Creating Custom Default User"
date: 2010-09-17
forum: General Help
---

### Post by lakerssuperman on 2010-09-17
I have been attempting to modify my /etc/skel so that all default users will be created with my user settings for theme, icons, etc.  I have nearly achieved success by copying

Folders:

.compiz
.config
.local
.gconf
.gconfd
.gnome2

Files:

.bash
.bashrc
.profile

The account that gets created has all of the theme and program settings correct.  However, none of the files that are typically found in home are created.  In fact, the new user's home folder is really the desktop.  Any file created in Nautilus, in what would be the home folder, appears on the desktop.  I would imagine there is simply a config file I am not copying that defines the new user's directory structure, but I don't know what file that may be.  Can anyone shed some light on this problem.  Thanks.

---

