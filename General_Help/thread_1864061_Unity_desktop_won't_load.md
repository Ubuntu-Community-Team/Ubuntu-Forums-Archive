---
title: "Unity desktop won't load"
date: 2011-10-18
forum: General Help
---

### Post by ldkronos on 2011-10-18
I upgraded to 11.10 last week and everything was fine for a few days. Today my system locked up on me (mouse cursor moved, but clicking did nothing, and I couldn't alt tab to other apps). I hit cltr-alt-delete, which did nothing for about 15 seconds, then the graphics got garbled for a second, then I was back at the login screen. I logged in and the screen was screwed up. I couldn't do anything at all, so I did a poweroff and reboot.

After logging back in, I now have no Unity desktop. It looks like I have nautalis running as my shell or something. I see my desktop files and my wallpaper, and at the top I have my Nautalis menu bar (File Edit View etc). The empathy window also pops up (it loads at startup). But other than that  I have nothing. No Unity launcher or dash. and no icons at the top right (theres no clock, mail icon, logout menu, or anything).

If I logout and login with Unity 2D, then I get the 2D desktop and everything pretty much seems like it should. I figured maybe it was a driver issue. I'm currently running "ATI/AMD proprietary FGLRX graphics driver". Theres also an option for "ATI/AMD proprietary FGLRX graphics driver (post-release updates)". I tried upgrading to that but the installation failed. I reverted back to the open source driver. That worked fine, but still no 3D unity. Tried reinstalling my original ATI driver, and that also worked fine, but still no 3D desktop. Switched back to the open source driver, and now even unity 2D fails to load.

So, thinking maybe it's a profile problem or something, I go into the recovery console and add another user to the system, login as that user, and I still get the same problem, both for Unity and Unity 2D.

Any ideas?

---

### Post by ldkronos on 2011-10-18
OK, I've got this fixed. I followed a bunch of the instructions from the following:
[http://ubuntuforums.org/showpost.php?p=11326398&postcount=5](http://ubuntuforums.org/showpost.php?p=11326398&postcount=5)
[http://ubuntuforums.org/showthread.php?t=1856053](http://ubuntuforums.org/showthread.php?t=1856053)

I purged the graphics drivers and installed the ones straight from ATI, I reset unity and forced a reinstall of a whole bunch of packages. None of that worked. Then, I saw the user in the second thread mentioned Unity was unchecked in compizconfig. So I used Nautilus to search for the compizconfig app, ran it, saw the box was unchecked for me. I rechecked it, and everything seems to be fine now. 

I've no idea what happened in the first place, or why unity first got disabled only in 3D, and then later in 2D also. So I guess the problem is fixed, even though it's still a bit of a mystery

---

### Post by MonolithImmortal on 2011-10-18
Weird, this is why I never liked that unity was a compiz plugin.

---

### Post by ldkronos on 2011-10-20
This happened to me again today. I was inside CompizConfig, configuring the grid plugin. I had just unchecked the box for "snap windows back to original size" and it instantly logged me out. When I logged in there was no unity again. So I went into compizconfig, but this time the Unity plugin was still checked. I tried unchecking it and rechecking it, but no change. So I unchecked it, logged out and in, then I rechecked the box and the Unity interface appeared.

When this happened to me last time, I was also in CompizConfig. That time, I had just opened it and I clicked on the Preferences option on the left panel. I'm not sure what's going on with CompizConfig, but at least today it only took me 5 minutes to fix rather than 4 hours.

By the way...why is it that CompizConfig routinely just forces a logout when you enable/disable certain plugins? It's not even nice about it. No prompt, warning, or even a chance to save any open files. Pretty crappy behavior.

---

