---
title: "Kernel testing dilemma: an infinite loop of noveau failure."
date: 2012-07-18
forum: General Help
---

### Post by epikvision on 2012-07-18
ok, I saw the announcement from the kernel team on wanting testers.  Earlier this afternoon, I decided that I want to give kernel testing a shot, so i followed the announcements and installed the kernel and rebooted. After running the script, I still didn't know how to interpret the output.  . What's the worst that can happen?

Upon booting, I thought the system will run smoothly.  Instead, it entered a strange loop with these 
> 
[<numbers>] [drm] nouveau 0000:01:00.0: FFIFO - playlist update failed
[<numbers>] [drm] nouveau 0000:01:00.0: Failed to idle channel 2
...

and so on.  The list keeps going nonstop, in which the <numbers> topped 3xxx.xxxx!

It's probably a failure of nouveau to run. Playlist can't update, and it can't idle channel 1 and 2.

---

### Post by epikvision on 2012-07-19
I guess I have to do a fresh install to reset back to normal again.  There's no way I can uninstall the kernel from the virtual terminal.  

It's definitely a bug, as I can't get past the bootup screen.  I want to scour the system, but I'm already hampered by the nouveau failure.  Can someone tell me how I can report this problem?  

[http://packages.qa.ubuntu.com/qatracker/milestones/223/builds/18435/testcases](http://packages.qa.ubuntu.com/qatracker/milestones/223/builds/18435/testcases)

I check this link, and it only leads me to finding bugs while running the desktop.

---

