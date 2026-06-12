---
title: "Bizarre Window Focus Behavior"
date: 2010-08-26
forum: General Help
---

### Post by C4colo on 2010-08-26
In the last four versions of Ubuntu I have used there is sometimes this window focus bug that is very annoying.

I do not know exactly how to reproduce it but I can explain how to increase the probability of it happening.

If you open more than one window and select one to set the focus to that window, then grab the title bar of another window and drag it, sometimes the first, focused window will snap to your mouse cursor and be dragged around even if the first window is not visible (minimized or behind forground, but non-focused window).  This also happens on other actions such as minimize, close and maximise/restore.

I'm using Gnome as the window manager, all visual effect are turned off.  I have had this issue intermittently in 8.04, 8.10, 9.04 and 9.10.  I have 10.4 on my media pc in the living room and I believe I have seen it happen once on there as well.

Is this something that it is designed to do?  A bug that nobody else has noticed because they interact with the windows differently than I do?  Am I even describing it adequately?

EDIT: I forgot to mention this is most likely to happen with terminal windows, but it is not exclusive to terminal windows.  Maybe I just use lots of terminals in my line of work and it is the most likely type of window I would be interacting with.

EDIT2: As I'm playing around I got it to do it.  It was not as I described though:

I Clicked on a terminal window deselecting this chrome window.  Then dragged a second terminal window by the title bar and the chrome window snapped to my mouse cursor from behind both terminal windows.  It was not even the focused window but the window that lost focus to the first terminal window.

I don't even know where to start trying to troubleshoot or debug this issue.

EDIT3: I was having trouble googling for the issue but finally ran across this bug report:

[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/613775](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/613775)

---

