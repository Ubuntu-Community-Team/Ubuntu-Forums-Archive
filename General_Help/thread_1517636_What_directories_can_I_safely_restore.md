---
title: "What directories can I safely restore?"
date: 2010-06-25
forum: General Help
---

### Post by BurningSludge on 2010-06-25
[FONT=Comic Sans MS][SIZE=3]Just in case I have some kind of error (again) I am wondering what directories I could restore without causing a boot error or force me to play with configure files using a live disk on the next reboot.

List of directories I could restore that I know won't cause a boot error.
[/SIZE][/FONT]
[LIST]
[*][FONT=Comic Sans MS][SIZE=3]home
[/SIZE][/FONT]
[/LIST]

---

### Post by bobcollard on 2010-06-25
> **BurningSludge said:**
> [FONT=Comic Sans MS][SIZE=3]Just in case I have some kind of error (again) I am wondering what directories I could restore without causing a boot error or force me to play with configure files using a live disk on the next reboot.

List of directories I could restore that I know won't cause a boot error.
[/SIZE][/FONT]
[LIST]
[*][FONT=Comic Sans MS][SIZE=3]home
[/SIZE][/FONT]
[/LIST]

Basically it is safe to say the directories normally visible in home, not the hidden ones which are config files.  Those are your personal information files like Documents, Music, Pictures, Public, Templates and Videos.  It helps to keep a list of your installed Applications so you can easily replace them, they may be updated so don't keep the original installers, or packages.

---

### Post by BurningSludge on 2010-06-25
[FONT=Comic Sans MS][SIZE=3]What about the usr, bin and sbin?[/SIZE][/FONT]

---

### Post by lsutiger on 2010-06-25
During backup, you would want to backup your mail files and bookmarks, which are usually located in a hidden folder of your home directory, IE home/user/.mozilla-thunderbird/ holds my mail

---

