---
title: "Where is my &quot;system notification&quot; tray in 11.04?"
date: 2011-05-02
forum: General Help
---

### Post by brad1138 on 2011-05-02
Where is my "system notification" tray in 11.04? I can't right click and add it (or anything) in 11.04.

Any thoughts?
Thanks,
Brad

---

### Post by boygenuis on 2011-05-10
I believe I am having the same, or similar, issue.  I was messin' around with my 3D effects in Compiz, restarted because I couldn't click on anything, and now the only items on my screen are my desktop icons; no notification area, no side application tray.  Fortunately, this only happens on my main account.  I can view everything normally on what I call my "guest" account.  Thoughts?

---

### Post by mcduck on 2011-05-10
> **brad1138 said:**
> Where is my "system notification" tray in 11.04? I can't right click and add it (or anything) in 11.04.

Any thoughts?
Thanks,
Brad
It's already there by default, but configured to only show icons for certain applications.

If you want to add a new application to the whitelist, or set it to show all icons, install the "dconf-tools"-package, then run "dconf-editor" and add your program to *desktop/unity/panel/systray-whitelist* (or set the value to "all")

> **boygenuis said:**
> I believe I am having the same, or similar, issue.  I was messin' around with my 3D effects in Compiz, restarted because I couldn't click on anything, and now the only items on my screen are my desktop icons; no notification area, no side application tray.  Fortunately, this only happens on my main account.  I can view everything normally on what I call my "guest" account.  Thoughts?
Make sure you have the Unity plugin enabled in CompizConfig Settings Manager.

---

### Post by boygenuis on 2011-05-18
> **mcduck said:**
> Make sure you have the Unity plugin enabled in CompizConfig Settings Manager.

I can't change any of the CompizConfig settings, or pull up the manager because only the wallpaper and desktop icons appear; the notification tray and the new side panel (meta button?) aren't visible.  Right-click works, but CTL-ALT-T doesn't pull up a Terminal window to try and initiate any programs.  Thoughts?

---

### Post by mcduck on 2011-05-19
> **boygenuis said:**
> I can't change any of the CompizConfig settings, or pull up the manager because only the wallpaper and desktop icons appear; the notification tray and the new side panel (meta button?) aren't visible.  Right-click works, but CTL-ALT-T doesn't pull up a Terminal window to try and initiate any programs.  Thoughts?

This might not be the smoothest way to sort that out, but I'd probably do it like this anyway. Just drop into a TTY (Ctrl-Alt-F1), log in, and install the "nautilus-open-terminal"-package. Then move back to GUI and log in, you should now be able to start a terminal from the right-click menu, and that of course allows you to launch any programs you want to, including CCSM. :)

(you *could* also just choose the Classic desktop from the session-menu in the login screen, access CCSM from there and enable Unity plugin, log out and choose the Unity session. But having the option to open a terminal in the right-click menu is great. ;))

---

### Post by wildmanne39 on 2011-05-19
> **boygenuis said:**
> I can't change any of the CompizConfig settings, or pull up the manager because only the wallpaper and desktop icons appear; the notification tray and the new side panel (meta button?) aren't visible.  Right-click works, but CTL-ALT-T doesn't pull up a Terminal window to try and initiate any programs.  Thoughts?Hi, you can also use the guide in my signature below this text to reset unity, that is what is messed up. The guide is called reset unity or compiz.

---

