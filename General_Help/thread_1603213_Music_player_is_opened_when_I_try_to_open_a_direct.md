---
title: "Music player is opened when I try to open a directory"
date: 2010-10-22
forum: General Help
---

### Post by bo-bobo on 2010-10-22
Hi everyone,
when I try to open a directory via the Places menu in gnome desktop (Places->home|music|...) the default music player which comes with Ubuntu is opened (I don't know why), but not the directory.

Do you know, guys, why does this happen and/or how can I solve it? I'm using Ubuntu 10.10.

Thank you.

---

### Post by nothingspecial on 2010-10-22
[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10004751#post10004751") 				 				[I]Check ~/.local/share/applications

See if Totem is listed in defaults.list or mimeapps.list as opening directories[/I]

---

### Post by bo-bobo on 2010-10-22
Ok, it's now solved. The exact content of that file (~/.local/share/applications/mimeapps.list) was the following:

audio/x-ape=rhythmbox.desktop;
inode/directory=rhythmbox-device.desktop;

I've just deleted the last line and it seems to work fine.

Thank you again.

---

