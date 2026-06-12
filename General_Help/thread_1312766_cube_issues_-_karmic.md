---
title: "cube issues - karmic"
date: 2009-11-03
forum: General Help
---

### Post by Mzwo on 2009-11-03
hi,

since upgrading to 9.10, the cube won't behave as before.

firstly, i can't make it rotate using the mousewheel or the right edge of the touchpad. i tried this [http://ubuntuforums.org/showthread.php?t=1278343&highlight=cube+scroll]("http://ubuntuforums.org/showthread.php?t=1278343&highlight=cube+scroll"), but no cigar. scrolling works, rotating won't.

secondly, draging windows from one workspace to another doesn't work anymore. before i could grab it, move it to the edge of the screen to make it flip onto the neighbouring workspace.

i'm aware that this probably just a matter of some settings having gotten lost - yet i have absolutely no idea which setting to change. am very grateful for pointers in the right direction.


cheers,
Mzwo

---

### Post by 1fox2go on 2009-11-03
Have the same issue, spent about 20 minutes trying to get my visual effects settings to stay on extra but it just keeps going back to none.

I know the video card can handle it because it worked great in 9.04

---

### Post by P4man on 2009-11-03
To fix the scrolling try this:
[http://ubuntuforums.org/showthread.php?t=1278343](http://ubuntuforums.org/showthread.php?t=1278343)

To drag windows "over the edge", go to compizconfig settings manager, rotate cube, enable Edge flip move and DragNDrop.

---

### Post by Mzwo on 2009-11-03
hi,

thanks, "over-the-edge-dragging" works now, but scrolling still won't. 

already tried all that has been suggested in the link above, no luck. besides, i don't want to disable mouse rotate left and right - i want to be able to do both as before (scrolling only worked on workspace, not within windows. they way it should be). suggested changes to next_button and prev_button haven't changed anything at all.

Mzwo

---

### Post by P4man on 2009-11-03
Did you change it with gconf-editor or in ccsm ? It should be done in gconf-editor. But apparently this is a bug that has been solved, but still appears if you did an upgrade rather than a clean install. No idea how to fix it if you did an upgrade.

---

### Post by Mzwo on 2009-11-03
hi,

i used gconf-edit. 

anybody else know how to fix this after an upgrade?

Mzwo

---

### Post by P4man on 2009-11-03
Just to be sure, you do have the Viewport switcher plugin enabled in cssm ?

---

### Post by Mzwo on 2009-11-03
:idea:
aha! I had indeed, but just to make sure I checked - and, as it were, in "desktop-based viewport switching" the left and right mouse options were disabled. set to button 4 and button 5 respectively and it works. 

thanks for the pointer.

Mzwo

---

### Post by hellblazer on 2009-11-05
Hurray! worked for me too

---

