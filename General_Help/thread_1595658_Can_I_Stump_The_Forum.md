---
title: "Can I Stump The Forum?"
date: 2010-10-13
forum: General Help
---

### Post by joeknoodle on 2010-10-13
Okay, here's the challenge my dear friends...  I would like to make a folder and / or file(s) available to the user / applications only at certain times of the day.   An example would be allowing the wallpaper changer to access  only my science pictures from say 8am to 1pm, then only allow automobile pictures from say 1pm to 5pm, then allow only architecture pictures from 5pm till let's say back to 8am. (I'm using DesktopNova if that helps, but I'm willing to try other wallpaper apps if they do as the challenge requests)   First one with a working solution is Ruler of the Intarwebs, their name to be hailed across the lands, with reverence, respect and the admiration he or she so deserves.

---

### Post by bouncingwilf on 2010-10-13
I don't know much about this sort of thing but I would start by taking the little man that operates the light in the fridge and give him a clock and a set of instructions; failing that I'd give the job to my mate cron.


Bouncingwilf

---

### Post by joeknoodle on 2010-10-13
> **bouncingwilf said:**
> I don't know much about this sort of thing but I would start by taking the little man that operates the light in the fridge and give him a clock and a set of instructions; failing that I'd give the job to my mate cron.


Bouncingwilf

So then, what might such a cron look like?

My googling and other searches show how to start apps on a schedule, but say nothing about blocking folders and files according to time of day.

---

### Post by bouncingwilf on 2010-10-13
As I stated in my original post I know nothing! but hundreds of years ago when I could just about find my way around the cli I might of used at to execute simple scripts that changed folder permissions etc. As you can probably guess, I'm shooting in the dark here but I'm sure I would of found a way of doing it. However, I'm also equally sure there's a much smarter solution - a clever poster will be along shortly sir. I was just trying to keep you amused while you waited.

Bouncingwilf

---

### Post by joeknoodle on 2010-10-13
> **bouncingwilf said:**
> As I stated in my original post I know nothing! but hundreds of years ago when I could just about find my way around the cli I might of used at to execute simple scripts that changed folder permissions etc. As you can probably guess, I'm shooting in the dark here but I'm sure I would of found a way of doing it. However, I'm also equally sure there's a much smarter solution - a clever poster will be along shortly sir. I was just trying to keep you amused while you waited.

Bouncingwilf
I am both amused and encouraged.

---

### Post by nothingspecial on 2010-10-13
First thoughts.

Use feh to handle your wallpaper. This script comes, I think, from the openbox wiki. It uses feh to create random wallpapers from a folder you specify.
```
WALLPAPERS="$HOME/path_to_your_wallpapers" ; ALIST=( `ls -w1 $WALLPAPERS` ) ; RANGE=${#ALIST
[*]} ; SHOW=$(( $RANDOM % $RANGE ));  feh --bg-scale $WALLPAPERS/${ALIST[$SHOW]}
```

You use cron or at to call variations of this script, where the path to the
path to the photo`s is different depending on the images you want displayed.

This script only picks one random wallpaper each time you run it.

Hope that gets you going.

***Edit  For some reason the forum is formatting the script as a single line, don`t know why??????

---

### Post by joeknoodle on 2010-10-13
> **nothingspecial said:**
> First thoughts.

Use feh to handle your wallpaper. This script comes, I think, from the openbox wiki. It uses feh to create random wallpapers from a folder you specify.
```
WALLPAPERS="$HOME/path_to_your_wallpapers" ; ALIST=( `ls -w1 $WALLPAPERS` ) ; RANGE=${#ALIST
[*]} ; SHOW=$(( $RANDOM % $RANGE ));  feh --bg-scale $WALLPAPERS/${ALIST[$SHOW]}
```You use cron or at to call variations of this script, where the path to the
path to the photo`s is different depending on the images you want displayed.

This script only picks one random wallpaper each time you run it.

Hope that gets you going.

***Edit  For some reason the forum is formatting the script as a single line, don`t know why??????
Got it!

I'll use cron to enact different feh scripts throughout the day.

Let all who witness this proclamation know that nothingspecial is Ruler of the Intarwebs, entitled to all rights and privileges thereof, and whose name shall be spoken only with reverence, respect, and admiration!

---

### Post by ean5533 on 2010-10-13
> **joeknoodle said:**
> Let all who witness this proclamation know that nothingspecial is Ruler of the Intarwebs, entitled to all rights and privileges thereof, and whose name shall be spoken only with reverence, respect, and admiration!

You'll of course be responsible for maintaining that proclamation, reminding the Intarwebs of nothingspecial's greatness in case in forgets.

---

### Post by efflandt on 2010-10-13
See **man crontab**, **man 5 crontab**, and **man chmod** in a terminal.  Depending upon who a directory is owned by, a directory needs **x** permission (which for a directory means **access** instead of execute) for that user, group, or other, in order to access that directory (do ls, etc. on it) and I think also **r** (read) permission to read files from it.

So if the directory is owned by root you could use **sudo crontab -e** to configure when (time) to **chmod 700** or **chmod 755** that directory.  But if you are not familiar with the default editor similar to **vi**, you may want to first set a different editor with **export EDITOR=nano**.

---

