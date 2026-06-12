---
title: "ssh -X changes desktop on host"
date: 2009-10-03
forum: General Help
---

### Post by jdrodrig on 2009-10-03
Hi,

Curious question. I connect ssh -X to my opensolaris box from my ubuntu laptop and I notice that everytime I run nautilus on the ssh session, besides the gui appearing, ubuntu's desktop's background changes to my opensolaris's...why is that? can I prevent it? it is kind of annoying...

---

### Post by SoftwareExplorer on 2009-10-04
Well, I think it's that nautilus is usually in charge of showing the desktop background and icons in gnome. I once disabled it showing the desktop background and icons, so that compiz could draw the wallpaper, and whenever I ran nautilus as root, it would replace the compiz wallpaper with whatever roots wallpaper was set to.
So, maybe you have nautilus drawing the desktop disabled, or maybe the solaris version doesn't check properly?
Also, a workaround I found was that when you are done, you can use the program killing applet (it's icon looks like a broken application window) and click on the desktop to make it go away.

---

### Post by 3rdalbum on 2009-10-04
Instead of just running "nautilus", you can run "nautilus --no-desktop".

---

### Post by jdrodrig on 2009-10-04
thanks to both of you. I will try right away your workarounds.

d.

---

### Post by SoftwareExplorer on 2009-10-04
> **jdrodrig said:**
> thanks to both of you.

Glad I could give you an idea of what is going on. :)

---

