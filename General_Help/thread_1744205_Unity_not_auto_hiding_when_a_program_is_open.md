---
title: "Unity not auto hiding when a program is open"
date: 2011-04-30
forum: General Help
---

### Post by faillord adam on 2011-04-30
Unity won't auto hide itself when I open a program, and it gets in the way of things like Google Chrome. This seems to only happen when using Unity 3D, not 2D. I'm using the experimental NVIDIA Drivers, but the problem was also present when I used the proprietary drivers. I have an Acer Aspire 5630 with a GeForce Go 7300.

:confused:

---

### Post by 3rdalbum on 2011-04-30
> **faillord adam said:**
> Unity won't auto hide itself when I open a program, and it gets in the way of things like Google Chrome. This seems to only happen when using Unity 3D, not 2D. I'm using the experimental NVIDIA Drivers, but the problem was also present when I used the proprietary drivers. I have an Acer Aspire 5630 with a GeForce Go 7300.

:confused:

If you haven't already, install compizconfig-settings-manager. Hit Alt-F2 and type 'ccsm' and hit Enter, to launch the settings manager.

Go to the Unity plugin and under "Hide Launcher", choose "Dodge Windows". This will immediately make the Unity launcher hide whenever a window is overlapping it.

---

### Post by faillord adam on 2011-04-30
> **3rdalbum said:**
> If you haven't already, install compizconfig-settings-manager. Hit Alt-F2 and type 'ccsm' and hit Enter, to launch the settings manager.

Go to the Unity plugin and under "Hide Launcher", choose "Dodge Windows". This will immediately make the Unity launcher hide whenever a window is overlapping it.
Unity still gets in the way. None of the other settings do anything either.

---

### Post by AbdRahim on 2011-05-02
I have the same problem, except, I noticed the Nvidia driver (current) was activated but not used. I uninstalled the nouveau drivers, but nothing I tried would get the OS to use he Nvidia driver. Of course you said you could not achieve the proper launcher behavior with the proprietary driver, so I am at a loss for a solution. I guess Unity 3D is really not ready for prime time usage. I would think for most non gamers wouldn't need it anyway.

---

### Post by faillord adam on 2011-05-04
It's happening with Unity 2D now.

---

### Post by cub on 2011-05-05
Same here. Sometimes the Dodge Windows work all day, sometimes it just stops hiding and stay that way until I log out/in. I tried to restart unity but it didn't change anything. Annoying. I won't accept rebooting my pc or log out/in to get things to work, I left that with Windows..;)

---

### Post by kiddykoff on 2011-05-05
I'm having the same problem.

I tried installing the Gnome3 ppa, but it was buggy. It wasn't easy (for me at least) to figure out how to come back to Unity.

---

### Post by cub on 2011-05-05
I found a workaround on launchpad. Drag an icon from the desktop over the launch bar (no need to drop the icon) and then back to the desktop again. Suddenly the bar decides to hide again. Not perfect, but it worked for me.

---

### Post by Fjodr on 2011-05-19
I can't believe that actually worked. I tried unity --replace before but it refused to go back into hiding. Seems more like a Compiz glitch if it's linked to dragging icons from the desktop or nautilus to the launcher.

---

### Post by kernelles on 2011-05-19
I have the same problem on two different machines.

---

### Post by alan200994 on 2011-05-23
This seems to be working for me, great word-around!:P

---

### Post by micael3000 on 2011-05-23
I gave up on that and made it never hides... This way it doesn't stay in front of my applications...
It is completely buggy. It just stuck and doesn't retreat anymore sometimes.

---

### Post by leviathan8 on 2011-05-23
Open a terminal and type

```
unity --reset
```

Wait 30 seconds (until the text stops scrolling), close the terminal, log out and back in, and hopefully - problem solved!

---

### Post by BigJules on 2011-05-23
Another way that works for me - don't know why - is to switch to workspace 1 then back. I have my workspaces bind to the top keypad keys so it's a very quick thing. (Compiz settings mgr Viewport switcher > go to specific viewport)

---

### Post by faillord adam on 2011-08-13
This bug appears to be fixed in Ubuntu 11.10 Oneiric Ocelot.

---

### Post by Ludd1te on 2012-07-17
Dragging an icon onto it used to work for me in 11.10, but no longer in 12.04.

unity --reset does work, ***but***: it resets *all* settings, so afterward it will revert to the default changes, e.g., not autohiding (i.e., fixed), erasing any key-binding mods, re-appearong on both my monitors.  All from it glitching.

As a digression, I love the *idea* of the HUD instead of menus, etc., but my experience is that it's unable to find even simple commands (e.g., save, find, insert:comment, etc.) or to suggest commands I'm not 100% what they're called; in both cases, I end up looking at the menu bar anyway.  Instead I use Cairo-Dock & Synapse/Kupfer.  O.K., I'm done ranting.  Sorry I come across so vexed in this reply.  :(

---

