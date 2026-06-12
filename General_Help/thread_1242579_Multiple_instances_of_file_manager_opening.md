---
title: "Multiple instances of file manager opening"
date: 2009-08-17
forum: General Help
---

### Post by Genesius on 2009-08-17
I know I've seen this on the forum before, but I've tried every keyword combination I can think of & can't find it. So, I throw myself on the mercy of the Group Mind.

My system is set up to let Compiz display a different wallpaper on each desktop. There was a bug in Nautilus before that would cause it to spawn out of control when you set Nautilus to not draw the desktop, but the bug was fixed. Now, however, after upgrading to Karmic the bug is back.

I know there's one setting that has to be changed in one file to fix this, but I can't come up with it.

---

### Post by Genesius on 2009-08-17
*sigh* Should have checked Launchpad first. . .

/usr/share/applications/nautilus.desktop and set X-GNOME-autorestart=false

---

