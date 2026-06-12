---
title: "Any Way to Bring Back Unmount Right Click Option?"
date: 2010-11-02
forum: General Help
---

### Post by mamamia88 on 2010-11-02
When I right click on my mp3 player it gives me the option of ejecting or safely removing.  If i do either it appears too the computer as though I unplugged it even though it's still connected to the computer.   Is there a way to bring back unmount so that it will still appear under places?  I would really love to have that behavior back

---

### Post by NertSkull on 2010-11-02
does it act the same when using the umount in the command line?

---

### Post by mamamia88 on 2010-11-02
never tried the unmount command from command line.  what is the command?

---

### Post by mc4man on 2010-11-02
If you wish to return then you'll need to re-build nautilus. quite easy to do.
What needs to be done depends on whether on lucid or maverick.

In lucid you just exclude the "16_hide_unmount.patch" from the build. (comment out the entry in /debian/patches/series

In maverick you'll need to revert the changes, I have done so here and made a patch to do so.

See here for maverick, and some general, (lucid inc.), build tips - if maverick updates and the patch changes may update the attachment (I think I can even though the forum is closed, I certainly can edit the post if need be. - wasn't much interest shown

[http://ubuntuforums.org/showthread.php?t=1591892](http://ubuntuforums.org/showthread.php?t=1591892)

Also includes a patch to 'fix' the 'open with - other application' misbehaviour

I switched to nautilus-elementary (maverick), a patch is available upon request
(n.e. updates in the ppa more frequently, the line #'s may change - lucid patch is also possible

---

### Post by inameiname on 2010-11-08
Here is a script I made that works like the old unmount option before they removed it. When right clicking the mounting device, just select it. That is, if you've added it to your nautilus-scripts folder in ~/.gnome2/nautilus-scripts/.

```

#!/bin/bash
# unmount
# ubulal

gksudo umount "`echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"`"

```

---

