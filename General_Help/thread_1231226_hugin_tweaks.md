---
title: "hugin tweaks"
date: 2009-08-04
forum: General Help
---

### Post by Bartender on 2009-08-04
I just wanted to mention a couple of odd quirks with hugin.  This is on Ubuntu 8.10, but I believe the same things are happening with 9.04.
There are several threads regarding "error code: 1".  The fix appears to be going into hugin's File>Preferences, then opening the Autopano tab.  Make sure the two lines in Autopano-SIFT box say ```
autopano-complete
``` then in the second line ```
--output %o --points %p %i
```  After you make these changes close hugin and turn it back on just to make sure.
That didn't fix it for me.  One of the threads I found mentioned that hugin didn't like file names with underscores.  The pictures I was trying to merge had several underscores in their names.  So I renamed them "snow1.jpg" and "snow2.jpg".
hugin worked!
I've used hugin for a while, across several different versions of Ubuntu.  Maybe I'm wrong but pretty sure I merged the exact same photos before and hugin didn't display the fussiness about file names.

---

