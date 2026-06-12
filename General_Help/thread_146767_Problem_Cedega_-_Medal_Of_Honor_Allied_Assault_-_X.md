---
title: "Problem: Cedega - Medal Of Honor: Allied Assault - XGL / Compiz - Latest ATI Drivers"
date: 2006-03-18
forum: General Help
---

### Post by Bradl3yJ on 2006-03-18
I have been working on this all day, and have made very little progress, i hope someone can help me.

I am running Breezy on x86 with a ATI Raedon 9600 XT, with the latest drivers from ati website installed.

I have been running XGL+Compiz on Breezy for a few days. and it runs great. I am trying to run Medal of Honor Allied Assault via cedega. I installed it on my windows partiton, booted ubuntu and copied the files over to my ubuntu partition, added it to cedega. The intros, menus, and sound all work great, but when i try to join a game or start a campaign, it loads, and then almost all of the textures are missing, everything is black exept for the sky, windows, doors, foilage, crates and such (any models that arent directly part of the map it seems).

I figured it might be XGL/Compiz interfering, so i disabled it by editng my gdm.conf and changing:

```
#1=Standard
1=xgl
```
to
```
1=Standard
#1=xgl
```


Well, now the game will not run at all! The first box pops up which is the console before it goes full screen, doesnt display any output and disappears within seconds. I have tried using the native linux installer (i'd prefer not to go this route, i hear its buggy and the sound sucks), and get errors in terminal, no windows open.

I tried enabling XGL again, and the game will launch again, with the black texture issue. Are there different config files for standard and xgl? Are my ATI drivers not loading when i don't have XGL running?

---

### Post by Bradl3yJ on 2006-03-19
I completely cleared my ubuntu partition, and reinstalled, First thing i installed was the fglrx from the default respositories. Then i ran the dpkg -reconfigure thing, and selected fglrx for my drivers. I then installed cedega, and i was actually able to install the game from the CD this time, i was albe to update the game from the official patch, i replaced the game executable with the NO-CD crack, and it plays fine now!

So something I had installed must had been configured all screwy, it seems when i do run that dpkg -reconfigure screen or whatever command that is to select fglrx, instead of adjusting the device for my video card in xorg.conf, it creates a second device, which could of had something to do with it. Oh well, in any case for now im sticking with the fglrx in the repositories until i find a game that needs updated drivers!

Incase anybody here is having similar issues with an ATI card and this game, try installing drivers from the repositories. As far as the cedega profile i used for the game, i disabled NV_VAR Extension because i believe thats for nvidia onle (correct me if i am wrong), and I used xRandR instead of using Xvid mode, xRandR adjusts the resolution of the actual screen for the game, and allows me to adjust brightness settings from within the game, where xvid mode if my desktop was 1024x768 ad the game was 640x480, the game would be up in the left corner of the screen, and the rest of the screen was black, and brightness adjustment did not work.

---

