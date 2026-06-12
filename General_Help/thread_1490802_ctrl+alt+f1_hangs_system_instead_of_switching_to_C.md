---
title: "ctrl+alt+f1 hangs system instead of switching to CLI."
date: 2010-05-22
forum: General Help
---

### Post by Flanger on 2010-05-22
Hello everybody.
I have been trying to switch to CLI mode for 2 hours now, I have searched possible solutions and I couldn't find any so I decided to make a new topic.

I'm running Kubuntu 10.04 x86_64. I need to log into CLI to stop KDE from running, but I just can't get there.

When I try ctrl+alt+F1 the only thing happens is that mouse pointer disappears and everything else (background, panels, etc.) stays the same, and frozen, no keyboard input helps.
Then when I perform ctrl+alt+F7 it gets me back into GUI. I have also tried sudo chvt 1, same effect. Then I tried to change inits. sudo init 1 and sudo init 2 give me just a blank black 
screen and where only reboot helps. init 3 doesn't do anything (guess I'm already running init 3 and thats why).

Could somebody help me with this?

Thanks.

---

### Post by dcstar on 2010-05-23
> **Flanger said:**
> Hello everybody.
I have been trying to switch to CLI mode for 2 hours now, I have searched possible solutions and I couldn't find any so I decided to make a new topic.

I'm running Kubuntu 10.04 x86_64. I need to log into CLI to stop KDE from running, but I just can't get there.

When I try ctrl+alt+F1 the only thing happens is that mouse pointer disappears and everything else (background, panels, etc.) stays the same, and frozen, no keyboard input helps.
Then when I perform ctrl+alt+F7 it gets me back into GUI.
.........

Things like this are usually issues with the video drivers or misconfigured /etc/X11/xorg.conf files.

---

