---
title: "Temporarily disable Composite"
date: 2010-07-13
forum: General Help
---

### Post by tgrego on 2010-07-13
Hello all.

I've installed a game on Ubuntu 10.04 x86, but it will crash if I just run it...

I've managed to get it to work if I create the file /etc/X11/xorg.conf (which doesn't even exist originally) with
```

Section "Extensions"
	Option "Composite" "Disable"
EndSection

```
and restartx.

I can play, but first I have to make that file and restart X, after I'm done playing I have to remove the file and restart X again... which is not very nice...

I'm trying to figure out how I can have the same effects without reboot/restartx, by disabling Composite temporarily.
I tried to disable compiz, but the game will crash with just disabling compiz...
Anyone can help?

Thanks

---

### Post by x-shaney-x on 2010-07-13
You could install fusion-icon, it will run in the system/notification tray and you can disable and enable it from there.

---

### Post by stinkeye on 2010-07-13
So the game won't run if you enable metacity as your window manager?
```
metacity --replace
```

Metacity has a compositing feature which can be disabled in gconf-editor
/apps/metacity/general/compositing_manager


fusion-icon will give you a right click menu in the notification area
to easily switch window managers.
```
sudo apt-get install fusion-icon
```

---

### Post by tgrego on 2010-07-13
I've installed fusion-icon, but with no luck in solving the problem...
Using fucion-icon to change Window Manager to metacity (with /apps/metacity/general/compositing_manager feature disabled) has the exact same effect of turning compiz off (at least the way I did it, which was selecting None in the Appearance/Visual Effects menu).
It will cause the game menu to start normally, but as soon as a game is started it will crash...)

By the way, without turning off compiz (or using the fusion-icon) the game menu will show up kind of transparent (fused with the desktop and unusable...). This also happens when using the fusion-icon and selecting the window manager metacity with /apps/metacity/general/compositing_manager feature enabled.

So by now the only way I have is still the xorg.conf edit and X restart...

---

