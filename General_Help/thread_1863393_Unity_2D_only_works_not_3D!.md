---
title: "Unity 2D only works not 3D!"
date: 2011-10-17
forum: General Help
---

### Post by dragonbeast25 on 2011-10-17
Okay well Ubuntu was really choppy and laggy i have no clue why, i have a really good computer, ATI radeon, 2GB, 4.5cpu dual core, Aspire Acer. Anyways all Ubuntu's lag and choppy really bad. I just Remove windows completely hoping to start with Ubuntu fresh, ive been around it since like 8.04 . I changed OpenGL setting and Composition setting, like it said on google so it would be faster it was! but the taskbar and icons all disapear nothing showed up. So i tryied doing unity --replace and, unity --reset, but it stays on this one option and doesnt move, 2D only works. im not impressed with ubuntu so far but i want to be, thank you for your time!

---

### Post by 3Miro on 2011-10-17
Which Radon is it? Historically ATI has had very bad support for Linux. There has been huge improvement in recent years, but this only covers the newer cards (ATI 4xxx and newer). Older Radeon cars may not support Unity.

You can also check for additional drivers by looking at the "Additional Drivers" program (search for it in the global menu). You can start it in the terminal with:
```
gksudo jockey
```

---

### Post by dragonbeast25 on 2011-10-17
Okay well ill try that, and its ATI Technologies Inc Radeon 2100, i still need help though guys please :/

---

### Post by badperson on 2011-10-17
I have a similar problem. the regular ubuntu setting "not ubuntu 2d" was working for me, but I was futzing around in the compiz settings, and now when I try to log in with the regular ubuntu I don't get the sidebar or any of the data on the upper right corner. Just the icons on the desktop and a pulldown for the file browser. Any idea how to fix the compiz stuff back to where it was?

---

### Post by dragonbeast25 on 2011-10-17
Exactly, im in 2D right now it works fine but not 3D :(

---

### Post by Meelad on 2011-10-17
Try:

[http://ubuntuforums.org/showthread.php?t=1863257](http://ubuntuforums.org/showthread.php?t=1863257)

Problem #4.
Please confirm if it works for you..

---

### Post by 3Miro on 2011-10-17
Read Meelad's post, but my guess is that you will not be able to run Unity 3D. You can install Gnome-shell and Gnome-session-fallback, you may like those better. Gnome-shell can be tweaked to be somewhat like Unity (in looks, not necessarily in functionality).

Alternatively, you can try XFCE or LXDE or even KDE.

PS: If Ubuntu 10.04 worked better for you, it will be supported for couple of more years. Debian 6 is very close to 10.04 and it will be supported for another three years. Those are other options.

---

### Post by badperson on 2012-06-04
has a solution been found for this issue in 12.04?

---

