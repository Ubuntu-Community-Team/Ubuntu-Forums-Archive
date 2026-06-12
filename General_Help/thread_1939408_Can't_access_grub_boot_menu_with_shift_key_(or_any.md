---
title: "Can't access grub boot menu with shift key (or anything else)"
date: 2012-03-11
forum: General Help
---

### Post by Yleeyas on 2012-03-11
Hi folks,

I recently installed Ubuntu 11.10 (64 bit) on a new (to me) AMD dual core system, and have been trying to get used to Unity for the last 2 weeks.

I tried to access the grub2 boot screen using the shift key, but no joy. I've searched these forums for help and found some references to:

1) repeatedly pressing <esc> key - didn't work
2) cntl-alt-del - didn't work (delete gets me into bios on this machine)
3) powering down during boot - didn't work

This bit may be a clue or a red herring, but when I powerup/boot/restart or shutdown, there is a box floating around reading 'video mode not supported'. According to my Samsung docs this is just a warning about a refresh freq mismatch between video card (onboard Nvidia 7025) and the monitor, but the boot goes ahead normally, and the monitor is fine.

This is troubling that I can't get to the boot screen so any help/insight would be much appreciated :)

tia

ps Is there  'unity for dummies' thread around here ;)

---

### Post by oldfred on 2012-03-11
I have these two links:
Unity info
[http://www.omgubuntu.co.uk/2011/04/how-to-add-folder-quicklists-to-the-home-launcher-in-ubuntu-unity/](http://www.omgubuntu.co.uk/2011/04/how-to-add-folder-quicklists-to-the-home-launcher-in-ubuntu-unity/)
[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)

One user was having keyboard issues and I suggested BIOS settings, but he replaced keyboard ($20) and it worked. Do you have USB keyboard setting in BIOS? Windows & Ubuntu seem to add own drivers but grub uses BIOS setting and if not turned on in BIOS keyboard does not work.

Enabling USB Legacy Support - If keyboard does not work.
[http://support.creative.com/kb/ShowArticle.aspx?sid=5754](http://support.creative.com/kb/ShowArticle.aspx?sid=5754)
[http://ubuntuforums.org/showpost.php?p=9203674&postcount=5](http://ubuntuforums.org/showpost.php?p=9203674&postcount=5)

Fast Boot setting prevents keyboard from working & other issues
Bios not loading no key works - disconnected power for about 10-15 minutes and the bios reset itself.

or
No grub menu even with shift key. Not sure if Start-up manager is still current, try grub customizer first:
Use Start-up manager to change resolution.
Repair grub's video mode and other settings
[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

---

### Post by Yleeyas on 2012-03-11
WOW! Thanx oldfred, for the quick response and all the references. 

I don't have a USB keyboard but I'll have a look around the grub-customizer and start-up manager and see what's there wrt screen resolution, incase that's causing the bypass.

later

---

### Post by Yleeyas on 2012-03-11
Grub-customizer helped alot!! I found that by resetting the grub screen resolution to a (default) low value, it got rid of the floating warning (GREAT!), but holding the shift key, or 'toggling' the esc key still don't work.(unless my timing is off?)

HOWEVER! When I try the power-down in the middle of the boot/restart and then powering up, and THEN hold the shift key, it (3 of 5 times) got to the grub boot screen!!!!! (kind of hard on the ware:))

So, I can get to the boot screen iff I must. Thanx for that oldfred :D

I'm still looking for a way to 'enable' the softer method (shift or esc),
so any additional insights/suggestions would still be appreciated :)


later

:popcorn: TIME!

---

### Post by Yleeyas on 2012-03-13
Well shift key worked as advertised today so ... thanx for the leads again oldfred :)
...and SOLVED

---

### Post by oldfred on 2012-03-13
Glad you got it working.:)

---

### Post by sudodus on 2012-05-25
.

---

