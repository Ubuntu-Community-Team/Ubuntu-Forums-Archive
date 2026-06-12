---
title: "How to add unmount option back to context menu in Lucid"
date: 2010-08-29
forum: General Help
---

### Post by inameiname on 2010-08-29
I am one of those apparently few who loved the 'unmount' option in the right context menu, alongside 'eject' and 'safely remove', and ever since it was removed in Lucid, as explained here: 

[https://launchpad.net/ubuntu/lucid/+source/nautilus/1:2.30.0-0ubuntu3](https://launchpad.net/ubuntu/lucid/+source/nautilus/1:2.30.0-0ubuntu3)

...I've been really upset, as now, whenever I wish to unmount things, I am forced to open the gnome-disk-utility. It's doable, but much more of a hassle than a quick right click and select. 

Basically, what 'unmount' works great for is unmounting rewritable media so as to either erase and then right discs, or shred flash drives and sd cards so I can then format with Gparted.

Anyway, my question is how to add it back. Or perhaps a simpler way of just adding a nautilus-script (which I'd also put in my nautilus-actions options). 

Therefore, does anybody have a script or could help write one so as to do just what I would like?

Any help would be grande, thanks.

---

### Post by mc4man on 2010-08-29
You may be able to do as a script ( though umount needs sudo
I'd just  simply rebuild the current nautilus source and not have the patch applied.

You could approach in several different ways, best is  probably to just redo as the same package set as is currently used (ie. build and install as debian packages.

The source builds 5 packages, if you keep the same version # then only the nautilus package would probably need to be replaced.

When you keep the same ver. # then the package is seen as a re-install but after install  then the repo package would been seen as an update.
So you'd need to be careful to not let it update.
The advantage there is if for some reason you want to go back to the repo package it's quite simple - just update.

Otherwise you could up the version slightly - in that case you'd need to install a min. of 3 packages at once with dpkg. 
Then there would be no update issue unless lucid updates nautilus, in that case you'd be informed which is a good thing. (if you up the ver. # properly.

screens shows the build folder and returned option - the patch is number 16, simply comment it out in the sources /debian/patches/series file


(if you wish to build and are unsure, just ask - otherwise maybe a script or N.A. will arise...

---

### Post by inameiname on 2010-08-29
Interesting idea. I'll look into it.

One worry though, is that I can see you are using the official Nautilus, 2.30.1, whereas I use Nautilus-elementary, which is a tweaked version of 2.31.1. I'm guessing that sort of screws it all up. Unless, I guess, I can get the source file and build it that way?

And if I'd have to get up Nautilus-elementary for the official one, of course I'd have to say forgeaboutit when it comes to the 'unmount' thing since Nautilus-elementary is just the cat's meow for me. hehe I can suffer.

---

### Post by inameiname on 2010-09-08
I found a script that works for this task.

#!/bin/bash 
# unmount 
# ubulal 

gksudo umount "`echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"`"


Also, shame I can't direct a nautilus-action to the path of this script,  so it'll also be in the main directory of my context menu, so I can be  even lazier and not have to go to my scripts folder for it. :razz: But since the icons for the drives aren't technically a file or a folder, it's not possible. Hehe

---

