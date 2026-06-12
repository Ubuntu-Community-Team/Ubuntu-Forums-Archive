---
title: "startup commands/scripts - help?"
date: 2006-03-16
forum: General Help
---

### Post by jms830 on 2006-03-16
ok, so i followed this guide [https://wiki.ubuntu.com/RotateWallpapers](https://wiki.ubuntu.com/RotateWallpapers) in order to make my wallpapers rotate every X seconds.  Now I've tried putting in the command "/home/jordan/theme/wallpaper/change-bg 10 /home/jordan/theme/wallpaper" (without quotes) into sessions>startup programs and that did not work, then i tried putting that command into an .sh script file and using the command "/home/jordan/theme/wallpaper/screenstarter10sec.sh" (without quotes) as a startup command, but nothing seems to be working.  Both the command and the script work fine when i run the commands once im logged in, but they will not work at login, any suggestions?

---

### Post by dcstar on 2006-03-17
[QUOTE=jms830]ok, so i followed this guide [https://wiki.ubuntu.com/RotateWallpapers](https://wiki.ubuntu.com/RotateWallpapers) in order to make my wallpapers rotate every X seconds.  Now I've tried putting in the command "/home/jordan/theme/wallpaper/change-bg 10 /home/jordan/theme/wallpaper" (without quotes) into sessions>startup programs and that did not work, then i tried putting that command into an .sh script file and using the command "/home/jordan/theme/wallpaper/screenstarter10sec.sh" (without quotes) as a startup command, but nothing seems to be working.  Both the command and the script work fine when i run the commands once im logged in, but they will not work at login, any suggestions?[/QUOTE]
Try this in a file:
```
#! /bin/sh
#
/home/jordan/theme/wallpaper/change-bg 10 /home/jordan/theme/wallpaper
```
And make it Executable.

---

