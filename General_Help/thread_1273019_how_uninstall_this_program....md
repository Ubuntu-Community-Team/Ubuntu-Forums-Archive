---
title: "how uninstall this program..."
date: 2009-09-22
forum: General Help
---

### Post by mephist0pheles on 2009-09-22
Heroes of Newerth
I installed it, found out my computer can't run it, and now I can't uninstall it. It didn't come with a script to uninstall it. So, I went ahead and deleted the HoN directory with all of its information in it. Problem is, it's still on my Games menu. How do I remove it and is there anything else that I should remove in order to completely remove it from my computer? 

Btw, it didn't show up on synaptic or add/remove programs, so....

---

### Post by DeMus on 2009-09-22
> **mephist0pheles said:**
> Heroes of Newerth
I installed it, found out my computer can't run it, and now I can't uninstall it. It didn't come with a script to uninstall it. So, I went ahead and deleted the HoN directory with all of its information in it. Problem is, it's still on my Games menu. How do I remove it and is there anything else that I should remove in order to completely remove it from my computer? 

Btw, it didn't show up on synaptic or add/remove programs, so....

How did you install it? Using Synaptic or add/remove, or through codes in a terminal?
To get rid of the entry in the menu do this:
right-click Applications on the top panel and choose Edit menus
In the left column of the new window choose games
On the right untick the box in front of the game you deleted
Now it won't show up again the menu

---

### Post by eaglemob on 2009-09-22
[B]Try this in terminal

sudo apt-get autoremove programname

or

sudo apt-get --purge programname[/B]

---

