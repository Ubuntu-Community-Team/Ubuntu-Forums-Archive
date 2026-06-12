---
title: "how to link samba folder"
date: 2009-10-05
forum: General Help
---

### Post by afeasfaerw23231233 on 2009-10-05
For example, there is a shared folder [http://192.168.1.2/bob/share](http://192.168.1.2/bob/share) , how could I make a link using the **ln** command?

---

### Post by 3rdalbum on 2009-10-05
You can't create a link to a location that is not in your filesystem. You need to mount the share somewhere, and then make a link to where it's mounted.

If you want to create some sort of icon that you can click to mount the share, then you should mount it in Gnome and then add it to your bookmarks. Then you can either access it through the Places menu, or drag it from Places to your desktop or your panels to create a launcher.

---

### Post by afeasfaerw23231233 on 2009-10-05
Thanks for the detailed explanation!

---

