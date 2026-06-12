---
title: "Newbie here with a couple of questions about 11.10"
date: 2011-12-16
forum: General Help
---

### Post by Auroraei on 2011-12-16
Hello! Newbie here and I have a couple questions.

I am completely new to Ubuntu or anything Linux so if you could explain things in layman's terms that would be great.

I have the latest version of Ubuntu (11.10), before this I used Windows XP and so far I am really liking it but I have a couple questions.

You know that bar on the left that holds your icons? Is there a way if I am not fullscreen on Firefox or a window, that I can make that bar disappear until I hover over the area? I don't like how it's taking up space right now.

Also, you know when you move a window up, or to the right or in a corner and the screen turns orange and it snaps into place or goes fullscreen, is there a way to disable that?

I know I'll have more questions but that's it for now :)

---

### Post by usmanasim on 2011-12-16
First of 

Welcome to the Wonderful Ubuntu forums and the world of linux and Ubuntu.

There is probably no graphical setting to turn of the auto full screen when you move a window to the top of the screen.

If you have used a windows7 and mac you will see that this is the default feature in these OSes as well. (and you can't disable in them as well.)

The autohide of the left shortcut bar is something that I have yet to find out.

---

### Post by Auroraei on 2011-12-16
> **usmanasim said:**
> First of 

Welcome to the Wonderful Ubuntu forums and the world of linux and Ubuntu.

There is probably no graphical setting to turn of the auto full screen when you move a window to the top of the screen.

If you have used a windows7 and mac you will see that this is the default feature in these OSes as well. (and you can't disable in them as well.)

The autohide of the left shortcut bar is something that I have yet to find out.

Thank you  :)

No I have not used Windows 7 or Mac, btw.

It always seems like the little things that bother me the most are unchangeable  :lol:

Still even with those annoyances so far I'm really liking Ubuntu, it seems simplistic.

---

### Post by Derek Karpinski on 2011-12-16
You'll have to open up the Ubuntu Software Center, and search for compizconfig, and install CompizConfig Settings Manager.

After that is installed, push the Super key (Windows key) on your keyboard, and type 'ccsm' in the search.  Start compizconfig settings manager.

Look for a section labeled 'Ubuntu Unity Plugin'.  In the 'behavior' tab, change Hide Launcher to 'Autohide' or my preference 'Dodge Active Window'.

---

### Post by daftlad on 2011-12-16
If you install CompicCongig settings manager from the software centre you can then adjust the side bar to autohide and other configurations.

---

### Post by nothingspecial on 2011-12-16
Hi, welcome to the forums. :)

The above is the correct procedure for autohiding the unity bar.

However, please don't go changing any settings in compizconfig-settings-manager unless you know what is going to happen. It is possible to mess things up in there.

---

### Post by lolpenguin on 2011-12-16
Yes, you can make the bar (called the _Launcher_ disappear unless you move your mouse near it.
1) Install the CompizConfig Settings Manager:
- Launch a terminal, search for terminal in the _Dash_
- Type or copy this command into the window
```
sudo apt-get install compizconfig-settings-manager
```
- Type in your password, note that the characters will not show, but are still registered.
2) Launch CCSM
- Search for ccsm in the dash.
- Scroll down to the "Desktop" category, then click on "Ubuntu Unity Plugin" (do NOT click on the checkbox!)
3) Set "Hide Launcher"
- Choose from Never, Autohide, Dodge Windows, or Dodge Active Window.
~~Never: the launcher will always be visible
~~Autohide: the launcher will always hide, it will only be visible if you move your mouse to the left edge of the screen
~~Dodge Windows: [default] the launcher will be visible unless a window is in its way
~~Dodge Active Window: the launcher will hide if the window currently selected is in its way
**Don't touch the other settings, just yet!**
Also, since you are new, the Absolute Beginner Talk sub-forum is there for a reason!

---

### Post by Auroraei on 2011-12-16
> **Derek Karpinski said:**
> You'll have to open up the Ubuntu Software Center, and search for compizconfig, and install CompizConfig Settings Manager.

After that is installed, push the Super key (Windows key) on your keyboard, and type 'ccsm' in the search.  Start compizconfig settings manager.

Look for a section labeled 'Ubuntu Unity Plugin'.  In the 'behavior' tab, change Hide Launcher to 'Autohide' or my preference 'Dodge Active Window'.

\\:D/ Thank you! That could not have been easier. I'm so glad I can hide that bar.

---

### Post by Auroraei on 2011-12-16
Hmmm seems like one of my posts were deleted. I don't know why though.

---

### Post by nothingspecial on 2011-12-16
No it wasn't it's here

[http://ubuntuforums.org/showthread.php?t=1896091](http://ubuntuforums.org/showthread.php?t=1896091)

---

### Post by Auroraei on 2011-12-16
> **nothingspecial said:**
> No it wasn't it's here

[http://ubuntuforums.org/showthread.php?t=1896091](http://ubuntuforums.org/showthread.php?t=1896091)

Thank you! I didn't know lol.

---

### Post by Auroraei on 2011-12-16
*Deleted*

---

