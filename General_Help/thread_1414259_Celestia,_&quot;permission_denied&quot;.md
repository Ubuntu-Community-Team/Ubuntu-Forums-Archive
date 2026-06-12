---
title: "Celestia, &quot;permission denied&quot;"
date: 2010-02-23
forum: General Help
---

### Post by eveningsky339 on 2010-02-23
Hello.  I just now installed Celestia, and I was in the process of installing a few addons.  In order to do this, files must be copied into the /usr/share/celestia.  However, I cannot do this.  I keep receiving a "permission denied" message, even after running sudo -i in the terminal.

Is there any way I can get rid of this "permission denied" stuff???

---

### Post by thatguruguy on 2010-02-23
First, make sure that celestia hasn't created a directory in your home directory for add-ons. It would probably be entitled something like ".celestia", and you'll have to use the "show hidden files" option in nautilus (or whatever your file viewing program is).

If not, and you still want to copy files into the /usr/share/celestia directory, the easiest way I've found is opening nautilus with super user permissions by opening the Run Application popup by pressing Alt-F2 and then typing "gksu nautilus" (without the quotes).  Then you'll have full access to all directories.

Let me know if that worked.

---

### Post by eveningsky339 on 2010-02-23
I had searched for a .celestia folder earlier, to no avail.  However, I did what you advised, and everything appears to be working now.  Thanks a bunch!

---

