---
title: "Deleted directories return after restart (files too)"
date: 2010-01-23
forum: General Help
---

### Post by hoink on 2010-01-23
Whether I use rm from the shell, Delete from Gnome, or drag-to-trash-and-empty (in Gnome), I'm unable to permanently delete some directories.  They are successfully deleted, but magically reappear after reboot.

I stumbled across a launchpad entry that talked about it and there may have been a fix, but I can't seem to find it now.

---

### Post by falconindy on 2010-01-23
> **hoink said:**
> some directories..
Perhaps you could be a little more descriptive?

---

### Post by hoink on 2010-01-23
I really would like to offer more info, but I'm at a loss of what to add.

It really is that basic.  Files are deleted, and they return after reboot.  If you can offer some other factors I can describe or explore, that would actually help.

---

### Post by hoink on 2010-01-23
Thanks for prompting me to dig into describing the directories.  I had given up on detecting a pattern to the strangeness until I realized...

All the directories were involved with Deluge bittorrent client which was recreating the directories for even dormant, empty torrents.  (Boo!)

Thanks for replying.

---

