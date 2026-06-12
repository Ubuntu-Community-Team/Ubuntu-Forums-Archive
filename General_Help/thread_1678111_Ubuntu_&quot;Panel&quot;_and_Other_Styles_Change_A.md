---
title: "Ubuntu &quot;Panel&quot; and Other Styles Change After Driver Install / System Update"
date: 2011-01-29
forum: General Help
---

### Post by Aea on 2011-01-29
I have a brand new install of Ubuntu, I have installed restricted drivers and upgraded system software (I believe all during one session without a start), after restarting my computer the panel style changed to another (ugly) style. I have ensured that I restarted multiple times afterwards and that the system -> pref -> appearance setting is set to "Ambiance."

I have also tried:

```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```and 

```
gconftool --recursive-unset  /apps/panel 
```Which both restart the panel but the style doesn't change. For reference it looks like: 

[http://i.imgur.com/LbrNw.jpg](http://i.imgur.com/LbrNw.jpg)

I have a Dell M6500 w/ an Nvidia graphics card. 

It could be noted that I have previously installed Ubuntu on this machine (for testing on another drive) and have upgraded (although possibly in piecemeal) without this problem happening. Any assistance would be appreciated, otherwise I'll likely reinstall as the time to do so has so far been less then trying to fix this problem. 

Thanks again for any help!


Edit: Did some experimenting, reinstall system and installed the recommended NVidia restricted driver (from the system -> administration menu), I had a choice of "Version 173" and "Recommended," as soon as I did and restarted the retro styling returned, am going to try using the (presumedly) newer driver in a bit.

---

### Post by Aea on 2011-01-29
After doing some experimentation it appears that installing the drivers will always cause the top and bottom panel to change, but deactivating a driver and restart will cause the default (and nice looking) style to return. 

Anybody have any ideas, or does this seem like drivers are the culprit?


Okay, after some more research I've found: 

[http://ubuntuforums.org/showthread.php?t=1611286&page=2](http://ubuntuforums.org/showthread.php?t=1611286&page=2)
[http://ubuntuforums.org/showthread.php?t=1575703&page=9](http://ubuntuforums.org/showthread.php?t=1575703&page=9)

After reinstalling nautilus the problem is resolved, appears to stick between restarts, notably gnome-settings-daemon didn't (appear to) start before doing that change.

Edit #2:

Nope, that was a lie, disabled proprietary driver, removed ~/.gconf and ~/.gconfd. 

This is aggravating.

---

### Post by p_motch on 2011-01-30
I have this problem in Ubuntu 10.10 64-bit as well. I run an ATI HD5970 gfx card. When I install Ubuntu, all is fine. Once I update everything, and install the default restricted driver for the ATI gfx card, that's when I get a similair image to the one you attached in the original post.

I found that if I add gnome-settings-daemon to Startup Applications, it works just fine. Not sure why though. It's a bug I hope they fix soon.

---

