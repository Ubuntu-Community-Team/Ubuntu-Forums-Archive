---
title: "Assign each workspace to a different wallpaper"
date: 2011-06-28
forum: General Help
---

### Post by anton706 on 2011-06-28
Hi I want to Assign each workspace to a different wallpaper in the following way:
workspace 1:Will have an image slide show that will use the wallpapers which change with the time of the day from this site:
[http://barid42.deviantart.com/art/A-Day-in-the-Life-204881196](http://barid42.deviantart.com/art/A-Day-in-the-Life-204881196)
 So in that workspace the wallpaper will change with the time of the day using these wallpapers.

workspace 2,3,4:Will have a fixed (different wallpaper).

can somebody help me accomplish that?

---

### Post by p-dh on 2011-06-28
I can get you started on the right path. To have a different wallpaper for each desktop, you'll need to use compiz and the Wallpapers plugin.

I'm not sure how you can choose a utility to have one desktop with changing wallpaper.

Paul

:cool:

---

### Post by pqwoerituytrueiwoq on 2011-06-28
this can be done but you will not be able to have icons on your desktop or right click the desktop
enable compiz wallpaper
add your wallpaper
open [FONT=Courier New]gconf-editor[/FONT]
un-check the following:
[FONT=Courier New]/apps/nautilus/preferences/show_desktop
[/FONT]

---

### Post by anton706 on 2011-06-29
> **pqwoerituytrueiwoq said:**
> this can be done but you will not be able to have icons on your desktop or right click the desktop
enable compiz wallpaper
add your wallpaper
open [FONT=Courier New]gconf-editor[/FONT]
un-check the following:
[FONT=Courier New]/apps/nautilus/preferences/show_desktop
[/FONT]
and that will allowme to add changing wallpaper+fixed ones?

---

### Post by Grenage on 2011-06-29
> **anton706 said:**
> and that will allowme to add changing wallpaper+fixed ones?

It will be the same wallpapers, but it should be possible.  If you tell compiz to use papers in a directory (like /home/anton/paper/1.jpg and /home/anton/paper/2.jpg), then have a script which copies 'random' images from a folder and replaces them.  The path and file name will be the same, so the machine should start using it.

Oddly enough, when I try it here, the screen only updates the wallpaper instantly if I overwrite the original using the cp command; the mv command does the job but doesn't update the screen.

---

