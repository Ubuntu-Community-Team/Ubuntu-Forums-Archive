---
title: "Resizing partitions"
date: 2011-05-26
forum: General Help
---

### Post by TivA on 2011-05-26
I have Ubuntu 11.04.
I currently use all my disc space for ubuntu (around 80 Gigs). I want to make a new smaller partition. Could I do that from Ubuntu 11.04 with maybe the terminal or what??
Thanks

---

### Post by Joe of loath on 2011-05-26
You will have to boot into a live CD/USB, as the resize action can only be done with the partition unmounted. However, it should work fine.

---

### Post by sanderd17 on 2011-05-26
you need to use a program called gparted (it's on the live CD).

When you edit the partions, Gparted will show you wat it will do, if you see suspicious things (like format partition /dev/sdx), just close Gparted and start over. Nothing happens until you click apply.

Once you click apply, do not pause the computer and make sure that he doesn't run out of power. The applying can take quite long (if you need to shrink a nearly full disk, it can take longer than an Ubuntu installation).

---

