---
title: "Problem with image rotations"
date: 2010-04-29
forum: General Help
---

### Post by Muscovy on 2010-04-29
It seems the photos on our computer, rotated with fspot aren't actually rotated. Viewing them in Nautilus, Eye of Gnome, and Gimp, everything is fine, but in Firefox, they're not rotated.

Simply opening them and saving them seems to fix them. I tried looking at md5sums to see if the photos are changing, but as they're .jpgs, they change every time regardless.

I tried making a .png file and rotated it, but Firefox showed the rotation fine. I'm *guessing* something's going wrong in the .jpg metadata.

Help is highly appreciated.

Also, just in case this matters, we open Fspot just by mass select, right click, and don't use it for other things like sorting.

---

### Post by Muscovy on 2010-04-29
A bit more searching found this: [https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/69577](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/69577)

Essentially, Fspot saves .jpg rotations in some external manner, which clearly, most local applications can pick up on. In the meantime, I'm directing my family to use Gwenview until Ubuntu/Gnome/Someone/I make the default image viewer autosave rotations.

But I've got cleanup to do. Most of our photos are improperly flipped. Simply opening and then saving fixed he issue. Does anyone know of a script I can make that will simply resave everything in ~/Pictures?

---

