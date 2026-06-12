---
title: "&quot;Bookmarks Toolbar Items&quot; Stuck in Firefox Toolbar?"
date: 2009-08-13
forum: General Help
---

### Post by ben-ess08 on 2009-08-13
Running Firefox 3.0.13;

I was switching themes for GTK and Firefox, and the Activity Indicator looked untidy, so I removed it by going to Customize via the right-click menu (All the bookmarks in the toolbar change automatically change to the single "Bookmarks Toolbar Items"). Since I came out Customize, my bookmarks are back there but so is the Bookmarks Toolbar Items? I can't delete it through right-clicking so any ideas? Thanks a lot. :)

---

### Post by coldReactive on 2009-08-13
To remove something from the bookmarks toolbar without right-clicking it, go to **Bookmarks > Organize Bookmarks**. There will be a pane to the left with a tree-like view, left click bookmarks toolbar to manage the bookmarks toolbar items.

If you want to completely remove the bookmarks toolbar from view, go to **View > Toolbars > Bookmarks Toolbar**.

The customize feature will not show your individual bookmarks on the bookmarks toolbar.

---

### Post by ben-ess08 on 2009-08-13
I know, I just have a dead link that I can't delete that would normall show up when I choose customize, here a screenshot. [IMG]http://www.freeimagehosting.net/uploads/6c5dfb9400.png[/IMG]

---

### Post by mlissner on 2009-08-13
I had a problem a while back with busted bookmarks. I think it happens with the sqlite database they're stored in gets corrupted. Probably the most foolproof (though perhaps not the most elegant) solution is to backup anything that is important to you in your FF profile, and then create a new one. It'll probably take a few hours, but it should fix the problem.

---

### Post by lovinglinux on 2009-08-14
Try this:

Right-click on the toolbar, select customize, then drag the Bookmarks Toolbar Items from the toolbar to the Customize Toolbar window. Close everything, restart Firefox and do the same same thing, but drag it back to the toolbar.

If that doesn't help, you could click the Restore Default Set in the customize window, which will reset your toolbar configuration.

If that doesn't work, try deleting your bookmarks database (make a backup first). See **Solution** [*[COLOR="Red"]**FOT003**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT003). If that doesn't fix the problem, then try **Solution** [*[COLOR="Red"]**FOT002**[/COLOR]*].

---

