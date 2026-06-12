---
title: "screenlets start at nearly random workspaces"
date: 2009-06-29
forum: General Help
---

### Post by myk02k on 2009-06-29
Hey guys, I don't know if this is the proper place to post this question but I am in need of some help.

I have installed screenlets on Workspace 1 and when X is restarted, they appear to load at an almost random workspace.  Although the majority of screenlets appear to load at the same improper Workspace (right now they tend to start at Workspace 3), one or two screenlets sometimes decide to load at random Workspaces.  I have attempted numerous fixes and always move them back to Workspace 1, but somehow after a few restarts they begin to act up again.  Please help; this is extremely annoying and frustrating.

---

### Post by Jay_Bee on 2009-06-29
That is one of the most reported issues with Screenlets, but unfortunately the project is abandoned and no longer developed so I doubt that it will be fixed. I don't know if there is any other way to force the Screenlets to start on a desired workspace. A workaround could be making them "Sticky" which will make them show on all workspaces.

---

### Post by CatKiller on 2009-06-29
If you're using Compiz, you can configure the Place Windows plugin to always put your Screenlets on a specified workspace (although Compiz calls them "viewports").

---

### Post by lovinglinux on 2009-06-29
> **CatKiller said:**
> If you're using Compiz, you can configure the Place Windows plugin to always put your Screenlets on a specified workspace (although Compiz calls them "viewports").

This a clever solution. 

The value would be *class=Screenlet.py*. This will put all screenlets on the same workspace, but if you want just a few of them, then you will need to grab the window class from each screenlet type. For example, the Disk usage screenlet would be *class=DiskusageScreenlet.py*.

---

### Post by myk02k on 2009-06-30
Works flawlessly!  Gotta love this forum, thanks!  I was losing hope as I couldn't find a solution by Googling this issue.

---

### Post by myk02k on 2009-10-15
Anyone know how I can hide the desktop icons on viewport 1?

---

