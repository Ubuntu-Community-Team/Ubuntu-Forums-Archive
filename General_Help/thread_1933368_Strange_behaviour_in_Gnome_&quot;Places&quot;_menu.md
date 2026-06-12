---
title: "Strange behaviour in Gnome &quot;Places&quot; menu"
date: 2012-02-29
forum: General Help
---

### Post by wurlyfan on 2012-02-29
I'm having a strange problem and would really appreciate some help.  Whenever I select an item (folder, link or bookmark) from the Gnome  "Places" menu, two applications (Konqueror and VLC Media Player) open  instead of the file browser.

When I select the same link or bookmark from within Nautilus, the file browser opens as normal.

I think this dates back to an occasion when I tried (unsuccessfully) to  open a whole folder in VLC Media Player (foolish, I know!), but I can't  seem to correct the problem.

Can anyone point me in the right direction, please :confused:

Oh, I'm running 11.04 on an i386 box, with the classic desktop!

---

### Post by Krytarik on 2012-02-29
Open the file "~/.local/share/applications/mimeapps.list", and in the "[Added Associations]" section, make the entry for "inode/directory" look like this, or remove the line altogether:
```
[Added Associations]
inode/directory=nautilus-folder-handler.desktop;
```Regards.

---

### Post by wurlyfan on 2012-02-29
Many thanks for the info, Krytarik. Actually I also had to change the corresponding line in the [Default Applications] block, but your post was what I needed to sort it out. Thanks again!

---

