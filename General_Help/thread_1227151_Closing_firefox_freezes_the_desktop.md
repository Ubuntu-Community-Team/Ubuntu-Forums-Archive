---
title: "Closing firefox freezes the desktop"
date: 2009-07-30
forum: General Help
---

### Post by hbj on 2009-07-30
Hello,

I have a Ubuntu Jaunty AMD64 system running on a Compaq Presario Athlon-X2 laptop with Nvidia graphics.  When I log in as a particular user, start firefox, open multiple tabs, and then hit the X to close the firefox window, the entire desktop freezes.  Access via ssh is still possible.  This happens very repeatably, even after deleting the .mozilla folder.

When I log in as another user, I can open tabs and close firefox without any problems.  I'm out of ideas for what might be causing the problem or how to diagnose it better.  Any help would be appreciated.

Thanks

---

### Post by TeoBigusGeekus on 2009-07-30
Two ideas:
1) Open firefox from terminal and see if you get any error messages upon closing it.
2) Remove firefox and reinstall it.

---

### Post by hbj on 2009-07-30
Thanks for the suggestions.  Just to follow up, I launched firefox from the terminal and it froze the desktop again on closing.  As I was researching on another computer, suddenly the firefox window disappeared and I was returned to a working desktop.  Only one error in the window:

Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

Now opening and closing firefox works fine with no freezes.  I'm glad it's working now, but it's very unsettling.  I'm worried that there might still be a lurking problem.

---

### Post by TeoBigusGeekus on 2009-07-30
No more ideas from me - devoted Opera user :P
Someone else?

---

### Post by dac69 on 2009-07-31
I get something similar: the desktop freezes when I try to close tabs, but only after firefox has been running for some time.  I can't say whether number of tabs is an issue or not.

It would greatly ease my mind if I could confirm that this is not a hardware issue on my end (7 year old computer -can't afford a new one).  Will post more as investigation continues.

---

### Post by hbj on 2009-08-21
This issue appears to have been resolved by switching to the older version of the proprietary nvidia driver.

---

