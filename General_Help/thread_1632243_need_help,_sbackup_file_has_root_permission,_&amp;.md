---
title: "need help, sbackup file has root permission, &amp; I can't copy the backup file to DVD"
date: 2010-11-27
forum: General Help
---

### Post by daaussie on 2010-11-27
Hi, I did a backup to my local desktop of all my files, now I want to copy to the cd-rom, so I can take the information to another location.

The only problem is, that the backup file has permissions locked to root. I thought I was logged into root?? I wouldn't know how to do this, I thought was user name was root, and I am obviously logged in, so it should be fine.

I couldn't even change the permissions, it's all locked...

Any help, with details for a novice to understand please...

---

### Post by Wobblybob on 2010-11-27
Ubuntu does not let you us root account as default but you can use it on a temp basis. To open a root instance of nautilus [the file eplorer] open a Terminal [Applications], [Accesories], [Terminal] and type after the prompt
gksudo nautilus
and press enter, a box will open and ask for your password, enter it [you will not see any text on the screen] and press enter. nautilus will now open with root permissions, just navigate to where your file is stored, right click on it select permissions and amend then to your user name. Close Nautilus after you have done this to close the root session.

---

### Post by daaussie on 2010-11-28
Thanks, i tried it, changed permissions, copying to disc, then when it tried to burn, it came up with: Error while burning. File "excludes" could not be opened (Permission denied).

Do you know what I can do about this?

---

### Post by Wobblybob on 2010-11-28
may still be a permissions problem, did you give yourself read/write, your group read and other read access to this file? what software are you using to burn with? I prefer k3b which works on Gnome as well as KDE desktops.

---

### Post by daaussie on 2010-11-28
Solved - Ok, its fixed now. I found that the tar and backup files themselves hadn't changed permissions, even though I had done the parent directory.
Thanks for your help.

---

