---
title: "Problems with Gnome after updates"
date: 2010-06-18
forum: General Help
---

### Post by Ildanach on 2010-06-18
Last night I upgraded to ubuntu 10.04, and it worked great. I went to bed running the update manager and restarted her in the morning. Now when I log in, GNOME doesn't display any panels, show applications, or do much of anything. All that i can do is switch in between workspaces. Works great on failsafe gnome though. Any ideas on how to fix?

---

### Post by rajn on 2010-06-18
What do you see? A blank wall paper?
Try this

Alt-F2.

If you get it then type "killall gnome-panel"

If you do not get the above, try cntrl-alt-F1
login into tty
then retype the above command.
then go back to graphics mode by 
cntrl-alt-F7.

Please post the outcome

---

### Post by Ildanach on 2010-06-18
Whoa, yeah, i had a blank wallpaper. But as soon as I ran that, everything popped up and worked.

---

### Post by rajn on 2010-06-19
> **Ildanach said:**
> Whoa, yeah, i had a blank wallpaper. But as soon as I ran that, everything popped up and worked.

Glad to know it worked. But it may not be permanent i.e., next time you boot in do you have to go through the whole process again?
If so here is what you need to do to make it permanent.
Go to System->Preferences->Startup Applications->Options and then select "Automatically remember... logging out". 
Next time when it reboots please inform the outcome. If it works would you mind marking this thread as SOLVED. Thanks,

---

### Post by Ildanach on 2010-06-19
oh, haha, that explains why its still working. I was thinking the same thing myself- that it would stop working as soon as i logged out. But auto-remember was one of the first things i turned on, so looks like I'm set. Thank you very much!

---

