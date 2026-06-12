---
title: "Not able to play .swf file"
date: 2011-07-19
forum: General Help
---

### Post by shamz_71 on 2011-07-19
It says

Gstreamer encountered a general supporting library error.

---

### Post by SavageWolf on 2011-07-19
You need to install the Flashplayer (Not the flashplugin).

1. Go to [http://www.adobe.com/support/flashplayer/downloads.html](http://www.adobe.com/support/flashplayer/downloads.html) and download the projector for Linux.
2. Run "gksudo nautilus", this'll open up a file browser as root.
3. Navigate to where you downloaded the file. (Your desktop is /home/(user)/Desktop)
4. Open the archive, by double clicking it.
5. Drag the file inside to /usr/bin.
6. To play the file you just have to run "flashplayer /path/to/file.swf".

Why is totem set to use *.swf files anyway?

---

### Post by jplunday on 2012-01-05
I had the same issue and this solved my problem.  Thanks.

---

