---
title: "'Places-&gt;Videos': Could not open location 'file:///...'"
date: 2010-04-15
forum: General Help
---

### Post by el_sordo on 2010-04-15
I renamed /home to /localhome and I'm getting an error message when I run 'Places->Videos'. The error is: 'Could not open location 'file:///home/<username>/Videos' Error stating file '/home/<username>/Videos: No such file or directory.

I'm using /localhome because /home is used for automounting home directories at my work. I prefer to use a local account rather than the NIS/NFS account.

What do I modify to have this reflect my new home directory location?

Thanks in advance! :P

---

### Post by scottiw2000 on 2010-04-22
The list of folders in your "places" menu should just be the same shortcuts that appear in the left side-pane of Nautilus. Open a nautilus window, find the "videos" shortcut in that side-pane and right-click on it. Select "remove". Then drag your new videos folder (from /localhome) into the side-pane and a new shortcut should be created.

---

