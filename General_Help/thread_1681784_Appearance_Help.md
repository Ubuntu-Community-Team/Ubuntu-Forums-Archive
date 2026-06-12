---
title: "Appearance Help"
date: 2011-02-04
forum: General Help
---

### Post by GlitchKing on 2011-02-04
Everything was looking fine until I restarted my computer and it had a new look. In my opinion it looks like the old Windows 95 OS which is very bland and ugly.

See attached screenshot for an example.

My theme is default on Ubuntu 10.10. Ambiance.

Icons: Humanity - although none seem to change the icons when switching.

Everything else looks fine.

Please offer support as to how I can get my desktop to looking like the normal freshly installed desktop its supposed too.

Thanks.

____________________________________________________________________________________

Problem fixed: Solution > [http://ubuntuforums.org/showpost.php?p=10428836&postcount=6]("http://ubuntuforums.org/showpost.php?p=10428836&postcount=6")

---

### Post by GlitchKing on 2011-02-04
Update: Restarted again and this is what my new default desktop looks like. Even uglier.

HELP!! :(

---

### Post by lightningfox on 2011-02-04
Maybe this is happening because your disk does not have enough free space left to display your desktop properly.

Make sure that you have at least 1 GB free space each on your / and home partitions.

---

### Post by GlitchKing on 2011-02-04
I have 183.1 GB of free space.

---

### Post by Frogs Hair on 2011-02-04
Take a look at this thread.[http://ubuntuforums.org/showthread.php?t=1575703&highlight=gnom+reverts](http://ubuntuforums.org/showthread.php?t=1575703&highlight=gnom+reverts)

---

### Post by GlitchKing on 2011-02-04
Thanks for the support but I've found the problem.

System > Administration > Additional Drivers

It showed a graphics driver that was not activated.

ATI/AMD proprietary FGLRX graphics driver
Tested by the Ubuntu developers
License: Proprietary
3D-accelerated proprietary graphics driver for ATI cards.

This driver is required to fully utilise the 3D potential of some ATI graphics cards, as well as provide 2D acceleration of newer cards.

I clicked to activate it and it told me to restart. I restarted and everything worked correctly.

__________________________________________________________________

I wonder what happened for the driver to get turned off of whatever.

---

### Post by EpicTone on 2011-02-04
im not a pro here, but did you try going to appearance properties and select a different theme?

---

### Post by GlitchKing on 2011-02-04
Yes, I even chanced the icons (although they didnt change) the theme did.

See my first screenshot compared to second for an example.

Problem fixed though. :) thanks.

---

