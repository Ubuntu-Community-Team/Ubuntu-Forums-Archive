---
title: "DVDs burn at lower speed than specified with Brasero"
date: 2011-01-12
forum: General Help
---

### Post by Asmodai on 2011-01-12
I'm using Brasero to burn DVDs and I'm burning at 4x speed (the DVDs and the DVD burner both support 16x max). The problem is that while burning, the speed is too low and it jumps around between 1.5x and 2.4x. This seems weird to me... shouldn't the burn process fail if it drops below 4x or if the speed is as unsteady as it is? But the DVDs seem to turn out fine anyway.
How come?

---

### Post by 3602 on 2011-01-12
Non-standard standards. Lots of CD-R writers are "52x max", and lots of CD-R discs are indeed 1x-52x. But if you burn music on it, it can go 16x-24x even if you specify Max Speed.
Are you burning music/video, data, or an image?

---

### Post by Asmodai on 2011-01-12
I'm burning video DVDs. When I clicked on "burn another copy", the speed jumped between 2x and 8x until it settled at a more or less steady 6x (I think Brasero automatically selects the max speed when selecting "burn another copy", so I suppose the target speed was 16x)
And now, the third DVD burns at 6x-11x, even though I selected 4x again.
There is something odd going on...

Edit: It might be worth mentioning that Brasero offers the following speeds: 4x, 8x, 12x and 16x and that all speeds except 4x appear twice in the menu.
This looks like a bug, unless I'm missing something.

Edit2: Disc 4 burns at a constant 8x for a change (of course, I selected 4x again).
I guess I'll have to give up on burning all DVDs at 4x speed.

---

### Post by mc4man on 2011-01-12
> shouldn't the burn process fail if it drops below 4x or if the speed is as unsteady as it is?
For the most part the  speed(s) aren't a factor in whether a burns 'succeeds' or not, a failure would be more from the process failing to complete for various reasons.

The speed however  is a factor in the quality of the burn, generally too fast or too slow will have negative effect to some degree.

Generally speaking the best quality burns come when the speed is 50% of the media's max., though that would be subject to the media itself, (mediacode), the drive, support for that mediacode in the drive's firmware, ect. ect.
(at some point 'burn quality' becomes a bit anal, all burns have errors, the value of a great burn vs. good burn is certainly debatable

Unfortunately brasero is somewhat inconsistent so you'd never be quite sure why it would burn a lower than the set speed.
With a solid burning app a lower speed is usually from the individual disk quality, though other factors could be firmware support for the media (burn strategy), drive health, drive and system buffer size.

---

