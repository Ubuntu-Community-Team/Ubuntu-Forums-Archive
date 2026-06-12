---
title: "What is the Amarok OSD Using for Transparency?"
date: 2006-03-06
forum: General Help
---

### Post by mrgnash on 2006-03-06
I noticed that with Amarok's (1.4 SVN) OSD (On Screen Display) you can now configure it to use translucency. I'm curious as to whether anyone knows what engine it is using to do this, because unlike 'phony' transparency, I can see windows, desklets, etc. underneath. I doubt it could be composit, because not only do I have an ATI card, but I haven't even gone to any special trouble to enable hardware acceleration for it. :confused:

---

### Post by ltmon on 2006-03-06
You can also get the K-menu and normal menu bar menus to do the same somehow.

I believe it's simply taking a screenshot into memory, and then setting a blended version of the screenshot as a background.

This is not useful for anything that moves, or is displayed a lot, because taking the screenshot is an expensive operation.  So many other apps (i.e. kicker, konsole) just take a screenshot of the background, which only has to be done once.

L.

---

