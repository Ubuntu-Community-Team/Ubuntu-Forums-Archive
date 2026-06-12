---
title: "Missing title bars after update in xubuntu ubuntu"
date: 2011-03-23
forum: General Help
---

### Post by murthy on 2011-03-23
The title bars / window decorations are missing since the last update done about two days ago.  I have AMD64 / nvidia 6600 / 2GB / compiz.  Latest driver is installed for nvidia and it was working without any problems since 9.04.  Now I find that desktop visual effects are selected as 'None' and I am unable to make it 'extra'.  Earlier it was set as custom and I had no problems.  I have searched the forums and tried many solutions without any success.  Now I am running metacity (metacity --replace)with no visual effects, 'compiz --replace' brings back the problem .  Is there any way of enabling visual effects // compiz now?  Or do I have to re-instal the whole thing?
Thanks in advance for suggestions / solutions.

---

### Post by murthy on 2011-03-24
Could this problem be caused by a virus?  Is no one else having such problem?  Any solution please?  I would like to have visual effects enabled.

---

### Post by murthy on 2011-03-26
Anyone please?  Is no one else experiencing this problem?  Shall I have to reinstall like windows to solve this?

---

### Post by murthy on 2011-03-28
Still no reply.  I will stop looking for any reply, and boasting to others about the wonderful help given regarding problems faced in linux!

---

### Post by bent12 on 2011-03-28
no i don't no

---

### Post by hexsel on 2011-05-25
Hah!  I have the same now.  Dunno what caused it, there was a small update today, but didn't look like it was related.

Using Chromium with the non-native window decorations to work around the issue for now...

---

### Post by wildmanne39 on 2011-05-26
> **murthy said:**
> The title bars / window decorations are missing since the last update done about two days ago.  I have AMD64 / nvidia 6600 / 2GB / compiz.  Latest driver is installed for nvidia and it was working without any problems since 9.04.  Now I find that desktop visual effects are selected as 'None' and I am unable to make it 'extra'.  Earlier it was set as custom and I had no problems.  I have searched the forums and tried many solutions without any success.  Now I am running metacity (metacity --replace)with no visual effects, 'compiz --replace' brings back the problem .  Is there any way of enabling visual effects // compiz now?  Or do I have to re-instal the whole thing?
Thanks in advance for suggestions / solutions.
Hi, this is how to enable visual effects in natty. [http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

---

### Post by hexsel on 2011-05-26
I don't have compiz installed, yet still lost it.  No weird PPAs either, just Chromium-beta.

Just for a test, I tried to install compiz and run compiz --replace this morning, but I STILL didn't get the decorations (but I can now select a different window than the last one I opened!).

It's a most odd bug, it feels like the nvidia driver is not active as there's no transparency on the bottom panel, but nvidia-settings shows as ok, there's nothing in the logs for X nor dmesg nor the main syslog.

Also, I don't seem to be able access the XFCE window manager settings, nor the Appearance settings.  I can access the "Display" settings, but those are really just the monitor settings.

---

### Post by hexsel on 2011-05-26
I'll just delete all xfce settings folders and try to log in again.  It's a pity, cause the bottom bar is a major pain to add a bunch of icons to.

---

### Post by hexsel on 2011-05-26
And... that didn't work, but installing and forcing metacity to replace whatever window manager xfce had or was expecting worked.

---

### Post by gb38 on 2012-05-15
I had the same problem in xubuntu
(lsb_release -a): Ubuntu 12.04 LTS precise
and solved it with the advice of
[http://ubuntuforums.org/showthread.php?t=941247](http://ubuntuforums.org/showthread.php?t=941247)
Run following command as normal user in a command prompt:
```
xfwm4 --replace &
```

The --replace exists apparently for most window managers.
So metacity --replace should work to.

---

### Post by murthy on 2012-05-15
I had finally reinstalled xubuntu and solved the problem.  I could not use compiz then.  Now I have upgraded my system and use xubuntu with compiz without any problems.

---

