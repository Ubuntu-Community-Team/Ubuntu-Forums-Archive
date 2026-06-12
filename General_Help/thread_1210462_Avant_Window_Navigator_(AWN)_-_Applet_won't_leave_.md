---
title: "Avant Window Navigator (AWN) - Applet won't leave (and keeps multiplying)"
date: 2009-07-11
forum: General Help
---

### Post by HiImTye on 2009-07-11
Hi there!

    Ok, so here is my problem. I installed the testing version of Avant Window Navigator to test out the 'Standalone Application Launcher'. It didn't work very well (had to manually refresh after editing it to make it load the settings and it didn't actually launch anything), so I removed the standalone switchers, uninstalled the trunk version (all the stuff that I could see that came with it), removed the repository for it and installed good old 'regular' AWN. Now, however, I keep getting 'lines' on AWN and when I go to AWN-Manager I see several 'ghost apps' with no description (which I assume to be the old 'Standalone Application Launcher'). I remove these, however, they keep appearing AND multiplying!
    Does anyone know of a way to manually remove these from outside AWN so that AWN doesn't keep adding them?

Thanks in advance!

---

### Post by HiImTye on 2009-07-12
ok so after a long time trying to get a fresh install (which I thought was impossible after uninstalling, deleting the /.config/awn and /.gconf/apps/avant-window-navigator folders, reinstalling it just to find out that the only things gone were my shortcuts inside the AWN Manager applet) I found a forum thread on the AWN launchpad 'answers' page which had this handy little snippet to put into a terminal
[FONT=monospace]
[/FONT]gconftool-2 --recursive-unset /apps/avant-window-navigator

reloaded AWN and everything is fine now! yay! just gotta set it up good again! no more testing stuff for me haha

---

### Post by HiImTye on 2009-07-13
ok, I lied. it didn't correct the issue. I have since gone back to Gnome-Panel for the top and bottom (not just the top). I will attempt to fix it later (and post any fix I happen to find, if I do). but atm I don't have the patience for it

---

### Post by HiImTye on 2009-07-14
ok so to fix the problem (which I got in response to my post about the problem on the AWN launchpad 'answers' section) I had to kill 'taskmand' (either 'killall taskmand' or kill it from the task manager/system monitor). once I removed the 198 instances of it which accumulated between when I last tried to fix it and when I killed the process it is perfect again :D

hope this helps someone else

---

### Post by SnappyU on 2012-09-15
This is three years old ... but still, I got a chuckle reading your self-relying Q&A.

On the issue, glad you resolved yours.  I'm having a ghost "+" applet in the Launcher/Task Manager area ... just found that I can remove it by dragging another app around.

More like a workaround than fix.  But as awn goes ... ;)

---

### Post by overdrank on 2012-09-15
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

