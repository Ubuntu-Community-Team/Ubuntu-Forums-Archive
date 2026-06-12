---
title: "Restoring Network Manager"
date: 2011-06-03
forum: General Help
---

### Post by earl100 on 2011-06-03
Tried this query on new user board.  No success.

Ubuntu 10.10 on netbook.  Network manager got deleted via software center command.

How do I connect to wifii without it, in order to restore it?

Or, where can I download it to a sd card and install?  From where, and how?

Or, have natty installed on a new partition.  Can I transfer NM and install it, and if so, how?

Thanks for the attention.

Earl

---

### Post by wgarcia on 2011-06-04
If you have uninstalled it, from a terminal

sudo apt-get install network-manager

will install it back. 

If you can't see it in the upper panel, and you're using Gnome classic, right-click and add the Notification area to see it again.

---

### Post by whatthefunk on 2011-06-04
You can also reinstall it via the Debian files on the install CD.  Put the CD in, go to Pool > Main > N > NetworkManager (if I remember correctly...)  I think you have to install the program and the aplet separately, but I dont remember....

---

