---
title: "Problems with Places&gt;Computer,OS,D."
date: 2010-01-23
forum: General Help
---

### Post by Joey B. on 2010-01-23
When I look into them they become mounted on my desktop, so I unmount them and they aren't back in my Places section, can someone help?

---

### Post by quixote on 2010-01-25
You mean that you'd like those drives or partitions mounted, so you can access files inside them, but you just don't want them on your desktop?

Or do you mean that when you unmount them, they totally disappear which makes it hard to mount them again when you want to?

If you mean the first, that behavior is, unfortunately, considered a feature not a bug by the Gnome developers.  (Don't get me started on the whole way they handle mounting drives and naming them.)  The workaround is to go through a bunch of command line work to mount them in another directory, such as /mnt, rather than /media where Gnome puts them by default.

Let me know if that's what you want to do and I'll list the three or four commands for you.  It's not difficult, just a bit tedious.

---

### Post by sgosnell on 2010-01-25
If they're not mounted, they won't appear in Places.  Only mounted volumes appear there.  If you don't want the mounted volumes to appear on your desktop, you can change that by Alt-F2 (run program), and putting gconf-editor there, or by typing gconf-editor in a terminal.  Then on the left side panel of the editor, find Apps/Nautilus/Desktop, and uncheck the volumes_visible option.  Or you can install ubuntu-tweak and change it.

---

### Post by quixote on 2010-01-25
Yes, ubuntu-tweaks is a great program.  I should have remembered that.  I'm off to install it right now.

---

