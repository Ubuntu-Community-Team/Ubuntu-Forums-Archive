---
title: "Ubuntu Trash Can Deleted"
date: 2009-11-13
forum: General Help
---

### Post by GreenDance on 2009-11-13
Hi, I've just deleted my trash can, I went Right Click and Add but the Trash Can isn't in the list, is this a bug (missing Trash Can from the list) Ubuntu 9.10

---

### Post by kestrel1 on 2009-11-13
> **GreenDance said:**
> Hi, I've just deleted my trash can, I went Right Click and Add but the Trash Can isn't in the list, is this a bug (missing Trash Can from the list) Ubuntu 9.10
Try Deleted Items folder.

---

### Post by Ian dewhurst on 2009-11-13
This should be in another category but what the heck.

Your a bit vague by i just deleted my trash can. From where? the panel as i imagine it you can't right click on the panel and add "deleted items"?

if you want deleted items on your desktop:

gconf-editor /apps/nautilus/desktop

and then there should be an item for trash_icon_visible (if memeory serves me correct)

---

### Post by RiceMonster on 2009-11-13
I think you mean you deleted it from your bookmarks?

try going to trash:// in nautilus, then adding that to your bookmarks.

---

### Post by Mornedhel on 2009-11-13
worksforme

(Next time, if you wish to report a bug, report it at bugs.launchpad.net, or run apport.)

(I do have a Trash applet in the list, if that's what you're referring to.)

---

### Post by kestrel1 on 2009-11-13
> **Mornedhel said:**
> worksforme

(Next time, if you wish to report a bug, report it at bugs.launchpad.net, or run apport.)

(I do have a Trash applet in the list, if that's what you're referring to.)
It isn't a bug, so why report it as a bug. If it has been deleted from the panel adding the Deleted Items Folder, as I said earlier will sort it.

---

