---
title: "Notification Area icons not appearing correctly sometimes (Lucid x64)"
date: 2010-06-26
forum: General Help
---

### Post by CTenorman on 2010-06-26
Sometimes the notification area doesn't display properly for me. I'm missing icons, etc. This happens on two x64 machines with all the latest updates in Lucid. A screen shot demonstrates what I mean.

Any ideas why this is, or should I submit a bug report?

---

### Post by avatardvr@gmail.com on 2010-06-26
I found a work around for the problem by adding the 'show hide button' on the panel and hiding and showing again.  worked for me in 10.04.  not a solution but effective...

---

### Post by CTenorman on 2010-06-26
Thanks for the tip!

Should I file a bug report, or did you or someone else do that? I didn't see anything, but then I've been known to miss things on occasion! :)

---

### Post by kiddykoff on 2010-06-26
I have the same issue and i'm running 64 bit, but i haven't submitted a bug report. I don't know what causes it as sometimes it loads bad, and other times it's fine. I haven't seen it happen with any 32 bit machines.

I tried twiddling around in gconf-editor. I managed to get it the applets to be placed correctly, but not always rendered correctly.

As a workaround, I added a custom launcher that will restart gnome-panel on my bottom panel, which always loads correctly. I attached an icon i made for it. The command is "killall gnome-panel"

If you file a bug report, post the link.

---

### Post by warfacegod on 2010-06-26
I've had this happen occasionally in Karmic 32. It seems to be totally random and doesn't happen often enough for me to care.

```
sudo restart gdm
```

You'll have to login again but it's better than rebooting.

---

### Post by hansdown on 2010-06-26
My toolbar keeps doing that.

I installed cairo dock, and oddly, firefox loads super fast now.

---

### Post by CTenorman on 2010-06-26
So evidently this is a problem that needs fixing. However, I can't for the life of me figure out where to file the bug or how to do it. Any ideas?

I wonder why Ubuntu makes this so hard!?!

---

### Post by warfacegod on 2010-06-26
This is one of the Sticky's at the top of Absolute Beginner Talk.

[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

---

### Post by CTenorman on 2010-06-26
Thanks warfacegod. I looked at that earlier, but I'm not sure what the package name is.

---

### Post by warfacegod on 2010-06-26
gnome-applets

---

### Post by CTenorman on 2010-06-26
Grand, thanks!

---

### Post by CTenorman on 2010-06-26
OK, bug filed:

[https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/598886](https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/598886)

Thanks everyone for your help!

---

### Post by warfacegod on 2010-06-26
Sure thing, hoss. This is one of those times that I think there should be a "Solved, Sort Of" option under Thread Tools.

---

### Post by octathlon on 2010-10-26
> **avatardvr@gmail.com said:**
> I found a work around for the problem by adding the 'show hide button' on the panel and hiding and showing again.  worked for me in 10.04.  not a solution but effective...

I'm running 32 bit but still have the same bug. I want to use your work around, but what 'show hide button' are you talking about?  I don't find it in the add to panel list of applets. 

I'd like to be able to reset the panel without having to log out or restart X ...

EDIT:
I found this workaround in the bug report:
"When it happens, right click the panel, click properties, then change the "size" by one pixel, then change it back after it refreshes."

---

### Post by CTenorman on 2010-10-27
Right click on the panel, click on properties, choose "show hide buttons." teh problem will be fixed for that session, You can check it off again and the problem will still be fixed. Again, it may not be solved on reboot, regardless of whether the box is left checked or not (in my experience).

---

