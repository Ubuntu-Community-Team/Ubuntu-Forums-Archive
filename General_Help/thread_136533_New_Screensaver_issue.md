---
title: "New Screensaver issue"
date: 2006-02-26
forum: General Help
---

### Post by qferret on 2006-02-26
I loved the Matrix screensaver from knoppix.ru that used to be in Hoary.

I have the 2 files from the tarball.

I placed matrix_gl in /usr/lib/xscreensaver
I placed KMatrix_gl.desktop in /usr/share/applnk/System/ScreenSavers/
I added the following line to .xscreensaver:

-		     "KMatrix" 	matrix_gl -root				    \n\

It shows in my list of screensavers and isn't greyed out, so I think I have it set up correctly that way. Unfortunately, even if I invoke it from a prompt, it give the following error:

```

ubuntu:/usr/lib/xscreensaver$ ./matrix_gl -root
freeglut (./matrix_gl): failed to change screen settings
Segmentation fault

```

Any ideas on how to look for what may be crashing it? (This may be why it was left out of Breezy)

---

