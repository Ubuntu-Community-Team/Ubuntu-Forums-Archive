---
title: "Video Flicker - DRI setting"
date: 2006-04-19
forum: General Help
---

### Post by jkahan on 2006-04-19
For those who are experiencing an odd flicker on your screen that appears to be a sync problem, I think I have found a fix.

This definately works with the ATI 200M on an Averatec 2155 (21xx).

Apt-get install driconf, run this app and make sure that "Synchronize buffer swap with vertical blank" is set to "no". Save this change with the save buttonthen exit. No reboot necessary.

If it is not obvious, to see this setting, browse the tree in the left pane of the window and make sure you are on the lowest level named "all".

It will cost you a few FPS's though, personally it is worth it.

---

