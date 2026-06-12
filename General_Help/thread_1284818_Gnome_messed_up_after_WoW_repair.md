---
title: "Gnome messed up after WoW repair"
date: 2009-10-07
forum: General Help
---

### Post by bluepop13 on 2009-10-07
I was trying out repairing World of Warcraft and after repairing it my Gnome Desktop Environment Resolution changed and I can't get it back to what it was. I'm stuck on what to do here. If there was a way to actually set my system back to yesterday I'd do that. Other than that I really don't know what exactly happened or what to do. Any help is truly appreciated!

Eric

---

### Post by Peter09 on 2009-10-07
Have you tried System->Preferences->Display

---

### Post by bluepop13 on 2009-10-07
I have went into preferences and done that, yes. I have also used xrandr in terminal with the help of a friend of mine. When I set it to what I thought it has been for so long everything gets real big, which isn't what I want. When I do get things looking the way I believe I wand them to then the icons and everything seems wider than should be. I have no clue what the hell happened here lol. Maybe I should reinstall ubuntu or something. Maybe more looking around and messing around with stuff. I guess the more you know the better and again the three rules of computers which I've never been one to follow and really should are backup, backup, backup lol. Thanks all the same!

Eric

---

### Post by Peter09 on 2009-10-08
OK try running the following in a terminal.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

this will reset your video display parameters.

---

### Post by bluepop13 on 2009-10-08
Actually I was able to fix my problem last night I believe. I thought I had my computer in a different resolution than it apparently was in. I was able to get it back to the resolution I had had it in and now everything works again as it should. Thanks for all help here to everyone. Much appreciated!

Eric

---

