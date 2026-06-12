---
title: "Bang mouse-cursor on corner screen = display all windows"
date: 2010-02-20
forum: General Help
---

### Post by vizitorq on 2010-02-20
Hey guys I just installed ubuntu 9.10 and I'm wondering where the setting is to set a corner or side of your monitor that allows you to bang your mouse in that area and it displays all the windows on all virtual desktops, allowing you to click any of them and automatically takes you to that window on that virtual desktop.

I believe this is something in compiz, which I have installed, but I can't find it in the CCSM. Can someone help me find this feature?

Thanks

---

### Post by The Toxic Mite on 2010-02-20
Compiz... no, probably not. This is probably something to do with GNOME Shell. Can you expand on this in any way possible?

---

### Post by vizitorq on 2010-02-20
Ya sure. So let's say you have 4 virtual desktops. Not meaning that you have windows running virtually, centos running virtually, ubuntu, and slackware, all running virtually in windows inside your one OS... Not at all.

I'm talking about the native linux virtual desktops. Let's say I have 4 of them, and I have the compiz cube enabled. In 8.10 I had an easy to get feature that enabled me to bang the mouse cursor on the bottom-left of my screen, and instantly the background of my screen would fade out and all the open windows in all my virtual desktops would be displayed in that one screen (minimized to fit all of them) almost like a menu. Then I could click any one of them, and it would instantly take me to that window on whatever virtual desktop it was on. 

Does that make more sense? I'm pretty sure it has something to do with compiz or just gnome.

---

### Post by punchdrunkgrunt on 2010-02-20
It's called Expo. I'm not sure if it's in simple-ccsm. Try installing the "proper" config utility

```
sudo apt-get install compizconfig-settings-manager
```

and look in the Desktop section.

---

### Post by vizitorq on 2010-02-20
It is not expo. That does not follow the description I provided at all. Please read carefully. I didn't say it showed all desktops. I said it showed all windows in all desktops, but displays them in the current desktop.

---

### Post by punchdrunkgrunt on 2010-02-20
My bad. I think it's Scale and it's in the Window Management section.

---

### Post by realzippy on 2010-02-20
Compiz,"shiftswitcher".
You have to configurate mouse action "top left edge" of course....

---

### Post by mcduck on 2010-02-20
> **punchdrunkgrunt said:**
> My bad. I think it's Scale and it's in the Window Management section.

This is correct, the **Scale** plugin is what allows you to view scaled-down versiosn of all your windows (from one workspace, or all of them) at the same time and swich between them by clicking on them. It's the one that works like expo does on OSX, and can be activated from screen corners.

Shif SWitcher is just one of the fancy Alt-tab tools to browse through your open windows, but it doesn't view all of them at the same time, and doesn't allow you to click on a window with to change to it, instead you have to repeat clicking the shortcut until you get the window you want.

Expo shows miniature versions of your desktops, not your open windows.

---

### Post by vizitorq on 2010-02-20
Thank you so much! It is scale. Initiate window picker for ALL windows, is what I was lookin for. Thanks for the help everyone!

---

