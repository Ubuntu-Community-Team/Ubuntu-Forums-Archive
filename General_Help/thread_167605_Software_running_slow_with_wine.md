---
title: "Software running slow with wine?"
date: 2006-04-28
forum: General Help
---

### Post by morbid_bean on 2006-04-28
I installed my game using wine..(starcraft) and my system is totaly able to run this game. however...when i open the starcraft.exe and at the menus i have a choppy like lag...how do i fix this??

---

### Post by slowestman on 2006-04-28
[QUOTE=morbid_bean]I installed my game using wine..(starcraft) and my system is totaly able to run this game. however...when i open the starcraft.exe and at the menus i have a choppy like lag...how do i fix this??[/QUOTE]
Same here but I can only play offline games are you able to play on battle-net?

---

### Post by kenweill on 2006-04-28
Same here. I've been playing MU Online through wine. Graphix sucks.
But the latest version of wine(0.9.12) is much faster now compared to the past versions.
But its not as good as playing the game in windows.

---

### Post by YokoZar on 2006-04-29
Wine has been generally slow with 2D DirectDraw apps (such as Starcraft) because it renders them in software mode rather than OpenGL.

A lot of work on getting DirectDraw to run in accellerated mode has been going on, however (alongside architectural changes to the Wine Direct 3D code), and it's all just about ready to merge.  My guess is that within the next version or two (that is, the next couple of weeks) the Wine D3D merge will be complete and your DirectDraw apps will be running via OpenGL for the first time.

---

