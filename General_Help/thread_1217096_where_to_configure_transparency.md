---
title: "where to configure transparency?"
date: 2009-07-19
forum: General Help
---

### Post by serious7 on 2009-07-19
Does anybody know how I can configure transparency thru compiz setting manager? I did google searches and I foudn no solution. I cannot hold ald and use mouse wheel. I cannot find opacity setting in general options of compiz settings manager. Please help.

---

### Post by serious7 on 2009-07-19
please guys. I really cant find the option. It just doesnt exist in general settings. I looked everywhere.

---

### Post by vinutux on 2009-07-19
in compiz config enable opacity -- tick opacity tab when mouse-over

tick Opacity,brihtness and saturn tab - window-skey with + for increase - windwskey+- for decrease

---

### Post by geirha on 2009-07-19
Not using compiz at the moment, but I think it's called opacity settings or something like that.

---

### Post by Cresho on 2009-07-19
in compiz on hardy heron use
compiz config settings manager->General options-opacity
click new and add Tooltip | Menu | PopupMenu | DropdownMenu and with a 68

then add blur to the opacity

Tooltip | Menu | PopupMenu | DropdownMenu | class=Gnome-terminal | class=Awn


make sure they are enabled.  In jaunty opacity has its own tab instead of it being in general.

Also, adding opacity will cause your games and such to look opacity so i add a script launcher to specific games.
```
#!/bin/bash
#Script Compiz/on/off

# Compiz off;
killall compiz.real &
metacity --replace &

#run game;
cd /home/someguy/Installed_Programs/astromenace
./game_launcher

#Compiz on;
compiz --replace &
metacity --replace &
```

---

### Post by CatKiller on 2009-07-19
The plugin that lets you make windows transparent with Alt-mousewheel is the Opacity, Brightness and Saturation plugin. It's in the Accessibility section of CompizConfig Settings Manager.

---

### Post by serious7 on 2009-07-19
Thanks guys. There was confusion because some versions had opacity setting in general tab. I was so confused because I couldnt find that silly tab in the general settings LOL. Thanks!!!!!

---

