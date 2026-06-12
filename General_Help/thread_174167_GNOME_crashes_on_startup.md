---
title: "GNOME crashes on startup"
date: 2006-05-11
forum: General Help
---

### Post by AirRaven on 2006-05-11
I've been playing around with my settings a little, and I seem to have completely... Trashed GNOME.

I recall that I was playing with themes when I started having problems, and now, after restarting, it doesn't seem to be able to load its theme. It just loads, blanks out, then loads again, and carries on until I reboot.

Is there any way of fixing this? Any way of configuring GNOME from the terminal?

---

### Post by Dr. Nick on 2006-05-11
[quote=AirRaven]I've been playing around with my settings a little, and I seem to have completely... Trashed GNOME.

I recall that I was playing with themes when I started having problems, and now, after restarting, it doesn't seem to be able to load its theme. It just loads, blanks out, then loads again, and carries on until I reboot.

Is there any way of fixing this? Any way of configuring GNOME from the terminal?[/quote]

You try to login to the failsafe session? I think you can also delete some hidden gnome folders in your home directory to reset it, not sure which ones though

---

### Post by VanHammersly on 2006-05-11
I'm having the same problem in Dapper.  I was using Kubuntu, apt-got gnome, was using fine one day (until I tried xgl/compiz) and now cannot get into Gnome.  KDE is fine.  No problems.  When I try gnome, though, top and bottom task bars blink white a few times and disappear.  I'd be open with just completely removing Gnome and reinstalling but all of my Googling has come up with no howto on acheiving this.

---

### Post by Dr. Nick on 2006-05-11
[quote=VanHammersly]I'm having the same problem in Dapper.  I was using Kubuntu, apt-got gnome, was using fine one day (until I tried xgl/compiz) and now cannot get into Gnome.  KDE is fine.  No problems.  When I try gnome, though, top and bottom task bars blink white a few times and disappear.  I'd be open with just completely removing Gnome and reinstalling but all of my Googling has come up with no howto on acheiving this.[/quote]

Im beting you edited a file with the xgl/compiz tutorial that is goofing you up, maybe your gdm setup file. Look at the tutorial you followed and undo teh changes that way

---

### Post by AirRaven on 2006-05-11
Fixed it up to a point- I can get into GNOME now. I just went into XFCE and went to the Gnome control center via the Debian menu. Failsafe GNOME crashed on startup- it was theme related. I'm guessing it couldn't find the theme it was looking for and bailed.

...Is there any way of deleting themes/Window borders/icon sets/gtk controls? I've got a few that are causing problems.

EDIT: In addition, all my window borders seem to come up as blue- even when I change the controls. It doesn't bother me much, since I use an OS X-imitation border, but I'd like to fix it. Any ideas how it could be done?

Thanks for the help.

---

