---
title: "What happened? no icons on desktop only background"
date: 2012-05-02
forum: General Help
---

### Post by rreyes3713 on 2012-05-02
So I change back some setting on xorg,conf file because during an "Upgrade Manager", some upgrade Nvidia settings were changed and my monitor wasn't running at optimum performance.

Anyway, changing back worked. But when playing with the Nvidia setting with dual monitor setting and restarting, I only have the background on the desktop. No icon to press. Seems like playing with the monitor setting messed up with the desktop.

How do I get it back? I can't select "Safe Mode" at GRUB menu because setting are messed up, I can't even get USER selection menu on Safe Mode.

Help!

---

### Post by rreyes3713 on 2012-05-02
I figured it out.

Changing the setting on Nvidia app (via Administration -> Nvidia Settings), made me loose my menu bar and icons.

To recover, press **Alt-F1**,

you'll see "**Application**" menu.
press arrow twice, you'll see "**System**" menu.

Depending where you did your settings, select from the pull down menu either "**Preference**" or "**Administration**"

From there again pull down menu select **monitor **or your **graphic card setting**.
Change your setting to a smaller size monitor settings.

You will have to restart your computer.

Press **Ctrl-Alt-Del** and that will bring you to "**Shut Down the Computer**" menu. Select "**Restart**."

If that doesn't display your menu bars and icons then repeat.

Yes, I know, probably fundamental things I should have known but maybe this will help others.

---

