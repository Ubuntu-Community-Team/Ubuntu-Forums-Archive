---
title: "Panel Menus rearrange when using &quot;Expand&quot;"
date: 2009-08-03
forum: General Help
---

### Post by Cuco3 on 2009-08-03
Hi everyone, first time here!

Just so you know, I have tried searching for a solution, but the ones that even came remotely close to what I was trying to accomplish didn't work.

I'm using Ubuntu 9.04 completely updated.

When I use "Expand" for the Gnome Panels, it works fine until I logoff/restart. When I do, it rearranges the location of where the menus should be.
[URL="http://img194.imageshack.us/img194/1392/screenshotssr.png"]
[/URL][B][Screenshot 1 (working)]("http://img4.imageshack.us/img4/1197/screenshottcz.png")[URL="http://img194.imageshack.us/img194/1392/screenshotssr.png"] 
[/URL][Screenshot 2 (broken)]("http://img37.imageshack.us/img37/9056/screenshot2cvj.png")[/B] (for the bottom panel, notice how the trash/show desktop/workspaces are on the left, the open programs are on the right. for the top panel, notice how the "Applications, Places, System" are completely on the left, and the "date/time/name/lan/volume" are completely on the right.

In order to revert to the default panels, I have to go to a terminal shell and run the following commands:
```
gconftool-2 --shutdown

rm -rf ~/.gconf/apps/panel

pkill gnome-panel
```Is this still a bug with Gnome or is there a workaround available?

Thanks in advance for your help!

---

### Post by jerrrys on 2009-08-03
an observation...the three dots appear on your screen six times.  as far as i know the three dots only represent two things.  #1 Windows List  and  #2 Notification Area.  try taking out the rest...i think you have four too many and thats the problem...

---

### Post by Cuco3 on 2009-08-04
> **jerrrys said:**
> an observation...the three dots appear on your screen six times.  as far as i know the three dots only represent two things.  #1 Windows List  and  #2 Notification Area.  try taking out the rest...i think you have four too many and thats the problem...Didn't work, but I tried deleting the menus and manually rebuilding the entire menu the way I wanted. I got it the way I like it and it seems to be saving now after rebooting.

Thanks for your help, hope this continues to save it!

---

