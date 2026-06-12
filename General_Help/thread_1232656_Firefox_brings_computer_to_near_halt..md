---
title: "Firefox brings computer to near halt."
date: 2009-08-05
forum: General Help
---

### Post by dustyg54 on 2009-08-05
It has worked fine until today. When I click on FF, everything slows waaaaay down.  I also have Kazehakase and it runs fine (using now to post this).  Running 9.04, FF version is 3.0 I think, at least I am getting updates for 3.0 through update manager.

---

### Post by TMAN 1 on 2009-08-05
Perhaps try to reinstall it,save your bookmarks though.
I had to do this and it worked fine afterwards.Though,I don't know what was the cause of it.

---

### Post by dustyg54 on 2009-08-05
Reinstalled through Synaptic, and it is doing the same thing..

---

### Post by dustyg54 on 2009-08-05
It seems as though this problem occurred after xulrunner was updated today through update manager.  will a fix for this be issued soon?

---

### Post by gldearman on 2009-08-05
Try starting Firefox in safe mode with all addons disabled.  This will disable all of your extensions and themes, but you will have to disable plugins manually.  See if you get any performance differences.

If you have the same problems in safe mode, try creating a clean Firefox profile from scratch and launch with that -- no add-ons, user settings, or anything like that.  See if that gives you any performance differences.  Note that you do not have to delete your existing profile to do this.

My best guess is that something in your profile, likely an add-on, has become corrupted or is not compatible with the upgrade.  Once we can figure out what the offending party is, you can disable it.

Let us know if you need more help, or if my troubleshooting instructions were too vague.

---

### Post by lensman3 on 2009-08-06
Firefox uses an sql database to keep track of cookies, visited sites, etc.  There is an sql command when it is pointed to when you run a sql fixup program on the file, will fix the database.

Sorry I can't be more help, but I saw a reference in passing about 3 months ago.  And that's all I remember.

I think it was a sub-command of sqlite3.

---

### Post by dustyg54 on 2009-08-07
I tried running FF safe mode in terminal via ```
firefox -safe-mode
``` to no avail. Same problem.  
Every minute or so (once I start FF) my whole system is 95% unresponsive (windows will pull up but nothing is displayed in them). Then for about 30 seconds I guess it becomes responsive and I can do anything, and it repeats. All the while my HD is making a distinct, repetitive noise as if it is trying to load something. 
(btw, I am a Linux turbo noob)

---

### Post by tgalati4 on 2009-08-07
Clear your private data.  This clears your cache.  It might help.

If you want fast, run firefox from a ramdisk:

[http://www.verot.net/firefox_tmpfs.htm](http://www.verot.net/firefox_tmpfs.htm)

---

