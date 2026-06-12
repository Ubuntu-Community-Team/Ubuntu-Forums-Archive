---
title: "backup an ubuntu?linux system i general"
date: 2010-03-01
forum: General Help
---

### Post by joe1600 on 2010-03-01
hello
how to backup and which all FS to backup ir / ,/root./home/user...

so which all to backup..

like if i install 10.04 alpha3 i want all my users settings and say banshee player from 9.10  to be available on 10.04 alpha also..

ie the wallpaper..profile settings..etc...

please help out anyone

---

### Post by dabl on 2010-03-01
If it's really important to keep all your user settings, you probably should wait until after 10.04 is released, and use the upgrade button.  The reason is, because it is a new version, it is going to create new settings when you install it, and some of the old 9.10 settings might not be compatible.

If you want to try anyway, the user settings are in hidden folders in your /home/joe1600 folder.  So in your file manager, click "View > Show hidden" and it will let you see them.  Usually the names tell which application they are for. ".mozilla", ".vmware", ".audacity", etc. etc. Back up the ones that are important to you, and then you should be able to restore them after you install 10.04.

---

### Post by fouserge on 2010-03-01
There are a few applications out there, including in the repository, but I haven't gotten around trying them out yet. Another way is to just compress the folders you want. As dabl said, most of your user settings are stored in hidden files/folders in the home directory so I just typically compress that and copy it.

Linux is real nice in that you can backup the entire filesystem by going to the root / directory and just compressing it to another location.

---

