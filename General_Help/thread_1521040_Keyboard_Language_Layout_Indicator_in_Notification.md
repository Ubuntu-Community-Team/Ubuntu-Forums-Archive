---
title: "Keyboard Language Layout Indicator in Notification Area?"
date: 2010-06-30
forum: General Help
---

### Post by dubref on 2010-06-30
How to properly show Keyboard Layout Indicator on my desktop?

Finding Keyboard Layout Indicator appears to be [SOLVED] if you only have one language layout and add second. 
[http://swiss.ubuntuforums.org/showthread.php?p=9486803](http://swiss.ubuntuforums.org/showthread.php?p=9486803)

However, I already had two language layouts and couldn't find an indicator... for kicks I added a third language (Russian) and now can switch between three languages, but I still do not see any indicators of my current layout state.

I have a rather basic 10.04 install, at least nothing has been removed.

Top right of my top panel consists of the following:
Indicator Applet Session 0.3.7
Notification Area 2.30.0
Clock 2.30.0
Log Out applet
(this is per default install)

Middle of my top panel is rather cluttered with various launchers.

I looked at [http://library.gnome.org/misc/release-notes/2.30/](http://library.gnome.org/misc/release-notes/2.30/) 
found the following tidbit:
"When you choose multiple keyboard layouts the status icon automatically appears in the notification area."

Now my finding: If I furiously right click on the Notification Area, I can find Keyboard Layout mini-menu at RANDOM places on this Area. 

**The location of the layout indicator is not consistent**. 

Similarly, by simply moving mouse over Notification Area I can find some pixels where MouseOver will show current Language Layout, but the location varies..

This takes some time (15 seconds at worst case) and is an extremely inconvenient way of showing current layout. The active area appears to be rather small maybe 5x5.

What would be the proper way to show the language layout indicator? That is I would like to see tiny letters indicating current layout state somewhere.

EDIT: Well, the inconsistency problem was solved by good old reboot, which was performed as part of kernel upgrade(most likely kernel had nothing to do with this). 

Now, Notification Area shows current language layout state with nice three letter acronyms(USA etc), like it was supposed to in the first place..

---

