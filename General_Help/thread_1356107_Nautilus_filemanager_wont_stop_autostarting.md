---
title: "Nautilus filemanager wont stop autostarting"
date: 2009-12-15
forum: General Help
---

### Post by conorsulli on 2009-12-15
So guys yet another bug with the piece of rubbish that is nautilus file manager...

(A few weeks ago I couldn't browse files with videos in them, In jaunty it used just go grey and unclickable browsing directories... and samba is a disaster compared to dolphin....)

So guys Ive disabled every autostart app AND reinstalled nautilus yet it still insists on popping up with every boot.........

Im stumped and sickened with this awful file-manager, some of my friends have suggested that just to install dolphin / thunar into my gnome environment..... how how can I fix this issue?

Its a pain... :(

---

### Post by baddog144 on 2009-12-15
When you checked autostart apps did you check in /usr/share/gnome/autostart? It might have plonked itself there, and maybe it's out of the reach of the Startup Manager or whatever Ubuntu uses (I can't quite remember off the top of my head)

---

### Post by ajgreeny on 2009-12-15
Open the Options tab of the Startup Applications window and choose to remember running applications (just for one time).  Now shutdown, making sure nothing is open except things you want when you startup.  Restart, open the Startup Applications again and remove the check mark.  That should work, or it did for me in the past when I had the same very annoying problem.

---

