---
title: "Restore environment variables"
date: 2010-12-16
forum: General Help
---

### Post by mynot on 2010-12-16
I seem to have lost all my directory shortcuts like Documents, Pictures etc, both those I added and those that were preset. Where would they be stored so I can get them from a backup? (I haven't specified anywhere myself, so it would be the 10.10 default).
Thanks
Tony

---

### Post by Wtower on 2010-12-16
Hm, what do you mean lost? Have you deleted them? Any chance that they can be found in the trash can? Have you moved them somewhere else? Have you issued any command in terminal that you don't know what it did? Are they important files or replaceable ones? Do you have a backup copy that you created (or instructed your system to do so)?

---

### Post by mynot on 2010-12-16
They were "lost" after a power outage. So they might well be still there somewhere, but I don't know how to get them back (other than re-entering them all again).
Tony

---

### Post by mynot on 2010-12-16
Well, simple solution really. Might've been better if I'd asked the right question. What I really wanted to do was restore my bookmarks. Took about 5 mins in Nautilus. But I still don't know where they're actually stored.
Tony

---

### Post by Wtower on 2010-12-17
Sorry, I'm afraid I still haven't quite understood what exactly is the issue to aid you. Do you mean you lost the locations menu on top panel (default)? Or the bookmarks stored? The bookmarks do not include documents, pictures, etc but rather user-defined locations.

For the first issue, try right clicking on a panel, add, menu toolbar. For the second, there should a hidden file in your home directory called .gtk-bookmarks. You can access hidden files with ctrl+h in nautilus or from terminal: gedit ~/.gtk-bookmarks

Regards

---

