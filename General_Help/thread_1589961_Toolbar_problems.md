---
title: "Toolbar problems"
date: 2010-10-07
forum: General Help
---

### Post by 4thfloorstudios on 2010-10-07
Hi,
in my desktop toolbar on the right side where my running applications are shown etc. I have some problems:

1) After a while and after some messages have been shown and applications started, there is a growing gap which gets larger. When I move the mouse over the gap, I see tooltips belonging to the application to the right which is always a different one so I assume that it is a toolbar problem and no application problem.

2) Some icons are not clickable with the left mouse button, e.g. Rhythmbox. When I left click on it, nothing happens.

3) When I open the volume control with a left click, I cannot close it by clicking somewhere else. I always have to click on the "Mixer" Button to see a whole window and then I can close it.

Does anyone know if these are bugs which get fixed (didn't find any) or if there is a solution for that?

Thanks,
Oliver

---

### Post by ankspo71 on 2010-10-08
Hi,
The only thing I can think of suggesting is to try removing the 'system tray' and 'notifications' widgets from the panel, then add them back to the panel again. Every widget I removed and re-added did not keep their settings, so the settings for those widgets will be recreated (if needed). This might help if it is a problem related to their settings.

Possibly related problems/bugs:
[https://bugs.kde.org/show_bug.cgi?id=247304](https://bugs.kde.org/show_bug.cgi?id=247304)
[https://bugs.kde.org/show_bug.cgi?id=225352](https://bugs.kde.org/show_bug.cgi?id=225352)
[https://bugs.kde.org/show_bug.cgi?id=251851](https://bugs.kde.org/show_bug.cgi?id=251851)

Hope this helps.

---

### Post by 4thfloorstudios on 2010-10-11
Hi,
I simply removed the message indicator, now it is fixed (the mixer problem too), so it seems that the message indicator is buggy in some way.

Thanks for your help.

I found this bug too which has something to do with the indicator:
[https://bugs.kde.org/show_bug.cgi?id=249819](https://bugs.kde.org/show_bug.cgi?id=249819)

Oliver

---

