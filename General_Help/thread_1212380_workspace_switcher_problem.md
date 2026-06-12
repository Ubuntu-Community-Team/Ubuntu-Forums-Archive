---
title: "workspace switcher problem"
date: 2009-07-13
forum: General Help
---

### Post by TreeHugger52 on 2009-07-13
I am having workspace issues after installing a slew of Jaunty updates (I hadn't updated for ~1 month). I'm running gnome on a macbook santa rosa. The workspace switcher doesn't respond to setting changes- if I right click on the switcher and change the number of columns or rows, nothing happens; I always have four workspaces arranged in a horizontal line. If I try to change workspaces by clicking on one of the inactive workspaces, I move to a screen with nothing but my wallpaper- no desktop icons, apps, or bars at the top or bottom of the screen. I'm stuck there, unable to do anything, and unable to get back (or, I don't know how to get back), so I'm forced to reboot. I can move around to different "workspaces" of nothing but my wallpaper using control*option with the compiz desktop wall.

I am able to change the number of displayed workspace icons in the switcher in the "general options" region of the compiz gui config tool, but still get warped to no-mans-land if I click on another workspace. I also can use the desktop wall to move between workspaces without being sucked into no-mans-land, but all of the apps stay in the bottom bar, so I'm not actually switching workspaces. If I right-click on a window and send it to a different workspace, it goes to no-mans-land. If I then switch to this application using the ring switcher, I also get sucked into no-mans-land with nothing but that application.

I've tried a number of suggested switcher fixes from the forums (remove the switcher from the panel and re-add it, disable the desktop cube) to no effect. This is really annoying, because I have to reboot after everything I try- I change one thing, click on an in-active workspace, and have to reboot.

Sorry this was so long. Any suggestions?

---

### Post by TreeHugger52 on 2009-07-13
I never figured out what went wrong, but I was able to resolve the problem by resetting compiz to its default settings in the compiz gui settings manager.

I'd rather have actually found the cause of the problem... but at least I won't have to reboot so frequently anymore.

---

### Post by iammatthew2 on 2009-08-03
I think I am experiencing the exact same problem you describe: if I use the workspace siwtcher to change to a different virtual workspace I get stuck in no-man's land. If, on the other hand, I use keyboard shortcuts to change workspaces the switch occurs without error.
 
My system: Unbuntu Studio 9.04, Dell laptop
 
This began happening a few weeks ago and I thought it was due to a bunch of changes I made that included the following:
 
-added KDE as an optional session type
-inside of a KDE session I named each workspace
-discovered the workspace problem, so I removed the KDE session type via command line command while in Gnome session type
 
This evening I will try to solve the issue as TreeHugger did: > I was able to resolve the problem by resetting compiz to its default settings in the compiz gui settings manager.
 
Will reply with results.

---

