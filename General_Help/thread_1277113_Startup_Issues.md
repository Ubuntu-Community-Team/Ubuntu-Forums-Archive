---
title: "Startup Issues"
date: 2009-09-27
forum: General Help
---

### Post by LoREZ on 2009-09-27
OK, I've looked everywhere in this forum, and I haven't found an answer to this particular issue.  Let me preface this by saying that I already know about System>Preferences>Startup Applications; it doesn't work.  I've purged the installation; it doesn't work.

OK, here's the problem: I'm trying to get Gnome Do to startup after login in Gnome and it won't.  I've got to do it manually now.  My version is 0.8.1.3, which I'm trying to use to replace AWN.

Here is my ~/.config/autostart/gnome-do.desktop file:

```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=GNOME Do
Type=Application
Exec=/usr/bin/gnome-do
Terminal=false
Icon=gnome-do
Comment=Do things as quickly as possible (but no quicker) with your files, bookmarks, applications, music, contacts, and more!
Categories=Utility;
X-GNOME-Autostart-enabled=false
Hidden=true
Name[en_US]=GNOME Do
Comment[en_US]=Do things as quickly as possible (but no quicker) with your files, bookmarks, applications, music, contacts, and more!
```

While I can make logical inferences, I don't know for sure what everyone of these tags does.  First off, I don't get why it says version 1, and I'm guessing that perhaps "X-GNOME-Autostart-enabled=false" should say true. Also "Hidden=true" is likely problematic, and maybe the "Comment" tag shouldn't appear twice.  Any suggestions?  Am I just looking in the wrong place to begin with?

Thanks for any help.

---

