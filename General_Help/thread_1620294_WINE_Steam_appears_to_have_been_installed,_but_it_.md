---
title: "WINE: Steam appears to have been installed, but it won't run."
date: 2010-11-12
forum: General Help
---

### Post by anthony62490 on 2010-11-12
Just bought The Orange Box today (finally) and I saw that Portal and Steam both get a platinum rating in the WINE App DB. So I:

Went to [http://store.steampowered.com/](http://store.steampowered.com/) and downloaded SteamInstall.msi

Opened terminal and entered ```
wine msiexec /i /home/anthony/Downloads/SteamInstall.msi
```

Followed various prompts and waited for Steam to update. After a while, Steam closed down and the Terminal stopped telling me what it was doing. It normally gives me a command prompt when it's finished with a task, but this time I had to press Enter before I could get a prompt. (This may be relevant, not sure yet)

Applications> Wine> Programs> Steam> Steam

**RESULT**: Steam creates a button in the bottom toolbar, but there is no window to go along with it.

Ubuntu 9.10
Wine-1.1.31

**_EDIT:_ Okay, it appears that I had WINE configured as Windows XP. I tried to install Steam for Win7/Vista. Just set Wine to run under Vista and it should work.**

---

