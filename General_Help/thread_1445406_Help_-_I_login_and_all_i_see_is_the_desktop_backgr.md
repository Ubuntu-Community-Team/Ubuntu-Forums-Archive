---
title: "Help - I login and all i see is the desktop background"
date: 2010-04-02
forum: General Help
---

### Post by jameselder232 on 2010-04-02
Hi, i need some help. I just restarted my computer, tried to login and all i see is the blue Kubuntu wallpaper, the desktop items never load, i can run terminal by pressing ctrl+alt+f2 however? This happened before and i just reinstalled the kde, but i really need to find out why this keeps happening...

Thanks, i searched the net but i didn't find anyone with the same problem, only similar ones,
James

---

### Post by Untitled_No4 on 2010-04-02
Can you right click on the desktop, then choose Unlock Widgets (if locked) and then right click again and choose Add Panel? Does that add a panel to your dekstop (most likely on top left corner or thereabouts)? If so it is possible that one of your KDE configuration files (at ~/.kde) got deleted or corrupted and therefore you lost your panel. 

You can also rename your ~/.kde folder and KDE will create a new one upon login with default settings (or at least it should do so).

Why would it happen? I guess there could be quite a few reasons, perhaps an update to KDE has not been finished properly and a configuration file was left empty?

---

